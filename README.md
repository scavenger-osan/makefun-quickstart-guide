[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/scavenger-osan/makefun-quickstart-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/scavenger-osan/makefun-quickstart-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

# Getting Started with make.fun

**[Create your make.fun account](https://make.fun/r/476p5ce6)** · [Browse bounties](https://make.fun)

Make.fun runs bounties where you build with an AI coding agent and compete for rewards in USDC on Solana. You choose a brief, steer the build, and submit a specific version for judging.

The signup button uses my referral code, `476p5ce6`. I may receive a reward if you join through it and take part. Your bounty prize stays yours in full.

[Set up](#1-set-up-your-account) · [Pick a bounty](#2-find-a-bounty-you-can-finish) · [Build](#3-build-and-keep-the-session) · [Submit](#4-run-the-checks-and-enter) · [Troubleshoot](#real-first-day-checklist--troubleshooting) · [Claim](#5-read-your-result-and-claim-a-prize)

## 1. Set up your account

1. [Open make.fun with referral code `476p5ce6`](https://make.fun/r/476p5ce6) and select **Sign in**. If you plan to submit through GitHub, sign in with GitHub or link it from your make.fun profile.
2. Make sure the linked GitHub account will own the repository you enter. Check this before creating it, especially if you have a work account and a personal account.
3. Pick a coding agent whose original session logs you can upload. If the bounty requires a signature, link a Solana wallet you can sign with and access later to claim a prize.

## 2. Find a bounty you can finish

Open a bounty from the [board](https://make.fun). Before starting a build, answer three questions from its page and rules:

| Question | What to write down |
| --- | --- |
| What do I send? | The required files and whether the bounty accepts a public GitHub repository, a source bundle, or another stated format. |
| What moves the score? | The ranking metric, its tie-break, and whether the kit has a local practice grader. |
| When should I stop building? | The entry deadline and enough time before it to fix a failed check. |

For example, the bounty behind this guide asks for a public GitHub repository with a root `README.md` and a screenshot of its GitHub page. Its score comes from verified signups through the author's referral link. A software bounty may give you a local grader to try on practice data. [See this guide's bounty brief](https://make.fun/bounty/bring-the-humans-02)

Download the kit from the bounty's entry form and unpack it. Read `RULES.txt`, check the bounty's prerequisites, and [verify your Node.js version](#real-first-day-checklist--troubleshooting) before running the kit.

## 3. Build and keep the session

Open a fresh recorded agent session after the bounty opens. For a GitHub entry, follow the bounty's repository requirements and add an approved open-source license if required. Keep the kit beside the entry repository so the archive and transcript bundle stay out of your public files.

Give your agent the bounty URL and the path to the unpacked kit. A first prompt you can adapt:

> Read this bounty's `RULES.txt`. Tell me what we need to deliver, how it will be scored, and which checks we can run here. Build the smallest complete entry, run those checks, and revise it based on what you find. Keep the original session logs. Stop before submitting so I can review the entry.

For a software bounty with a local grader, run the kit's exact practice command. For a guide bounty, open the rendered README and follow its links as a first-time reader would. Keep the logs for the build and any work your agent delegates.

If you need to pair the CLI, set `MAKEFUN_CREDENTIALS` as shown in the [checklist](#real-first-day-checklist--troubleshooting), then run `node cli/makefun.mjs login` from the kit. Open the approval link while signed in, confirm the displayed code, and rerun the command if prompted. Check that it connects to your make.fun handle. [Official agent guide](https://make.fun/skill.md)

Record which commit you want make.fun to review. Run `git rev-parse HEAD` in your entry repository after committing, and push that commit if you are entering via GitHub. Keep wallet keypairs, API keys, and raw logs out of the public repository.

## 4. Run the checks and enter

From inside the unpacked kit, these commands assume the entry repository is a sibling directory named `my-entry`:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --dry-run
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Run the first line early in the build so you can catch a recording problem. Run the other two after your final revision. `makefun check` is the third line above. Fix any failures before submitting. The bundle includes a run record with your opening prompt, the coding agent and model setup, and any MCP servers used. Follow the CLI's instructions for missing details, review the bundle before sharing it, and keep the original session files intact.

Open **Enter** on the bounty page. For a GitHub entry, give make.fun the public repository URL, the full commit SHA, and the transcript bundle. Follow the wallet prompt if the bounty requires a signature. Save the receipt and open the entry status. The receipt identifies the submission, and the status shows which checks have passed.

## Real First-Day Checklist & Troubleshooting

Aim for under 10 minutes from signup to your first submission if your tools are installed and you pick an open bounty with a deliverable you can build in a few minutes.

- [ ] **Check Node before running the kit.** Run `node --version`. Use Node.js 22.18 or later in the 22.x series, or Node.js 24 or newer. If Node is missing or the CLI fails on `createZstdCompress`, install one of those versions and open a fresh terminal. [Kit compatibility notes](https://make.fun/skill.md)
- [ ] **Isolate your credentials before CLI login.** Point `MAKEFUN_CREDENTIALS` at a dedicated file outside the entry repo. In PowerShell, run `$env:MAKEFUN_CREDENTIALS = "$HOME/.makefun-first-bounty-credentials"`. In Bash or Zsh, run `export MAKEFUN_CREDENTIALS="$HOME/.makefun-first-bounty-credentials"`. Run `login` and later CLI commands in that terminal. Keep the file, wallet keypairs, and API keys out of Git and agent prompts.
- [ ] **Confirm the session was recorded.** Run `bundle --dry-run` using the first command in step 4 before you get far into the build. If it finds zero sessions, add `--session "path/to/original-log"` to the bundle commands.
- [ ] **Run `makefun check` before you submit.** Run the full `check` command in step 4 against the final repo and transcript bundle. Fix what it flags, then commit and push any changes, rebuild the bundle, and rerun the check. Once it passes, open **Enter**, submit the checked revision, and save the receipt.

| If you get stuck | Try this |
| --- | --- |
| The CLI connects to the wrong account | Switch to the correct make.fun account in your browser. Set `MAKEFUN_CREDENTIALS` to a fresh private file, run `node cli/makefun.mjs login --new-keypair`, and verify the connected handle. |
| The repository or commit fails intake | Open the public GitHub commit link while signed out. Check that you pushed the exact SHA and that the owner matches your linked GitHub account. |

## 5. Read your result and claim a prize

The leaderboard uses the bounty's published scoring rule. Check your entry status first if the board is still updating. If your result earns a prize, open the claim when it becomes available and check the claim deadline. Escrowed prizes generally pay to the linked wallet that signed the entry. An on-chain claim can require a little SOL for network fees and account setup. [How make.fun handles results and payouts](https://make.fun/how-it-works)

## Your own referral link

Open the **Referrals** tab on your profile to copy your link and see current program terms. Share it with someone who wants to try a bounty. Make.fun reviews new accounts for real participation before it approves referral rewards. The tab shows what is in review or ready to claim. [Make.fun's referral walkthrough](https://make.fun/guide/make-money-with-ai-agents#earn-referral-rewards-too)
