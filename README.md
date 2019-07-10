# learning-how-to-use-git
#### 准备工作

* Git 使用 git init 命令来初始化一个 Git 仓库   使用当前目录作为Git仓库，我们只需使它初始化。 生成 .git 文件

* 使用以下命令生成 SSH Key：   $ ssh-keygen -t rsa -C "youremail@example.com"

* 成功的话会在 ~/ 下生成 .ssh 文件夹，进去，打开 id_rsa.pub，复制里面的 key，填入github中

* 为了验证是否成功，在git bash下输入：  $ ssh -T git@github.com
* 如果是第一次的会提示是否continue，输入yes就会看到：You've successfully authenticated, but GitHub does not provide shell access 。这就表示已成功连上github。

```git
$ mkdir runoob-git-test                     # 创建测试目录
$ cd runoob-git-test/                       # 进入测试目录
$ echo "# Git 测试" >> README.md     # 创建 README.md 文件并写入内容
$ ls                                        # 查看目录下的文件
	README
$ git init                                  # 初始化
$ git add README.md                         # 添加文件
$ git commit -m "添加 README.md 文件"        # 提交并备注信息
[master (root-commit) 0205aab] 添加 README.md 文件
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

# 提交到 Github
$ git remote add origin git@github.com:tianqixin/runoob-git-test.git
$ git push -u origin master
```

#### 提交文件

* 第一步：使用命令 git add readme.txt添加到暂存区里面去。
* 第二步：用命令 git commit告诉Git，把文件提交到仓库。     //git commit -m "内容"
                  我们下面可以通过命令git status来查看是否还有文件未提交，
                  使用git diff readme.txt 看下readme.txt文件到底改了什么内容
* 第三步：用命令 git push 更新github
                  知道了对readme.txt文件做了什么修改后，我们可以放心的提交到仓库了，
                  提交修改和提交文件是一样的2步(第一步是git add 第二步是：git commit，中间可以用git status检查)。