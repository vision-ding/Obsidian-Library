iSH可以模拟linux环境，因此在iSH上的操作与真实的linux操作类似。

##### 安装git
`apk update`
`apk upgrade`
`apk add git`
`apk add openssh`

##### 创建ssh key 并授权给github
`ssh-keygen -t ed25519 -C "email"  -- 生成ssh key`
`cat ~/.ssh/id_ed25519.pub  --在github上授权这个公钥`
`ssh -T git@github.com  --测试iSH是否能正常连接github`

##### 配置git环境：
`git config --global user.name "name"`
`git config --global user.email "email"`

##### 添加安全目录
`git config --global --add safe.directory "*"`  -- 不然在使用git时会出现报错：fatal:detected dubious ownership in repository