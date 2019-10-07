---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "New"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2019-10-07T16:04:12+07:00
lastmod: 2019-10-07T16:04:12+07:00
featured: false
draft: true

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
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