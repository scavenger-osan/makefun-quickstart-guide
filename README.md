[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/scavenger-osan/makefun-quickstart-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/scavenger-osan/makefun-quickstart-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

# Getting Started with make.fun

Make.fun runs bounties where you build with an AI coding agent and compete for rewards in USDC on Solana. You choose a brief, steer the build, and submit a specific version for judging. Start by opening one bounty you could finish and finding its deliverable, scoring rule, and deadline.

**[Create your make.fun account](https://make.fun/r/476p5ce6)** · [Browse bounties](https://make.fun)

The signup button uses my referral code, `476p5ce6`. I may receive a reward if you join through it and take part. Your bounty prize stays yours in full.

[Set up](#1-set-up-your-account) · [Pick a bounty](#2-find-a-bounty-you-can-finish) · [Build](#3-build-and-keep-the-session) · [Submit](#4-run-the-checks-and-enter) · [Claim](#5-read-your-result-and-claim-a-prize)

## 1. Set up your account

1. Open the signup link and select **Sign in**. If you plan to submit through GitHub, signing in with GitHub is the simplest route. You can also use another offered sign-in method and link GitHub from your profile.
2. Make sure the linked GitHub account will own the repository you enter. Check this before creating it, especially if you have a work account and a personal account.
3. Pick a coding agent whose original session logs you can upload. If the bounty requires a signature, link a Solana wallet you can sign with and access later to claim a prize.

## 2. Find a bounty you can finish

Open a bounty from the [board](https://make.fun). Before starting a build, answer three questions from its page and rules:

| Question | What to write down |
| --- | --- |
| What do I send? | The required files and whether the bounty accepts a public GitHub repository, a source bundle, or another stated format. |
| What moves the score? | The ranking metric, its tie-break, and whether the kit has a local practice grader. |
| When should I stop building? | The entry deadline and enough time before it to fix a failed check. |

For example, the bounty behind this guide asks for a public GitHub repository with a root `README.md` and a screenshot of its GitHub page. Its score comes from verified signups through the author's referral link. The kit has pre-submission checks for the guide and screenshot. A software bounty may instead score a program on practice data and give you a local grader. [See this guide's bounty brief](https://make.fun/bounty/bring-the-humans-02)

Download the kit from the bounty's entry form and unpack it. Read `RULES.txt` and check any prerequisites on the bounty page before starting. The kit CLI runs on Node.js 22 or later. Use `node --version` to check your installation.

## 3. Build and keep the session

Open a fresh recorded agent session after the bounty opens. For a GitHub entry, follow the bounty's repository requirements and add an approved open-source license if required. Keep the kit beside the entry repository so the archive and transcript bundle stay out of your public files.

Give your agent the bounty URL and the path to the unpacked kit. A first prompt you can adapt:

> Read this bounty's `RULES.txt`. Tell me what we need to deliver, how it will be scored, and which checks we can run here. Build the smallest complete entry, run those checks, and revise it based on what you find. Keep the original session logs. Stop before submitting so I can review the entry.

For a software bounty with a local grader, run the kit's exact practice command. For a guide bounty, open the rendered README and follow its links as a first-time reader would. Keep the logs for the build and any work your agent delegates. To pair the kit CLI with your account, run `node cli/makefun.mjs login` from the kit, then open its approval link while signed in and confirm the displayed code. [Official agent guide](https://make.fun/skill.md)

Record which commit you want make.fun to review. Run `git rev-parse HEAD` in your entry repository after committing, and push that commit if you are entering via GitHub. Keep wallet keypairs, API keys, and raw logs out of the public repository.

## 4. Run the checks and enter

From inside the unpacked kit, these commands assume the entry repository is a sibling directory named `my-entry`:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --dry-run
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Run the first line early in the build so you can catch a recording problem. Run the other two after your final revision. The bundle includes a run record with your opening prompt, the coding agent and model setup, and any MCP servers used. Follow the CLI's instructions for missing details. Review the bundle before sharing it and keep the original session files intact.

Open **Enter** on the bounty page. For a GitHub entry, give make.fun the public repository URL, the full commit SHA, and the transcript bundle. Follow the wallet prompt if the bounty requires a signature. Save the receipt and open the entry status. The receipt identifies the submission, and the status shows which checks have passed.

| If you see… | Try this |
| --- | --- |
| The bundle finds zero sessions | Locate the log your agent recorded and pass its path with `bundle --session`. |
| The repository or commit fails intake | Open the public GitHub commit link while signed out. Check that you pushed the exact SHA and that the owner matches your linked GitHub account. |
| A required file fails a check | Use the check's fix, commit and push the revision, rebuild the bundle, and submit the new SHA within the entry window and limits. |

## 5. Read your result and claim a prize

The leaderboard uses the bounty's published scoring rule. Check your entry status first if the board is still updating. If your result earns a prize, open the claim when it becomes available and check the claim deadline. Escrowed prizes generally pay to the linked wallet that signed the entry. An on-chain claim can require a little SOL for network fees and account setup. [How make.fun handles results and payouts](https://make.fun/how-it-works)

## Your own referral link

Open the **Referrals** tab on your profile to copy your link and see current program terms. Share it with someone who wants to try a bounty. Make.fun reviews new accounts for real participation before it approves referral rewards. The tab shows what is in review or ready to claim. [Make.fun's referral walkthrough](https://make.fun/guide/make-money-with-ai-agents#earn-referral-rewards-too)
