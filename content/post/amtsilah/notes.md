git push origin -f HEAD^:mydev
git reflog

hapus repo 
git push

====Recover readme.md in github
It is not unrecoverable, there is a chance it exists on remote repository reflog. Normally you can't access remote repository reflog but github has events API.

# show the events on repo (including commits)
curl -u <username> https://api.github.com/repos/:owner/:repo/events

# create a new branch from the commit sha found in prev command
curl -i -u <username> -X POST -d '{"ref":"refs/heads/new-branch", "sha":"<lost-sha>"}' https://api.github.com/repos/:owner/:repo/git/refs

The first command lets you find the sha of lost remote commit. The second command lets you create a branch on that commit. Then simply fetch all changes on local repo and new branch should appear. After that simply merge that branch or cherry-pick the commit and push.

---------------------------------------------------------------------------
//git add creates a hash, compresses the file and adds the compressed object to the object store.
git hash-object helloworld
a0423896973644771497bdc03eb99d5281615b51

git cat-file a0423896973644771497bdc03eb99d5281615b51 -p
hello world!

Git consists of 3 parts: the object store, the index and the working directory.