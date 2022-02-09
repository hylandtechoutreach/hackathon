# Git - Merge Changes
Merging changes is one of the most crucial aspects of collaborating on a git project. When multiple developers are working on the same codebase simultaneously, it can be difficult to keep things running smoothly. This demonstration simulates a merge conflict, and shows how it is possible to resolve issues of this nature.

## Multiple Feature Branches - Instructor Walkthrough
>Note: For the "Instructor Walkthrough" portion, students should simply watch. Once it comes time to deal with merge conflicts, there will be an opportunity for students to test things out themselves.

For this example, we begin with a [repository](https://github.com/markbrendanawicz/TEST-REPO) that has some bugs. For the sake of simplicity, these bugs will be semantic/spelling mistakes within a block of text. These errors are all within a file named **Frankenstein.md**, which contains the first few paragraphs of Mary Shelley's Frankenstein. 

Here are the errors, grouped into three distinct categories:

**1. British Spellings**
- "splendour" should be "splendor"
- "tranquillise" should be "tranquilize"
- "favourite" should be "favorite"

**2. Name Mistakes**
- "Maggie" should be "Margaret"
- "Bart" should be "Homer"

**3. Spelling Errors**
- "rejoce" should be "rejoice"
- "abtain" should be "obtain"
- "affusions" should be "effusions"

### Fixing the Errors - Branching
Now, imagine there are a team of people dedicated to this project. Each individual is assigned one group of errors to fix, and they do this using _feature branches_. Let's call one of these people **Alice**, and another one **Bob**. **Alice** will work on Americanizing the text, and **Bob** will work on the name mistakes.

1. On the TEST-REPO repository on GitHub, create a new _branch_ named `alice-americanize-spelling`
    - This is where Alice will do her work
1. On the new branch, open the **Frankenstein.md** file for editing
1. Fix the three British spelling mistakes, and commit the changes
1. On the TEST-REPO repository, switch back to the `main` branch
1. There, create another new branch named `bob-fix-names`
    - This is where Bob will do his work
1. On the new branch, open the **Frankenstein.md** file for editing
1. Fix the two name mistakes, and commit the changes

Now there are two branches, each containing _some_ of the necessary bug fixes. The goal is to get both sets of changes into the `main` branch, WITHOUT them interfering with each other.

>Note: this example may seem contrived, but remember it is simply for demonstration purposes. In a real project, the changes would likely be much more complex.

### Merging the First Branch
The first part should be fairly straightforward - since both feature branches were directly copied from `main`, and there are no additional changes to `main`, there should be no conflicts with the first merge. Start with the `alice-americanize-spelling` branch.

1. Go to the "Pull requests" tab at the top of the page
1. Click on "New pull request"
1. For the "base" branch, keep `main`
1. For the "compare" branch, select `alice-americanize-spelling`
1. Check out the changes and click the "Create pull request" button
1. On the next page, click the "Create pull request" button
1. On the next page, click the "Merge pull request" button
    - Note: in the real world, pull requests should be reviewed by a team before merging
1. Click the "Confirm merge" button to merge the changes into `main`
1. Click the "Delete branch" button to delete the `alice-americanize-spelling` branch

Go back to the Code tab, and on the `main` branch, check out the **Frankenstein.md** files. All the spellings should be Americanized - the changes from Alice's feature branch should be there!

## Merging the Second Branch - Student Follow-Along Activity
This is where things get tricky - there will be merge conflicts. Switch to the `bob-fix-names` branch to see what's happening: the branch should be 1 commit ahead, but **2 commits behind** the `main` branch. This means that the `main` branch changes need to be merged into the `bob-fix-names` branch before _it_ can be merged into `main`. It's time to do some merging.

### Importing the Repository
For each student to have their own working copy of the TEST-REPO repository, it will be necessary to import one. Follow these steps:

1. Go to [GitHub.com](https://github.com)
1. In the upper right, click on the "+" dropdown and select "Import repository"  
    ![](https://i.imgur.com/Lj8Lz5w.png)
1. On the next page, paste in the TEST-REPO URL for "Your old repository's clone URL"
    - https://github.com/markbrendanawicz/TEST-REPO-TEST/
1. Enter "TEST-REPO" for the Repository Name
1. Click the "Begin import" button  
    ![](https://i.imgur.com/2U5Jjua.png)
1. Wait for the import to complete
1. Once the import is done, click the link to your new repository!  
    ![](https://i.imgur.com/wFDxqqQ.png)

### Merging `main` into `bob-fix-names`
Now that the repository is setup, it will be necessary to clone it locally. Follow the steps in the [Local Setup Guide](LocalSetup.md) to accomplish this. It is possible to accomplish these tasks using the command line, VS Code, or any number of other tools. For this activity, the command line will be used.

1. Open up a terminal, and `cd` into the newly-created repository's folder
    - In VS Code, this can be accomplished by going to Terminal -> New Terminal from the top nav bar  
    ![](https://i.imgur.com/qz5Wwgu.png)
1. Switch to the `bob-fix-names` branch by entering `git checkout bob-fix-names`
    - Check the **Frankenstein.md** file to make sure the name fixes are there
    - The Americanized spelling fixes should _not_ be there
1. Attempt to merge in the `main` branch by entering `git merge main`
    - An error should appear, saying that there are merge conflicts
1. Open up the **Frankenstein.md** file to see the merge conflict

#### Dealing with the Conflict
The syntax for merge conflicts is a little weird, but it basically shows you the change coming from one side compared to the change coming from the other side.

![](https://i.imgur.com/2nWhMv8.png)

Under `<<<<<<< HEAD` is the text as it currently is on the present branch. In the case of the `bob-fix-names` branch, it has properly swapped "Maggie" out for "Margaret", but it still has the British spelling of "splendour."

The `=======` separates the two versions, with one being above and one being below.

The `>>>>>>> main` indicates the end of the second version of the text. In the case of the `main` branch, it has the old name "Maggie," but it has the fix for "splendor."

The goal, then, is to take the good parts of each version, mash them together into one final version, and get rid of the `<<<<<<< HEAD`, `=======`, `>>>>>>> main`, and old versions. Ultimately, the fix should replace this:

```
<<<<<<< HEAD
There, Margaret, the sun is for ever visible, its broad disk just skirting the horizon and diffusing a perpetual splendour.
=======
There, Maggie, the sun is for ever visible, its broad disk just skirting the horizon and diffusing a perpetual splendor.
>>>>>>> main
```

with this:

```
There, Margaret, the sun is for ever visible, its broad disk just skirting the horizon and diffusing a perpetual splendor.
```

Once that's done, it's time to push it up.

1. Save the **Frankenstein.md** file
1. Open up the terminal again
1. Enter `git add Frankenstein.md` to mark the file as resolved
1. Enter `git commit -m "merge main"` to commit the change and conclude the merge
1. Enter `git push` to push the change up to the remote branch
1. Go to [GitHub](https://github.com) and check on the `bob-fix-names` branch in the TEST-REPO repository
    - It should now be **2 commits ahead** of `main`, and no commits behind!

### Creating a Pull Request for Bob's Branch
Now that all of the changes have been merged into the `bob-fix-names` feature branch, it's ready to be merged into `main`. This is possible via pull request.

1. On the TEST-REPO GitHub page, go to the "Pull requests" tab
1. Click on "New pull request"
1. For the "base" branch, keep `main`
1. For the "compare" branch, select `bob-fix-names`
1. Check out the changes and click the "Create pull request" button
1. On the next page, click the "Create pull request" button
1. On the next page, click the "Merge pull request" button
1. Click the "Confirm merge" button to merge the changes into `main`
1. Click the "Delete branch" button to delete the `bob-fix-names` branch

Go back to the Code tab, and on the `main` branch, check out the **Frankenstein.md** files. All the names should be fixed - the changes from Bob's feature branch should be there!

## Fixing the Additional Errors - Individual Work
There are still some bugs in the **Frankenstein.md** file! For some added practice, fix the additional spelling errors by following the proper process.

1. On the TEST-REPO repository in GitHub, create a new branch named `fix-spelling`
1. Make the changes to the **Frankenstein.md** file on the new branch
1. Create a pull request from the `fix-spelling` branch into the `main` branch
1. Merge in the changes!