# Generating and Registering an SSH Key with GitBash on Windows

This guide will walk you through the steps to generate an SSH key using GitBash and register it with your GitHub account. This guide is intended for PC users.

---

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Step 1: Open GitBash](#step-1-open-gitbash)
3. [Step 2: Generate an SSH Key](#step-2-generate-an-ssh-key)
4. [Step 3: Start the SSH Agent](#step-3-start-the-ssh-agent)
5. [Step 4: Copy Your SSH Key to Clipboard](#step-4-copy-your-ssh-key-to-clipboard)
6. [Step 5: Add SSH Key to GitHub](#step-5-add-ssh-key-to-github)
7. [Step 6: Test the SSH Connection](#step-6-test-the-ssh-connection)
8. [Step 7: Create a New Repository on GitHub](#step-7-create-a-new-repository-on-github)
9. [Step 8: Clone the Repository to Your Computer](#step-8-clone-the-repository-to-your-computer)
10. [Step 9: Use the Same SSH Key for GitLab](#step-9-use-the-same-ssh-key-for-gitlab)
11. [Troubleshooting](#troubleshooting)
12. [Useful Links](#useful-links)

---

## Prerequisites

1. **GitBash Installed**  
   Download and install GitBash from the official site: [Git for Windows](https://git-scm.com/download/win). Follow the installer prompts to complete the installation.

2. **A GitHub Account**  
   If you do not already have a GitHub account, create one at [GitHub Signup](https://github.com/signup).

---

## Step 1: Open GitBash

After installing GitBash, launch the application. You can find it by searching for "GitBash" in your Windows Start Menu.

---

## Step 2: Generate an SSH Key

1. In GitBash, type the following command to generate a new SSH key:

   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   Replace `your_email@example.com` with the email address associated with your GitHub account.

2. When prompted to "Enter a file in which to save the key," press `Enter` to accept the default file location.

3. When asked for a passphrase, press `Enter` to skip creating a passphrase. **Do not set a passphrase** to avoid potential issues with forgetting it.

   Once completed, your SSH key will be generated and saved to your computer.

---

## Step 3: Start the SSH Agent

To use your SSH key, you need to ensure the SSH agent is running. In GitBash, enter the following commands:

1. Start the SSH agent:

   ```bash
   eval $(ssh-agent -s)
   ```

2. Add your SSH key to the agent:

   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

---

## Step 4: Copy Your SSH Key to Clipboard

To register the key with GitHub, you need to copy it to your clipboard. Use the following command:

```bash
clip < ~/.ssh/id_ed25519.pub
```

This copies the public key to your clipboard.

---

## Step 5: Add SSH Key to GitHub

1. Open [GitHub](https://github.com) and log into your account.

2. Navigate to **Settings** (found in the top-right dropdown menu).

3. In the settings menu, go to **SSH and GPG Keys**.

4. Click the **New SSH Key** button.

5. Give the key a descriptive title (e.g., `My PC SSH Key`).

6. Paste your public key into the "Key" field. Use `Ctrl+V` to paste if necessary.

7. Click **Add SSH Key**.

8. Confirm your GitHub password if prompted.

---

## Step 6: Test the SSH Connection

Verify that your key was added successfully by typing the following command in GitBash:

**Note:** On your first attempt, you may be asked to verify the authenticity of the host by typing 'yes'. This is normal and only occurs the first time.

```bash
ssh -T git@github.com
```

You should see a message like this:

```text
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

---

## Step 7: Create a New Repository on GitHub

1. Log into your GitHub account and navigate to your profile.
2. Click the **Repositories** tab and then click **New**.
3. Provide a name for your repository (e.g., `my-first-repo`).
4. Ensure the repository is set to **Public**. This is required so that graders can access your homework.
5. Check the box to **Initialize this repository with a README**.
6. Select a `.gitignore` template: Choose **Python** from the dropdown menu.
7. Click **Create Repository**.

---

## Step 8: Clone the Repository to Your Computer

1. On the repository page, click the green **Code** button.
2. Select the **SSH** option and copy the SSH URL.
3. Navigate to the directory where you want to clone the repository. You can use the following shortcut:
   - Open the folder where you'd like to clone the repository.
   - Right-click in the folder, select **More Options** (if applicable), and then click **Open GitBash Here**. This will open GitBash in the desired directory.
4. Clone the repository using the SSH URL:

   ```bash
   git clone git@github.com:username/repository-name.git
   ```

   Replace `username` and `repository-name` with your GitHub username and the repository name.

5. Navigate into the cloned repository:

   ```bash
   cd repository-name
   ```

You can now start working on your project locally.

---

## Step 9: Use the Same SSH Key for GitLab

Your SSH key can also be used to authenticate with your class GitLab page. Follow these steps:

1. Open your class GitLab page and log in.
2. Navigate to **Preferences** (usually accessible from your profile dropdown).
3. In the preferences menu, go to **SSH Keys**.
4. Paste the same public key you copied earlier into the "Key" field.
   - If the key is no longer in your clipboard, re-copy it using the following command in GitBash:
     
     ```bash
     clip < ~/.ssh/id_ed25519.pub
     ```
5. Remove any value from the "Expiration Date" field to ensure the key does not expire.
6. Give the key a descriptive title (e.g., `My PC SSH Key`).
7. Click **Add Key** to save it.

Once added, you can use the same SSH key to interact with your repositories on GitLab.

### Clone the GitLab Repository to Your Computer

To access the class materials:

1. Navigate to the GitLab repository page and copy the **SSH URL** from the **Clone** dropdown menu.
2. Open GitBash and navigate to the directory where you want to clone the repository. For example:

   ```bash
   cd /path/to/your/directory
   ```

3. Clone the repository:

   ```bash
   git clone paste_the_full_SSH_URL_here
   ```

   Be sure to paste the entire link you copied from the GitLab repository page.

4. Navigate into the cloned repository:

   ```bash
   cd classroom-repository-name
   ```

### Keep Your Repository Updated

You will need to pull the latest updates before every class session and after class to retrieve solutions to classroom activities:

1. To pull updates:

   ```bash
   git pull
   ```

   This will synchronize your local copy with the latest changes on GitLab.

2. Run `git pull` about 30 minutes after class concludes to access the solutions provided by the instructor.

Remember, you will not be pushing changes to this repository.
---

## Troubleshooting

### 1. SSH Key Not Found
   - Ensure the file path for your key is correct. Use the `ls ~/.ssh` command to list your SSH keys.

### 2. Permission Denied
   - Make sure the SSH agent is running and the correct key has been added using `ssh-add`.

---

## Useful Links

- **Git for Windows Download**: [https://git-scm.com/download/win](https://git-scm.com/download/win)
- **GitHub SSH Key Documentation**: [https://docs.github.com/en/authentication/connecting-to-github-with-ssh](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
- **GitLab SSH Key Documentation**: [https://docs.gitlab.com/ee/user/ssh.html](https://docs.gitlab.com/ee/user/ssh.html)

---

This concludes the setup process for generating and registering an SSH key with GitBash on Windows, creating a new repository on GitHub, and cloning it to your computer. If you encounter any issues, refer to the troubleshooting section or ask for assistance.

