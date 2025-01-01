# GitCommitGPT

Automate commit message creation with a script that fetches Git diffs, sends them to ChatGPT for generating commit messages, and commits with the auto-generated message.

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/your-repo/GitCommitGPT.git
   cd GitCommitGPT
   ```

2. Create a symbolic link to make the script globally accessible:
   ```bash
   sudo ln -s /path/to/GitCommitGPT/gitcommitgpt /usr/bin/gitcommitgpt
   ```

   Verify the link:
   ```bash
   ls -l /usr/bin/gitcommitgpt
   ```

3. (Optional) Install clipboard utilities for easier usage:
   - Install `wl-clipboard` (for Wayland environments):
     ```bash
     sudo apt install wl-clipboard
     ```
   - Install `xclip` (for X11 environments):
     ```bash
     sudo apt install xclip
     ```
   - Install `xsel` (alternative for X11):
     ```bash
     sudo apt install xsel
     ```

   These utilities allow the generated commit message to be automatically copied to the clipboard.

## Usage

1. Stage changes in your Git repository:
   ```bash
   git add .
   ```

2. Run the script to generate a commit message:
   ```bash
   gitcommitgpt
   ```

3. The script will:
   - Check for staged changes.
   - Fetch the `git diff` and generate a meaningful commit message using ChatGPT.
   - Copy the commit message to the clipboard (if `wl-clipboard`, `xclip`, or `xsel` is installed).

4. Review and commit the changes:
   ```bash
   git commit -m "$(wl-paste)"
   ```

   If using `xclip`:
   ```bash
   git commit -m "$(xclip -o)"
   ```

   Or, if using `xsel`:
   ```bash
   git commit -m "$(xsel --clipboard --output)"
   ```

## Dependencies

- Bash
- Git
- `wl-clipboard` (for Wayland environments)
- `xclip` or `xsel` (for X11 environments, optional for clipboard functionality)
