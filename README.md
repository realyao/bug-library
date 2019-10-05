# bug library
git踩坑

使用原始的remote方式可能会出现不能push的情况，最好用htts的格式。

https类型的格式为：$ git remote add origin https://github.com/realyao/gityy.git

然后又会报错 error: failed to push some refs to 'https://github.com/realyao/gityy.git' hint: Updates were rejected because the remote contains work that you do hint: not have locally.

一般是因为远程库中已经存在readme.md文件了，所以需要先pull下来。

 使用 $ git pull origin master --allow-unrelated-histories
 
 默认会打开vim编辑器，按 i 切换到插入模式， Esc→：→wq 即可保存退出编辑器。如果不进入vim编辑器，则会自动生成一个合并代码的commit。然后再使用前面的命令push将本地提交推送到远程仓库。后面如果本地还有commit，就可以直接用 git push origin master 推送
