# Introduction - learning-git-demo 

This is just a sample repository where I document my journey using github on macOS. GitHub is a developer platform that allows developers from all over the world create, store, manage, and share their code. Over the years I have written lots of code, but nothing I would say was worth sharing. Learning to use Git more fluently and posting at least one of my projects is one of my personal goals. 

# Create a GitHub Account

Assuming you have already created a GitHub account you can follow along. If you have not created an account, you can click the following link to [create a GitHub account](https://docs.github.com/en/get-started/start-your-journey/creating-an-account-on-github).

# Setup Git
So we know what GitHub is but what is Git? Git is the open-source version control system (VCS) that powers GitHub. It's responsible for anything GitHub Related that happend on your computer.

### Install Git on macOS

To learn to install git you can visit the [official git download page](https://git-scm.com/download). 

If you're on a mac you can run the following command to install Apple Xcode tools which ships with a copy of [Xcode](https://developer.apple.com/xcode/). 

This is the following method I used:

1. [Open a new terminal window](https://mac.install.guide/terminal/open)
2. Type `xcode-select --install` and press **Enter**
3. You'll see a message that asks you to install Xcode Command Line Tools
4. Click 'Install' to begin the download and install. Be aware the install time depends on your internet connection. 
	- If you receive an error: "xcode-select: error: command line tools are already installed" Run the following command in the same terminal window:
	`sudo rm -rf /Library/Developer/CommandLineTools`
5. To verify that the install was successful run the following command:
`Softwareupdate --history | grep "Command"`
### Setting your username in Git

1. Open Terminal (See: Step 1 in previous section)

2. Set A Git Username with the following command:
`git config --global user.name "UserName Goes Here"`

3. Confirm that you set the username correctly:

    $ git config --global user.name
    > UserName Goes Here

###  Set your commit email address in Git

1. Open Terminal
   
2. Set an email address in Git. You should use your GitHub-provided noreply email address or any email that you want to use. Use the following Command:
   `git config --global user.email "YOUR_EMAIL"`

3. Confirm that you have set the email address correctly in Git:
    $ git config --global user.email
    > email@example.com

4. If you use a different email than you used when you signed up for your GitHub account you will need to [Add the email address to your account on GitHub](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/adding-an-email-address-to-your-github-account)so that your commits are attributed to you and will appear in your contributions graph. 

# Connect to GitHub with SSH

Now that Git is setup we will need to connect to GitHub. We will [setup an SSH connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) to authenticate using an SSH key instead of using other credentials or a username and password. I'll assume you don't have any existing SSH keys. If you are unsure, you can use the steps on the [Checking for existing SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys) article from the GitHub Docs. 

### Generate a new SSH key and add it to ssh-agent

1. Open Terminal
2. Paste the command below replace the email used in the example with your GitHub email address.
   `ssh-keygen -t ed25519 -C "your_email@example.com"`
3. When you're prompted to "Enter a file in which to save the key" Press **Enter**
4. At the prompt, type a secure passphrase.

#### Add your ssh key to the ssh-agent

1. Type the following command to start the ssh-agent in the background.
   `eval "$(ssh-agent -s)"`

2. Now let's modify the `~/.ssh/config` file to automatically load the keys into the ssh-agent and store the passphrases in the keychain.
	- First we have to check in the files exists. 
	  `open ~/.ssh/config`
	- If the files doesn't exist, you can create the file with the following command:
	  `touch ~/.ssh/config`
	- Open the file:
	  `open ~/.ssh/config`
	- Copy and passte the following text into the file:
	
			Host github.com
			  AddKeysToAgent yes
			  UseKeychain yes
			  IdentityFile ~/.ssh/id_ed25519
	
	- Save the file
	
3. Add your SSH private key to the ssh-agent and store your passphrase in the keychain.
`ssh-add --apple-use-keychain ~/.ssh/id_ed25519`

4. Last step will be to add the SSH public key to your account on GithHub. For more informatiom, see: Next Section.

#### Add SSH key to your GitHub account

1. Copy the SSH public key to your clipboard
`pbcopy < ~/.ssh/id_ed25519.pub`

2. Visit SSH keys settings page on Github.com
https://github.com/settings/keys 

3. Click "New SSH key" button in the top right corner of the page.

4. Change the title to reflect the computer that this key is stored on.

5. Paste the SSH public key that you copied in Step 1.

6. Success you are now ready to create a respository.
