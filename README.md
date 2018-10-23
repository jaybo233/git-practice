# Git和GitHub练习地

——熟练使用 Git，GitHub。



1、如何在 GitHub 上添加协议？

1. 进入你的“代码仓库”，点击"Create new file"，这时 GIHub 的新页面上，有一个空格让你填入文件名称。

2. 在输入框输入文件名”LICENSE"，这里输入框的右侧会出现包含所有开源协议的列表，选择合适的开源协议，选择你需要的协议；

3. 点击“Commit new file”，这时你添加的开源协议就在代码仓库的菜单中了。

   参考：[如何在github上添加协议](https://www.jianshu.com/p/e4d6e6a05f14)



2、保持码云 Gitee 和 GitHub 同步更新？

参考：[使用码云](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00150154460073692d151e784de4d718c67ce836f72c7c4000)

``` xml
git remote add gitee git@gitee.com:liaoxuefeng/learngit.git
```

再关联码云的远程库，名称为 gitee。可以用`git remote -v`查看远程库信息。