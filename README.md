#Put Home Directory Under Version Control

If you want to have the entire home directory under git version control, you should start an empty git repo there:
```
cd ~
git init
```

From here, we can add the GitHub or GitLab repo as the origin of this repo:

```git remote add origin http://git_lab_ip/your_gitlab_user/repo_name.git```

After this point, we will need to do something a bit different if we already have files on this machine that may come into conflict with what is in our repo. For instance, a ~/.bashrc file is usually included by default for each user.

One option would be to delete or move each file that conflicts with our repo files. However, we can also just tell git to overwrite all conflicting files with the remote versions.

We can do this by first fetching the remote files, and then telling git to reset to the most recent commit, which should be our remote versions:

```
git fetch --all
git reset --hard origin/master
```

This should bring all of the remote files into our new machine.

You can easily modify files on this machine and push them back to the remote repo as well:

```
echo "# a comment" >> .bashrc
git add .bashrc
git commit -m "test"
git push origin master
```

Reference: https://www.digitalocean.com/community/tutorials/how-to-use-git-to-manage-your-user-configuration-files-on-a-linux-vps
