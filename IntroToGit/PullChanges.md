# Pull Changes
When you want to retrieve changes from the server, you will have to **pull** those changes down. You can pull changes from a personal or team GitHub repository.

For this activity, create a new file on the server repository. On the repository page, click the "Add file" button and select the "Create new file" option:

![](https://i.imgur.com/GNNcTrX.png)

Fill out a name and content for the file, enter a commit message, and click the green "Commit new file" button at the bottom of the page:

![](https://i.imgur.com/ze40UPZ.png)

Now there will be a change to pull down from the server to the local clone!

## Pulling Changes in Visual Studio Code
Visual Studio Code has an interesting tool for pulling changes down from the remote repository. Instead of simply pulling changes, it actually _synchronizes_ the local and remote repositories. This means that it pushes any commit changes up, and also pulls down any changes from the server that may exist.

To pull your changes down, use the **Synchronize Changes** button on the blue bar at the bottom of the window:

![](https://i.imgur.com/SLM4MiV.png)

Once you click that button, your server changes should exist in your local clone! You can go to your repository on GitHub and make sure it matches your local repository.

## Pulling Changes via the Command Line
If you're using the command line, pulling from your server repository is simple:

1. Change your directory to the folder that contains your repository (replace `/path/to/repository/` with your path) 
    ```bash
    cd /path/to/repository/
    ```
1. Run the `pull` command
    ```bash
    git pull
    ```

That's it! Now your local clone repository should have all the latest changes from your GitHub repository.