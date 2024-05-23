## Uploading Local Repository to GitHub using Access Token

## Table of Contents
---
<!-- vscode-markdown-toc -->
- [1. Prerequisites](#1-prerequisites)
- [2. Generating a Personal Access Token (PAT)](#2-generating-a-personal-access-token-pat)
- [3. Uploading Your Repository](#3-uploading-your-repository)
- [4. Initialize Git](#4-initialize-git)
- [5. Stage and Commit](#5-stage-and-commit)
- [6. Connect Local Repository to Remote](#6-connect-local-repository-to-remote)
- [7. Push to GitHub](#7-push-to-github)
- [8. Important Security Notes](#8-important-security-notes)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc --> 
 ---

Here's a breakdown of how to upload your local repository to GitHub using an access token, along with security considerations:

##  1. <a name='Prerequisites'></a>Prerequisites

Git Installed: Ensure Git is installed on your system.
GitHub Account: You'll need an active GitHub account.
Access Token: Generate a Personal Access Token (PAT) with the necessary permissions (at least repo scope). Never share your access token publicly!

##  2. <a name='GeneratingaPersonalAccessTokenPAT'></a>Generating a Personal Access Token (PAT)

Navigate to Settings: Log in to GitHub and go to your profile picture (top right) > Settings.
Developer Settings: Go to Developer settings (bottom left).
Personal Access Tokens: Click on Personal access tokens > Generate new token.
Token Configuration:
(It's better to use Fine Grained Tokens insetead of of Classic Tokens)
Provide a descriptive Note (e.g., "Repository Upload").
Select the repo scope (or a more restrictive scope if possible).
Generate and Copy: Click Generate token. Copy the token immediately as it will only be displayed once.

##  3. <a name='UploadingYourRepository'></a>Uploading Your Repository

Open Your Terminal/Command Prompt: Navigate to your local repository's root directory.

##  4. <a name='InitializeGit'></a>Initialize Git

 {#Initialize Git:}If your repository isn't already a Git repository:

```
git init
```

##  5. <a name='StageandCommit'></a>Stage and Commit

**Add your files and commit the changes:**

```
git add .
```
```
git commit -m "Initial commit
```

Create a Remote Repository (Optional) You can either:

**Create an Empty Repository on GitHub:** Do this through the GitHub website (no code needed).
Create it via the command line:

```
curl -u 'your_username:your_access_token' https://api.github.com/user/repos -d '{"name":"your-repo-name", "private": true}'
```

**Replace** 

-   **your_username** with your GitHub -    **username**, 
-   **your_access_token** with your -   **PAT** **(Personal Access Token)**
-   **your-repo-name** with your desired **repository name**

##  6. <a name='ConnectLocalRepositorytoRemote'></a>Connect Local Repository to Remote 

-   Replace **your-username** and **your-repo-name**

-   Replace **private** with **public** in case you want to create a **public** repository.

```
git remote add origin https://<your-username>:<your_access_token>@github.com/<your-username>/<your-repo-name>.git
```

##  7. <a name='PushtoGitHub'></a>Push to GitHub

```
git push -u origin main
```
---
*(**Note:** If you're not using the main branch, replace it with your branch name. Main and master branch are conceptually the same thing. The convention just changed: previously the primary branch was called master and for newer repository that defaults to main . You should only ever have one of those in a single repository. Also note that, the most common name used for main branch is master branch if you are using git on linux terminal like such as ubuntu terminal.)*

---
##  8. <a name='ImportantSecurityNotes'></a>Important Security Notes 

-   **Token Scope:** Limit the scope of your PAT to the minimum permissions required. The repo scope grants broad access.
-   **Token Security:** Treat your access token like a password. Never commit it to version control or share it publicly.
-   **SSH as an Alternative:** For enhanced security, consider using SSH keys for authentication instead of access tokens.
