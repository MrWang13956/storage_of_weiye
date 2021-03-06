### 一、Ubuntu下GitHub环境的搭建

1. 安装Git，使用命令sudo apt-get install git

2. 到GitHub创建GitHub账号

3. 生成ssh key，使用命令ssh-keygen -t rsa -C “用户名”，一直enter，enter，enter

   ls -a 查看隐藏生成文件  ~/.ssh

4. 回到github，进入edit profile—personal setting，左边选择SSH Keys，Add SSH Key,  title随便填，粘贴key。key就是id_rsa.pub内容。

5.  测试ssh key是否成功，使用命令“ssh -T git@github.com”，如果出现You’ve successfully authenticated, but GitHub does not provide shell access 。这就表示已成功连上github。

6. 配置Git的配置文件，username和email
   git config --global user.name “your name” //配置用户名    本地git
   git config --global user.email “your email” //配置email
   查看配置信息：
   git config user.name
   git config user.email

### 二、创建仓库并使用

1. 在github创建一个新的repository    my_first_project

2. 在Ubuntu建立一个文件夹  用于工程存储

3. 举例说明

   ```
   echo "# my_first_project" >> README.md
   git init
   git add README.md
   git commit -m "first commit"
   git branch -M main
   git remote add origin git@github.com:MrWang13956/my_first_project.git
   git push -u origin main
   ```

4. 克隆工程

   git clone git@github.com:MrWang13956/my_first_project.git

5. 拉取工程

   git pull git@github.com:MrWang13956/my_first_project.git





### 三、常用命令记录

**1. 分支指令**

```
git branch  			 -->查看当前分支
git branch -r 			 -->查看远程分支
git branch -M xxx        -->更改当前使用分支名
git branch xxx 			 -->创建分支
git branch -d xxx 		 -->删除指定分支
git checkout xxx         -->切换分支
git merge dev 			 -->合并dev分支到当前分支
git diff branch1 branch2 --> 显示出两个分支之间所有有差异的文件的详细差异
git diff branch1 branch2 --start --> 显示两个分支之间所有有差异的文件列表
git diff branch1 branch2 xxx     --> 显示指定文件的详细差异
git checkout -b xxx origin/xxx   --> 拉取远程分支并在本地创建该分支
git fetch origin master:tmp      --> 新建一个tmp分支,将远程仓库的master分支代码版本复制到tmp分支上,不会自动合并
git fetch                        --> 将远程分支拉取到本地,并在本地新建一个与远程分支名字一样的本地分支
git fetch origin xxx远程分支名    --> 拉取xxx远程分支变为本地分支
git pull origin xxx远程分支名     --> 拉取远程分支的代码到新建的本地分支

```

**2. 其他操作**

```
git status               -->红色表示在工作区/绿色表示在暂存区

git diff                 --> 比较暂存区与工作区
git diff --cached        --> 比较版本区与暂存区
git diff master          --> 比较版本区与工作区

git rm xxx               -->删除文件
git rm -rf xxx           -->删除文件夹


git log                  --> 显示从最近到最u按的所有提交日志,如果出现 ':' 表示为输出完成,出现end后最后完成
git reflog               --> 显示每次提交(commit)的 commit id
git reset --hard HEAD^   --> 版本回退(回退一次提交),^^表示回退两次 - 最多回退两次
git reset --hard 版本号  --> 回退到指定版本号的commit id 版本

git reset HEAD           --> 用版本库中的文件去替换暂存区的全部文件
git checkout --x.txt     --> 用暂存区指定的文件去替换工作区的指定文件(危险操作)
git checkout HEAD x.txt  --> 用版本库中的文件替换暂存区和工作区的文件(危险操作)
git rm --cached x.txt    -->从暂存区删除文件

```

