# notes
遇到的问题以及解决方法记录

## ssh免密登陆vps

  本地先生成密钥(默认名称id_rsa,id_rsa_pub)
  
  
  `
  ssh-keygen -t rsa
  `

```
cd ~
cd .ssh
cat id_rsa.pub
```

把本地公钥文件上传到服务器

`
 scp ~/.ssh/id_rsa.pub root@x.x.x.x:/root/.ssh/
`

使用密码远程登陆一次vps服务器,进入根目录,进入.ssh目录,把当前目录下的id_rsa.pub改名为authorized_keys

`
cd ~
`

`
cd .ssh
`

`
mv -f id_rsa.pub authorized_keys
`


搞定,下次就可以直接登陆

`
ssh root@xxx.xx.xx.xx
`


## 服务端子路由刷新404

[官方配置](https://router.vuejs.org/zh/guide/essentials/history-mode.html)

[nginx配置 详细说明](https://www.cnblogs.com/Miss-mickey/p/6734831.html)


## 撤销到git pull之前的状态

`
git pull --rebase origin master
`

从远程仓库把代码下载下来再集成。
rebase保证本地文件夹是干净的。
这个操作删掉了本地很多文件，若想回到之前的状态。

查看提交记录

`
git reflog master
`

commit后面就是上传文件的描述(说明)，可以根据说明找到想回滚的位置。

`
5e87e7a master@{1}: commit: upload
`

找到位置执行代码，搞定。

`
git reset --hard master@{1}
`
