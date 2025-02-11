# **POC of Pull Request in GitHub**

| **Author** | **Created on** | **Version** | **Last updated by**|**Internal Reviewer** |**Reviewer L0** |**Reviewer L1** |**Reviewer L2** |
|------------|---------------------------|-------------|---------------------|-------------|-------------|-------------|-------------|
| Aayush Verma|   10-02-2025             | v1          | Aayush Verma        |  Komal Jaiswal |  |   |      |


# Steps to Create a Pull Request (PR)

## **1. Create a Repository on GitHub**

**Log in to your GitHub**

 * Go to Repositories and click New.

 * Enter the name for your repository, choose public or private, and add a description if you want.

* Click Create Repository to set it up.


## **2. Clone the repository to your local system**

```
git clone <your-repo-link>
```


## **3. Change directory to your project directory**

```
cd <project_name>
```


## **4. Create a new branch and switch to the same branch**

```
git checkout -b <new_branch>            #Create and switch to the new branch at same time
```
or
```
git branch <new_branch>             #Creates new branch
git checkout <new_branch>           #Switch to new branch
```


## **5. Get all branches in your repository**

```
git branch
```

## **6. Make changes in the project**

```
echo "Changes made!!" >> file.txt
```


## **7. Check the status**

```
git status
```

## **8. Stage your changes**

```
git add <file name>
```


## **9. Commit the changes with a message**

```
git commit -m "PR demo"
```


## **10. Push your code to GitHub**

```
git push --set-upstream origin <new_branch>  #links your (new_branch) to the remote branch (origin/new_branch) 
                                             #git push upload changes to remote repository
```

## **11. Navigate to your GitHub repository to view the new branch**

![image](https://github.com/user-attachments/assets/4ba2608b-ceba-470e-b367-99278c2d57f2)

## **12. Access the "Pull Requests" section and initiate a new pull request.**

## **13. Select the branch you wish to merge with the base branch**


## **14. Submit the pull request with a title and comments.**

**NOTE:-** If you have Closing a Pull Request:-

**1.** Navigate to the Pull Request:

Go to the repository where the PR was submitted.

Click on the "Pull requests" tab.

Find the PR you want to close from the list and click on it to open the PR page.

**2.** Review the PR (Optional):

Before closing the PR, you may want to review the changes and comments to ensure that closing it is the appropriate action.

**3.** Close the PR:

Scroll down to the bottom of the PR page.

Click the "Close pull request" button. This button is usually located near the comment box.

**4.** Add a Comment :

You can add a comment explaining why you are closing the PR. This is especially useful if the PR is being closed without being merged.

Type your comment in the comment box and click "Comment" if you want to leave a note.

**5.** Confirm the Closure:

Once you click "Close pull request", the PR will be marked as closed. The status will change to "Closed", and the PR will no longer be open for further changes or comments unless it is reopened.

## **15. Merge the pull request.**

## **16. Review for any merge conflicts after submission.** 


## **17. If the branch is no longer required, delete it after merging the changes.**



# Contact Information

| **Name**    | **Email address**         |
|-------------|---------------------------|
| Aayush Verma | <aayushverma4481@gmail.com>   |

# References

| **Link** | **Description** |
|----------------------------------------------------|--------------------|
| <https://github.blog/developer-skills/github/beginners-guide-to-github-creating-a-pull-request/> | How create a Pull Request? |



