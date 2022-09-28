# Ubuntu新建用户

> [USTC lug](<https://101.lug.ustc.edu.cn/Ch05/>)

## 新建可图形用户界面登录的用户

```bash
# 切换到root用户获取权限
sudo su
# 添加一个用户
adduser sunshuqing
# 查看用户属性
cat /etc/passwd
# 查看当前组
groups
# 添加到sudo组
sudo adduser sunshuqing sudo
# 切换到新用户
su sunshuqing
```
