# Version Control System Branching Exercise

This exercise illustrates how organizations implement continuous integration. The exercise demonstrates a project with fixed branches: Production, Hot Fix, Integration, Feature/Sprint 1, and Feature/Sprint 2.

The production branch is always in sync with the hotfix and the Integration branch. Any instant fix required on the production code is developed on the hotfix branch. The hotfix changes are then merged into both the production and the Integration branch.

![image](https://github.com/Career-Navigator-Academy/git-final-project/assets/152508691/dd985b05-2169-4540-b894-80f4d8ef2e6d)

## Exercise:

### 1. Create a Production branch:

You can create this on GitHub site or with Git CLI. We'll be using Git CLI:

```bash
git checkout -b production
```

#### a. Create a file in the production branch as the starting point:

Let's create a file called `profile.json` with some initial details, such as the name, age, and employee ID.

```bash
echo '{"name": "James Doe", "age": 27, "emp_id": 1234}' > profile.json
```

#### b. Commit and push changes to the remote production branch:

```bash
git add profile.json
git commit -m "Initial Commit to Production"
git push origin production
```

### 2. Create hot-fix and integration branches based on the production branch:

This ensures that the changes from the production branch are added to the new branches at creation time.

```bash
git branch hot-fix
git branch integration
```

#### a. Push the new branches to your remote:

```bash
git push origin hot-fix
git push origin integration
```

### 3. Create Sprint-1 and Sprint-2 or Feature-1 and Feature-2 branches based on the integration branch:

```bash
git checkout integration
git branch sprint-1
git branch sprint-2
```

#### a. Push the new branches to your remote:

```bash
git push origin sprint-1
git push origin sprint-2
```

### 4. Checkout sprint-2 branch and modify the profile.json by adding location:

#### a. Commit and push sprint-2 changes to the remote:

```bash
git checkout sprint-2
echo '{"name": "James Doe", "age": 27, "emp_id": 1234, "location": "123-street"}' > profile.json
git add profile.json
git commit -m "Add location to profile.json in sprint-2"
git push origin sprint-2
```

### 5. Merge sprint-2 into integration:

#### a. Push integration to remote:

```bash
git checkout integration
git merge sprint-2
git push origin integration
```

### 6. Merge integration into hot-fix:

#### a. Push hot-fix to remote:

```bash
git checkout hot-fix
git merge integration
git push origin hot-fix
```

### 7. Merge hot-fix into production:

#### a. Push production to remote:

```bash
git checkout production
git merge hot-fix
git push origin production
```

### 8. Checkout and Rebase sprint-1 branch with integration branch:

This is important because trying to merge sprint-1 changes into the integration branch will create a merge conflict as sprint-2 branch already modified the same file (profile.json) by adding location, and sprint-1 branch doesn't have this change yet. So, by rebasing, you get these changes sprint-2 made into sprint-1.

```bash
git checkout sprint-1
git rebase integration
```

### 9. Modify the profile.json by adding telephone:

#### a. Commit and push sprint-1 change to the remote:

```bash
echo '{"name": "James Doe", "age": 27, "emp_id": 1234, "location": "123-street", "telephone": "555-1234"}' > profile.json
git add profile.json
git commit -m "Add telephone to profile.json in sprint-1"
git push origin sprint-1
```

### 10. Merge sprint-1 into integration:

#### a. Push integration to remote:

```bash
git checkout integration
git merge sprint-1
git push origin integration
```

### 11. Merge integration into hot-fix:

#### a. Push hot-fix to remote:

```bash
git checkout hot-fix
git merge integration
git push origin hot-fix
```

### 12. Merge hot-fix into production:

#### a. Push production to remote:

```bash
git checkout production
git merge hot-fix
git push origin production
```

### 13. Checkout hot-fix branch and modify the profile.json by changing the employee ID:

#### a. Commit and push hot-fix change to remote:

```bash
git checkout hot-fix
echo '{"name": "James Doe", "age": 27, "emp_id": 5678, "location": "123-street", "telephone": "555-1234"}' > profile.json
git add profile.json
git commit -m "Change employee ID in hot-fix"
git push origin hot-fix
```

### 14. Merge hot-fix into integration:

#### a. Push integration to remote:

```bash
git checkout integration
git merge hot-fix
git push origin integration
```

### 15. Merge hot-fix into production:

#### a. Push production to remote:

```bash
git checkout production
git merge hot-fix
git push origin production
```
