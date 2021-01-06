# [Git与Github的连接与使用](https://www.cnblogs.com/flora5/p/7152556.html)

 

下面继续，使用git 将项目上传到GitHub上

首先要有GitHub账号,这就不用说了，没有的先注册，地址：[https://github.com](https://github.com/) 

没有仓库的话，先新创建一个仓库

![img](https://images2015.cnblogs.com/blog/1192146/201707/1192146-20170711180300993-19531117.png)s

![img](https://images2015.cnblogs.com/blog/1192146/201707/1192146-20170711180300993-19531117.png)

填写新仓库名称，备注信息。点击创建即可完成。

 

![img](https://images2015.cnblogs.com/blog/1192146/201707/1192146-20170711180434525-1461384261.png)

创建完成会显示如下界面。先放置不用管。后面会用到

 

![img](https://images2015.cnblogs.com/blog/1192146/201707/1192146-20170711180601197-948815634.jpg)

 

因为本地Git仓库和GitHub仓库之间的传输是通过SSH加密传输的，GitHub需要识别是否是你推送，GitHub只要知道了你的公钥，就可以确认只有你自己才能推送，所以需要配置ssh key。

1.创建SSH Key。

在用户主目录（C:\Users\Administrator）下，看看有没有.ssh文件，如果有，再看文件下有没有`id_rsa`和`id_rsa.pub`这两个文件，如果已经有了，可直接到下一步。如果没有，打开Git Bash，输入命令，创建SSH Key

```
$ ssh-keygen -t rsa -C ``"123@126.com"` `//123 是你自己注册GitHub的邮箱
```

直接回车就哦了

![img](https://images2015.cnblogs.com/blog/1192146/201707/1192146-20170714173049337-699715656.png)

出现上图，就说创建成功啦，再去用户主目录里找到`.ssh`文件夹，里面有`id_rsa`和`id_rsa.pub`两个文件，这两个就是SSH Key的秘钥对，`id_rsa`是私钥，不能泄露，`id_rsa.pub`是公钥，可以公开。

 

2.接下来到GitHub上，打开“Account settings”--“SSH Keys”页面，然后点击“Add SSH Key”，填上Title（随意写），在Key文本框里粘贴 `id_rsa.pub`文件里的全部内容。

![img](https://images2015.cnblogs.com/blog/1192146/201707/1192146-20170714173851775-474031887.png)

点“Add Key”，你就应该看到已经添加的Key，可以添加多个Key

![img](https://images2015.cnblogs.com/blog/1192146/201707/1192146-20170714174315025-1450935601.png)

 

3.验证是否成功，在git bash里输入下面的命令

```
$ ssh -T git@github.com
```

如果初次设置的话，会出现如下界面，输入yes 同意即可

![img](https://images2015.cnblogs.com/blog/1192146/201707/1192146-20170714175422400-33988795.png)

4.下面开始设置username和email，因为github每次commit都会记录他们

```
$ git config --global user.name ``"name"``//你的GitHub登陆名``$ git config --global user.email ``"123@126.com"``//你的GitHub注册邮箱
```

5.接下来就是把本地仓库传到github上去，之前在GitHub上建好一个新的仓库是，跳转的页面，完全按照上面的只是操作就可以了。

 

```
$ git remote add origin git@github.com:flora0103/example.git  ``//关联一个远程库命令， git@github.com:flora0103/example.git  这个是自己远程库``git push -u origin master  ``//关联后,第一次推送master分支的所有内容命令，此后，每次本地提交后，就可以使用命令git push origin master推送最新修改
```

 

 