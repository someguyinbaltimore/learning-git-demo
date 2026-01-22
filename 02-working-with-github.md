# Working with Github - learning-git-demo
It's been 2 years since my last commit and I'm embarrased. So I have to play catchup.
I  had to install wsl on this windows pc I'm currently using so I figured I'd get Git setup and running as well.
In this post, I will talk about a few important commands needed to work with Github after you've installed and setup Git.

# Initialize or Clone a repository into a directory as a Git repository

### Setup and Initializing
1. Open a terminal or wsl
2. Change to the working directory or create a new folder.
3. Run `git init`

### cloning a repo
1. Open terminal or wsl
2. Change to the working directory that you want the cloned repo to go.
3. Run `git clone`, and then paste the URL of the project.
Example:
`git clone https://github.com/someguyinbaltimore/learning-git-demo`

# Getting your files to your repo (After you have created something).

### 1. Check what has changed.
```
git status
```

### 2. Add the file to staging. 
### (Add one file)
```
git add filename.txt
```

### (Add every file you created or you changed)
```
git add .
```

### 3. Commit the change.
```
git commit -m "Add initial file / update content"
```

### 4. Push the file(s) to GitHub.
```
git push
```

*Note:* If it's your first time pushing this repo, you may get an error telling you there is no upstream branch. To resolve this use the following command.
`git push -u origin main` (or `master` if that's your branch name)

# Quick workflow
If you already know what files you changed or doing a quick update. Use the following commands.
```
git add .
git commit -m "Your comment"
git push
```

I wrote this for my own memory and reference, but if you found this helpful. I'm happy for that as well. If y ou did find this and you made it this far, I want to sincerely wish you good luck and success on your journey.
