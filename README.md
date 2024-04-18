# node-red 的docker启动包


配置文件在./data/settings.js


首先 更改一个password
```bash
git clone https://github.com/kerwin-cn/docker-node-red.git
cd docker-node-red
# 启动容器
docker-compose up -d

# 进入容器
docker-compose exec node-red bash
```

```bash
node-red-admin hash-pw
# 输入自己的密码得到一串。。。。。"$2b$08$5LHg...."
# 退出容器

#退出到宿主机后 修改settings.js
vim data/settings.js
```

```json
// 打开data/settings.js 文件，改成
...
    adminAuth: {
        type: "credentials",
        users: [{
            username: "admin",
            //这一段改成自己设置的密码 "$2b$08$5LHg...."
            password: "$2b$08$5LHg....",
            permissions: "*"
        }]
    },
...
//保存退出 exit 容器，返回到宿主机

```

```bash
# 重启docker
docker-compose restart # 访问 http://host:1880
```