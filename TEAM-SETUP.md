# Team Setup: Edit the KMC Calendars with Claude Code

Paste the prompt below into the Claude desktop app (Code tab) or Claude Code in a terminal, started in any folder such as Documents. It sets up your computer to edit the calendars. If you only have a regular Claude chat, paste it there and it will walk you through the steps one at a time.

You need the Claude desktop app or Claude Code installed first, since a prompt can't install the app it runs in. You also need Logan to add you as a collaborator on the repo (Settings > Collaborators) before you can push changes.

## The prompt

```text
I'm a new teammate on the KMC calendars project. Please set up my computer so I can edit the calendars with Claude Code. Go one step at a time, keep explanations short, and run commands yourself when you can. If you can't run commands on my computer, give me one step at a time and wait for me to confirm before moving on.

1. Check whether I'm on Windows or Mac.
2. Check whether Git, the GitHub CLI (gh) and Claude Code are installed, and install whatever is missing:
   - Windows: winget install --id Git.Git -e   and   winget install --id GitHub.cli -e
   - Mac: brew install git gh (install Homebrew first if I don't have it)
   - Claude Code: if it's missing, walk me through the current official install instructions.
   After installing, new programs may not be found until I open a new terminal or restart this app. If a command isn't found, try the full path (on Windows, gh is at C:\Program Files\GitHub CLI\gh.exe) or tell me to restart and come back.
3. Check that Git knows who I am (git config --global user.name and user.email). If not, ask me for my name and email and set them.
4. Sign me in to GitHub. This step is interactive, so tell me to run `gh auth login` in my own terminal and choose: GitHub.com, then HTTPS, then Yes to authenticating Git, then "Login with a web browser". Confirm with `gh auth status`. If I don't have a GitHub account, tell me to create one at github.com first. Never ask me to paste a password or token to you.
5. Clone the project into a "GitHub" folder inside my Documents folder (create it if needed): git clone https://github.com/Logan-KMC/KMC-Calendars.git
6. Check that I can make changes: gh api repos/Logan-KMC/KMC-Calendars --jq .permissions.push. If it says false, tell me to send Logan my GitHub username so he can add me as a collaborator. I can finish the other steps now, and my edits will work once he adds me.
7. Run git pull inside the folder to confirm it works, then read CLAUDE.md and summarize its rules in 3 short bullets.
8. Tell me exactly how to open Claude Code in the KMC-Calendars folder (switch folders yourself if you can). Remind me that from then on I can just ask for calendar changes in plain English.

Don't edit, commit, or push anything during this setup.
```

## After setup

Open Claude Code in the `KMC-Calendars` folder and ask for changes in plain English. The rules in `CLAUDE.md` load automatically, including pulling the latest version before every edit and pushing only when you ask.
