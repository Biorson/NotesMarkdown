

[TOC]

## 使用SSHkey

```shell
ssh-keygen -t rsa
三个连续的回车
会生成id_rsa和id_rsa.pub（密钥和公钥）
将你的id_rsa.pub中的内容添加到你的GitHub、Gitee等等中的NEW SSHkey

```



##远程代码-->本地(可选择分支)

```shell
git clone git@git.hrlyit.com:scf/scf-batch.git
```

```shell
git clone -b dev-v2.0.0 git@git.hrlyit.com:scf/scf-rules.git
```



## 提交本地代码-->远程仓库

每次提交代码前都应该进行一次git pull，以免发生冲突

```shell
git pull
git status(查看发生变化的文件)
git add . (添加所有发生变化的文件到缓存区)
git commit -m '备注' （提交缓存区的内容到远程仓库）
```

## 创建和删除分支

```shell
git checkout -b dev origin/dev  (创建本地dev分支并与远程仓库dev分支关联)
git branch -a (查看本地和远程仓库分支)
git branch -d/D <branchName> (强制)删除本地分支
```



## 合并和放弃合并分支代码

```shell
git checkout release (切换到合并的分支)
git merge dev --no-ff -m "注释" (合并分支dev的代码到release分支)
git push origin release
```





## 回退代码

### 单个文件

#### 未提交，放弃修改的代码

```shell
git checkout mulu/xxx.txt
```



### 已提交，回退到某个版本的代码

```shell
git log /xx/xxx.txt --查看提交单个文件的提交记录
git reset 
```



## 更换远程仓库地址

```shell
git remote set-url origin git@git.hrlyit.com:fengsibo/lls-bee-base-1.0.0.git
```

