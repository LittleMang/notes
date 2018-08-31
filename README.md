# notes
遇到的问题以及解决方法记录

ssh免密登陆vps

  本地先生成密钥(默认名称id_rsa,id_rsa_pub)
  
  `
  ssh-keygen -t rsa
  `

`
cd ~
cd .ssh
cat id_rsa.pub
`

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
