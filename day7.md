# git
> 什么是git，有什么作用
* git是目前最好用的分布式版本控制系统,git主要用来版本控制，利用git能快速回退以前的版本.
> 如何查看git日志
* 利用git log 命令即可查看git历史提交日志
> 如何回退之前的版本
* 可以先利用git log命令查看历史提交日志，找到想要回退的版本id，然后利用git reset --hard id回退到相应版本
> 如何修改git commit信息？
* 利用 git commit --amend命令可以帮助我们重写上一次的提交信息,此时会进入编辑器界面，即可修改
> 如何合并分支
* 在分支中完成新建文件等任务后，可以用git checkout master切回到master仓库，然后利用git merge 分支名,将分支合并
