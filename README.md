# Git workflow

This is gitflow for team development projects. It helps developers to track changes in the codebase and collaborate with other developers.

Created by [RyanLee] from **RushB**.

Source: [nvie.com](https://nvie.com/posts/a-successful-git-branching-model/)

<img src="https://nvie.com/img/git-model@2x.png">

## Initial Setup
### New Repository
```bash
git init
```

### Add files to the staging area
```bash
git add .
```

### Commit changes
```bash
git commit -m "commit message"
```

### Modify branch name from master to main
```bash
git branch -M main
```

### Add remote repository
```bash
git remote add origin <repository-url>
```

### Push changes to the remote repository
```bash
git push -u origin main
```

### Create a new branch for development with name "develop"
```bash
git branch develop
```

### Push the develop branch to the remote repository
```bash
git push -u origin develop
```

## Existing repository(Join the project)
### Clone the repository
```bash
git clone <repository-url>
```

### Create a new branch
```bash
git checkout -b <branch-name>
```

### Make changes to the code

### Add changes to the staging area
```bash
git add .
```

### Commit changes
```bash
git commit -m "commit message"
```

## Project manager creating issues for the project
1. Go to the issues tab in the repository
2. Click on the "New issue" button
3. Add issue title and description
4. Assign the issue to the developer(ryan, john, etc)
5. Add labels to the issue (bug, feature, enhancement, etc)
6. Click on the "Submit issue" button

## Developer working on the issue
1. Create a new branch feature with the issue number(#1) and title
```bash
git checkout -b feature/1-add-login-page
```

2. Make changes to the code
3. Add changes to the staging area
```bash
git add .
```

4. Commit changes with the issue number(#1) and title
```bash
git commit -m "#1 - Add login page"
```

5. Push changes to the remote repository
```bash
git push 
```
or 
```bash
git push -u origin feature/1-add-login-page
```

> *That the issue number(#1) and title should be included in the commit message to link the commit to the issue.*

## Project manager reviewing the changes
1. Go to the pull requests tab in the repository
2. Click on the "New pull request" button
3. Select the base branch(main) and compare branch(feature/1-add-login-page)
4. Add pull request title and description
5. Click on the "Create pull request" button
6. Review the changes and click on the "Merge pull request" button
7. Confirm the merge by clicking on the "Confirm merge" button
8. Delete the branch after merging the changes

## Developer fetching the changes from the develop branch
1. Switch to the develop branch
```bash
git checkout develop
```

2. Fetch the changes from the remote repository
```bash
git pull
```

3. Checkout to release branch example release-v1.0.0
```bash
git checkout -b release-v1.0.0 develop
```

4. Create tag for the release example v1.0.0
```bash
git tag 'v1.0.0'
```

```bash
git push --tags
```

5. Merge the changes from the develop branch to the release branch
```bash
git merge develop
```

6. Push the changes to the remote repository
```bash
git push
```

## Project manager creating a release
1. Go to the repository
2. Click on the "Compare & pull request" button
3. Select the base branch(release-v1.0.0) and compare branch(main)
4. Add release title and description
5. Click on the "Create pull request" button
6. Review the changes and click on the "Merge pull request" button
7. Confirm the merge by clicking on the "Confirm merge" button

## Developer fetching the changes from the main branch
1. Switch to the main branch
```bash
git checkout main
```

2. Fetch the changes from the remote repository
```bash
git pull
```

3. Create tag for main branch example v1.0.0
```bash
git tag 'v1.0.0'
```

```bash
git push --tags
```

4. Push the changes to the remote repository
```bash
git push
```

## Developer clear the local branches
1. List all the branches
```bash
git branch
```

2. Delete the feature branch
```bash
git branch -d release-v1.0.0
```

## Developer clear the remote branches
1. List all the remote branches
```bash
git branch -r
```

2. Delete the remote feature branch
```bash
git push origin -d release-v1.0.0
```

> *Delete the local and remote branches after merging the changes to the main branch*

## Hotfixes branch to main branch
1. Create a new branch hotfix with the issue number(#2) and title
```bash
git checkout -b hotfix/2-fix-login-page
```

2. Make changes to the code
3. Add changes to the staging area
```bash
git add .
```

4. Commit changes with the issue number(#2) and title
```bash
git commit -m "#2 - Fix login page"
```

5. Push changes to the remote repository
```bash
git push 
```
or 
```bash
git push -u origin hotfix/2-fix-login-page
```

> *That the issue number(#2) and title should be included in the commit message to link the commit to the issue.*

## Project manager reviewing the hotfixes
1. Go to the pull requests tab in the repository
2. Click on the "New pull request" button
3. Select the base branch(main) and compare branch(hotfix/2-fix-login-page)
4. Add pull request title and description
5. Click on the "Create pull request" button
6. Review the changes and click on the "Merge pull request" button
7. Confirm the merge by clicking on the "Confirm merge" button
8. Delete the branch after merging the changes
```bash
git checkout main
```
Local branch
```bash
git branch -d hotfix/2-fix-login-page
```
Remote branch
```bash
git push origin -d hotfix/2-fix-login-page
```
> Delete the local and remote branches after merging the changes to the main branch

## Hotfixes branch to develop branch
1. Switch to the develop branch
```bash
git checkout develop
```

2. Merge the changes from the hotfix branch
```bash
git merge hotfix/2-fix-login-page
```

3. Push the changes to the remote repository
```bash
git push
```

4. Create release branch example release-v1.0.1
```bash
git checkout -b release-v1.0.1 develop
```

5. Create tag for the release example v1.0.1
```bash
git tag 'v1.0.1'
```

```bash
git push --tags
```

6. Merge the changes from the develop branch to the release branch
```bash
git merge develop
```

7. Push the changes to the remote repository
```bash
git push
```

## Project manager creating a release
1. Go to the repository
2. Click on the "Compare & pull request" button
3. Select the base branch(release-v1.0.1) and compare branch(main)
4. Add release title and description
5. Click on the "Create pull request" button
6. Review the changes and click on the "Merge pull request" button
7. Confirm the merge by clicking on the "Confirm merge" button

## Developer fetching the changes from the main branch
1. Switch to the main branch
```bash
git checkout main
```

2. Fetch the changes from the remote repository
```bash
git pull
```

3. Create tag for main branch example v1.0.1
```bash
git tag 'v1.0.1'
```

```bash
git push --tags
```

4. Push the changes to the remote repository
```bash
git push
```

## Developer clear the local branches
1. List all the branches
```bash
git branch
```

2. Delete the local hotfix branch
```bash
git branch -d hotfix/2-fix-login-page
```

3. Delete the remote hotfix branch
```bash
git push origin -d hotfix/2-fix-login-page
```

> *Delete the local and remote branches after merging the changes to the main branch*


## Developer handling merge conflicts
1. Fetch the changes from the remote repository
```bash
git pull
```

2. Switch to the develop branch
```bash
git checkout develop
```

3. Merge the changes from the main branch
```bash
git merge main
```

4. Resolve the merge conflicts
5. Add changes to the staging area
```bash
git add .
```

6. Commit changes
```bash
git commit -m "Merge changes from main branch"
```

7. Push changes to the remote repository
```bash
git push
```

## Developer handling rebase
1. Fetch the changes from the remote repository
```bash
git pull
```

2. Switch to the develop branch
```bash
git checkout develop
```

3. Rebase the changes from the main branch
```bash
git rebase main
```

4. Resolve the rebase conflicts
5. Add changes to the staging area
```bash
git add .
```

6. Continue the rebase
```bash
git rebase --continue
```

7. Push changes to the remote repository
```bash
git push
```

## Developer handling revert changes
1. Fetch the changes from the remote repository
```bash
git pull
```

2. Switch to the develop branch
```bash
git checkout develop
```

3. Revert the changes from the main branch
```bash
git revert <commit-hash>
```

4. Resolve the revert conflicts
5. Add changes to the staging area
```bash
git add .
```

6. Commit changes
```bash
git commit -m "Revert changes from main branch"
```

7. Push changes to the remote repository
```bash
git push
```

## Conclusion
This is a basic Git workflow that you can follow to collaborate with other developers on a project. Git provides a powerful set of tools that can help you track changes in the codebase and work together with other developers effectively. By following the steps outlined above, you can contribute to the project and collaborate with other developers seamlessly.