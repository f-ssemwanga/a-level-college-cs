
# Git & GitHub SSH Setup Guide (School Devices)

This guide shows you how to set up Git and GitHub with SSH keys on managed school computers. SSH keys provide secure authentication without needing to enter passwords repeatedly.

**Prerequisites:** Git Bash installed via Company Portal

---

## Step 1: Configure Git Identity

First, tell Git who you are. Open Git Bash and run these commands with **your own details**:

```bash
git config --global user.name "Your Full Name"
git config --global user.email "your.email@college.ac.uk"
```

Verify your configuration:
```bash
git config --global --list
```

---

## Step 2: Generate SSH Key

Create a new SSH key pair. Replace with **your actual GitHub email**:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

**When prompted:**
- **File location:** Press Enter (uses default location)
- **Passphrase:** Press Enter twice (no passphrase for school use)

**Expected output:**
```
Your identification has been saved in /c/Users/YourUsername/.ssh/id_ed25519
Your public key has been saved in /c/Users/YourUsername/.ssh/id_ed25519.pub
```

---

## Step 3: Start SSH Agent

Run this command to start the SSH agent:

```bash
eval "$(ssh-agent -s)"
```

**Expected output:**
```
Agent pid 1234
```

---

## Step 4: Add Key to SSH Agent

Add your private key to the SSH agent:

```bash
ssh-add ~/.ssh/id_ed25519
```

**Expected output:**
```
Identity added: /c/Users/YourUsername/.ssh/id_ed25519 (your_email@example.com)
```

---

## Step 5: Copy Your Public Key

Display and copy your public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

This prints a long line starting with `ssh-ed25519 AAAA...`

**Copy the entire output** (including `ssh-ed25519` at the start).

---

## Step 6: Add Key to GitHub

1. **Go to GitHub:** Log into your GitHub account
2. **Navigate to Settings:** Click your profile picture → Settings
3. **SSH Keys:** Click "SSH and GPG keys" in the left sidebar
4. **Add New Key:** Click "New SSH key"
5. **Fill in details:**
   - **Title:** `School Laptop Key` (or similar)
   - **Key type:** Authentication Key
   - **Key:** Paste your copied public key
6. **Save:** Click "Add SSH key"

---

## Step 7: Test SSH Connection

Verify your SSH setup works:

```bash
ssh -T git@github.com
```

**Expected output:**
```
Hi your-username! You've successfully authenticated, but GitHub does not provide shell access.
```

If you see a message about host authenticity, type `yes` and press Enter.

---

## Step 8: Clone Repository Using SSH

When cloning repositories, use the SSH URL instead of HTTPS:

```bash
git clone git@github.com:username/repository-name.git
```

For example, to clone the class repository:
```bash
git clone git@github.com:f-ssemwanga/a-level-college-cs.git
```

---

## Step 9: Test Push Access

Navigate to your cloned repository and test pushing:

```bash
cd a-level-college-cs
echo "# Test file" > test.txt
git add test.txt
git commit -m "Test commit from school device"
git push origin main
```

If successful, you should see output confirming the push completed.

---

## Troubleshooting

### Problem: "Permission denied (publickey)"
**Solution:** Check that:
- SSH key was added to GitHub correctly
- SSH agent is running: `eval "$(ssh-agent -s)"`
- Key is loaded: `ssh-add ~/.ssh/id_ed25519`

### Problem: "Could not open a connection to your authentication agent"
**Solution:** Restart SSH agent:
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

### Problem: Git asks for username/password
**Solution:** You're using HTTPS URL instead of SSH. Check your remote:
```bash
git remote -v
```
If it shows `https://`, change to SSH:
```bash
git remote set-url origin git@github.com:username/repo.git
```

---

## Daily Workflow

**Each time you open Git Bash**, you may need to restart the SSH agent:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

**Then you can work normally:**
```bash
git add .
git commit -m "Your commit message"
git push
```

---

## Security Notes

- **Never share your private key** (`id_ed25519` file)
- **Only share your public key** (`id_ed25519.pub` file) 
- **Use different SSH keys** for different devices/accounts
- **Remove SSH keys** from GitHub when you no longer use a device

---

## Need Help?

1. **Check error messages carefully** - they usually tell you what's wrong
2. **Test SSH connection** first: `ssh -T git@github.com`
3. **Verify Git configuration:** `git config --global --list`
4. **Ask for help** during class if stuck

**Remember:** SSH setup is a one-time process per device. Once configured, Git operations will work seamlessly!
````