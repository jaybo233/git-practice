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

删除已关联的名为`origin`的远程库：`git remote rm origin`

说明：本人用的同一个 SSH-key 的情况下，在提交代码`git push`时候貌似只提交到了 GitHub 远程仓库（但好像会同步到 Gitee，只是非常慢，我没去耐心等待，待测）；若要提交到 Gitee，则再需`git push gitee master`。

后面我按下面方式配置了多个 SSH-key，`git push`提交后，最后 Gitee 和 GitHub 是能同步更新的，但 Gitee 同步速度非常慢。



3、Git 配置多个 SSH-key？为什么？

参考：

- [Git配置多个SSH-Key](https://gitee.com/help/articles/4229#github)
- [一台电脑配置多个ssh key（不同的多个邮箱ssh key，多git账号，智能选择对应的ssh key）](https://blog.csdn.net/yimingsilence/article/details/79980135)
- [管理git生成的多个ssh key](https://www.jianshu.com/p/f7f4142a1556)

背景：当有多个 git 账号时，比如

a. 一个 gitee，用于公司内部的工作开发；
b. 一个 github，用于自己进行一些开发活动；

1. 生成一个公司用的 SSH-Key

   ``` xml
   ssh-keygen -t rsa -C 'xxxxx@company.com' -f ~/.ssh/gitee_id_rsa
   ```

2. 生成一个 github 用的SSH-Key

   ``` xml
   ssh-keygen -t rsa -C 'xxxxx@qq.com' -f ~/.ssh/github_id_rsa
   ```

3. 在 ~/.ssh 目录下新建一个config文件，添加如下内容（其中Host和HostName填写git服务器的域名，IdentityFile指定私钥的路径）

   ``` xml
   # gitee
   Host gitee.com
   HostName gitee.com
   PreferredAuthentications publickey
   IdentityFile ~/.ssh/gitee_id_rsa
   
   #github
   Host github.com
   HostName github.com
   PreferredAuthentications publickey
   IdentityFile ~/.ssh/github_id_rsa
   ```

4. 用ssh命令分别测试

   ``` xml
   ssh -T git@gitee.com
   ssh -T git@github.com
   ```

