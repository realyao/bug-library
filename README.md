# git踩坑 进阶全记录

选择一个合适的地方，创建一个空目录：

$ mkdir learngit

$ cd learngit

$ pwd

/Users/michael/learngit

通过git init命令把这个目录变成Git可以管理的仓库：

使用原始的远程方式可能会出现不能push的情况，最好用htts的格式。
https类型的格式为：

$ git remote add origin https://github.com/realyao/gityy.git

然后又会报错错误：无法将一些引用推送到“ https://github.com/realyao/gityy.git ”提示：更新被拒绝，因为远程包含您确实提示的工作：本地没有。
一般是因为远程库中已经存在readme.md文件了，所以需要先拉下来。

使用$ git pull origin master --allow-unrelated-histories

默认会打开vim编辑器，按i切换到插入模式，Esc→：→wq即可保存退出编辑器。如果不进入vim编辑器，可以自动生成一个合并代码的提交。然后再使用前面的命令push将本地提交推送到远程仓库。后面如果本地还有commit，就可以直接用git push origin master推送


### .git文件夹

工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。

## push方法

第一步，用命令git add .告诉Git，把文件添加到仓库：

第二步，用命令git commit告诉Git，把文件提交到仓库：
$ git commit -m "描述"

第三步， $ git push -u origin master

## 回退版本

git log命令显示从最近到最远的提交日志

  用HEAD表示当前版本，也就是最新的提交1094adb...（注意我的提交ID和你的肯定不一样），上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。

$ git reset --hard HEAD^  // 回退上个版本

$ git reset --hard 1094a

HEAD is now at 83b0afe append GPL

版本号没必要写全，前几位就可以了，Git会自动去找。当然也不能只写前一两位，因为Git可能会找到多个版本号，就无法确定是哪一个了。

$ git reflog  //用来记录你的每一次命令

## 远程克隆

yuyao@laptop-yuyao MINGW64 ~/gityy (master)

$ git clone https://github.com/realyao/to-zly.git        //https 或 url

Cloning into 'to-zly'...

remote: Enumerating objects: 27, done.

remote: Counting objects: 100% (27/27), done.

remote: Compressing objects: 100% (23/23), done.

remote: Total 27 (delta 5), reused 0 (delta 0), pack-reused 0

Unpacking objects: 100% (27/27), done.

yuyao@laptop-yuyao MINGW64 ~/gityy (master)
$ ls

README.md  readme.txt  test2.txt  to-zly/



## 创建ssh key

$ ssh-keygen -t rsa -C "youremail@example.com"

GitHub允许你添加多个Key。假定你有若干电脑，你一会儿在公司提交，一会儿在家里提交。

“有了远程仓库，妈妈再也不用担心我的硬盘了。”——Git点读机

## 分支 与 协作

