# DevOps

## VPS on Vagrant

### 自动化配置(Chef)

#### 服务器环境组件
- Ubuntu 14.04 LTS
- Nginx
- Unicorn
- PostgreSQL
- Redis
- Ruby(rbenv)

#### Chef

手动操作

SSH + VPS（APT）

自动操作

##### 工具

大厨 -> 菜谱 -> 配方

- Chef/Chef Solo
- Knife/Knife Solo
- Berkshelf

##### 自动化配置服务器环境组件

```bash
vagrant init ubuntu/trusty64
vagrant up
# vagrant ssh

# gem install bundler
# touch Gemfile
# bundle install
# bundle exec knife solo init .
# bundle exec berks install
bundle exec knife solo prepare vagrant@127.0.0.1 -p 2222
bundle exec knife solo cook vagrant@127.0.0.1 -p 2222
```

##### 说明
###### 术语
- 配方(recipe)

  定义安装单个组件(Niginx/Monit)所需的命令。

- 食谱(cookbook)

  相关的配方集合，例如，“mysql”食谱中包含 MySQL 服务器配方和 MySQL 客户端配方。

- 节点(node)

  要配置的远程服务器。

- 角色(role)

  一系列配方的组合，应用到节点上时，就称为一个角色。

- 数据包(data bag)

  配方所用的元数据，保存为 JSON 格式文件。例如，要创建的用户列表，以 相应的公钥。

- Chef 仓库(chef repository)

  一系列节点和角色定义。

##### 过程

```bash
chef generate cookbook site_cooks/redis

```

### 自动化部署(Capistrano)
