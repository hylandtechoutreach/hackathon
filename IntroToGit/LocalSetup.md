# Git - Local Setup
To complete this activity, you should have a GitHub account and a repository created. There are instructions here for working with Visual Studio Code, as well as command line instructions. There are several other Git GUIs and integrations, but the options below are recommended.

## Downloading and Installing Git
In order to actually clone a GitHub Repository locally, it will be necessary to download and install Git.

- On a Mac or Linux machine, download Git from here: https://git-scm.com/downloads
- On a Windows machine, download Git from here: https://gitforwindows.org/
    - This comes with Git BASH, a command-line utility

## Cloning the Repository
Once you have everything downloaded and installed, you can clone your repository on your local machine to play around with it!  A **clone** is a copy of a repository that lives on your computer instead of on a website's server somewhere.

1. On the right side of your repository page, click the green **Code** button
    - Make sure you are on the **HTTPS** menu
1. Click the _copy_ icon to copy your repository URL to your clipboard  
    ![](https://i.imgur.com/ggwFhPd.png)

Depending on which tool you are using, follow the instructions in one of the sections below to complete the cloning process.

### Cloning in Visual Studio Code
If you have installed Git on your machine, Visual Studio Code has built-in Git tools you can use.

1. Open Visual Studio Code
1. Press `Ctrl`+`Shift`+`P` to open the Command Palette
1. Type in ">Git: Clone" and press `Enter` to execute the command  
    ![](https://i.imgur.com/WEoYQer.png)
1. Paste in your repository URL and press `Enter` to confirm  
    ![](https://i.imgur.com/djjRyK8.png)
1. Navigate to a suitable location for your repository folder, and click the **Select Repository Location** button  
    ![](https://i.imgur.com/ELgHyHy.png)
1. Once your repository is cloned, a popup should appear in the lower right corner of the window. Click the **Open** button to open the newly cloned repository
    ![](https://i.imgur.com/BrYDU2p.png)

That's it! Now you have a local clone of your repository.

### Cloning via the Command Line
If you have Git Bash installed on your machine (or another shell), you can use that for all Git commands.

1. Open your shell application (e.g. Git Bash)
1. Change your directory to wherever you'd like the repository to live
    ```bash
    cd /path/to/folder/
    ```
1. Use the `clone` command to clone the repository (paste in the repository's url after `clone`)
    ```bash
    git clone https://github.com/YOUR_REPO_URL.git
    ```

That's it! Now you have a local clone of your repository.