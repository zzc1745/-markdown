# Git基础操作

1. 查看git版本号   git --version
2. 创建文件        touch index.html
3. 初始化git       git init
4. 查看git配置     git config
5. git添加文件 
   * 添加单个文件   git add index.html
   * 添加某一类文件 git add *.html
   * 添加全部文件   git add.
6. 查看git状态     git status
7. 删除某个文件    git rm --cached index.html
8. 备注commit 
   * 备注单个文件   git commit -m "备注单个上传文件"
   * 备注全部文件   git commit .
   * 退出备注界面   ESC ==> :wq   或者  ESC ==> ZZ			 
9. 忽略某个文件
   * 创建指定文件   tonch .gitignore
   * 在 .gitignore 文件中输入想要忽略的文件名、文件夹名
     书写格式:
	 index.html  （单个文件）
	 \aaa        （文件夹）
10. 分支操作	  
	  * 创建某个分支   git branch  mybranch
    * 切换到分支处   git checkout  mybranch
		* 在分支上操作，编写代码，不影响主线开发
		* 分支合并到主线 git merge mybranch 记得要push
		* 本地分支连接git仓库  
	    git remote add origin https://github.com...
			git remote
		  git push -u origin master
    
		 
