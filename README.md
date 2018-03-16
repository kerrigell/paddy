# paddy
record my ansible playbook used by working and office

## 服务器信息修改
服务器信息记录在inventory.ini文件中，主要包括两大分类：
1. jumper：跳板机信息，一般设置为localhost，为运行ansible controller的当前机器
2. ops：运维操作机器，可以分若干组，需要把组名写到ops节点内

## 用户操作

### 添加新用户
1. 修改group_vars/all.yml文件，按yaml文件格式，将要增加的用户名作为列表补充到apply_users节点内
2. 运行 ansible-playbook createUser.yml,最后若没有错误表示增加完成
3. 新增用户的登录信息记录到ssh_keys/文件夹中
   * 用户名-id_rsa 是用户私钥
   * 用户名-id_rsa.pub 使用ssh公钥
   * 用户名-pwd.txt记录用户密码
4. 删除group_vars/all.yaml中，apply_users节点内列表内容

> 注意：每次运行ansible-playbook createUser.yml如其他条件不变，会自动修改用户密码！！！
