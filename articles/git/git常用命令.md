## 设置ssh关联
### 设置全局name与email
- `git config --global user.name "xhyrzldf"`
- `git config --global user.email "xhyrzldf@gmail.com"`

### 生成ssh秘钥
- `ssh-keygen -t rsa -C "xhyrzldf@gmail.com"`


## 普通命令

 | 命令                 | 作用                   |
 | -------------------- | ---------------------- |
 | `git add .`          | 将指定文件提交至暂存区 |  |
 | `git commit -m "xx"` | 提交                   |  |


## 远程仓库命令
 | 命令                                          | 作用                 |
 | --------------------------------------------- | -------------------- |
 | `git remote -v`                               | 查看远程仓库列表     |  |
 | `git remote add [别名] [远程仓库地址]`        | 增加仓库             |  |
 | `git push [remote-name] [分支名]`             | 将数据推送至远程仓库 |  |
 | `git remote show [remote-name]`               | 查看远程仓库具体信息 |  |
 | `git remote rename [remote-name] [new-name] ` | 更改远程仓库名       |  |
 | `git remote rm [remote-name]`                 | 删除一个远程仓库     |  |

 ## 分支相关命令
- [x] 还未完成... 