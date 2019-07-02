### WebStorm和GitHub互传文件
#### GitHub的代码传到WebStorm
- 首先要下载Git，网上搜索Git，进入官网下载。
- 打开WebStorm，点开File -- Settings（Ctrl+Alt+S）分别对Git和GitHub进行配置：
	- 搜索GitHub -- 点击Add account -- 输入账号密码 -- 点击Log In，链接到你的GitHub账户。
	 ![3.png](attachments\3.png)
	- 搜索Git – 输入你的Git安装路径 – 点击Test，完成配置。
	 ![4.png](attachments\4.png)
- 获取本地的ssh（如果没有获取会报错）：
	- 打开你Git安装目录下的git-bash.exe。
	- 输入ssh-keygen -t rsa -C “你的邮箱”,输入完后按四次回车。
	- 在C盘 -- 用户 -- 用户名里面找到.ssh文件，点开找到id_rsa.pub文件，打开复制里面的内容。
	- 打开你的GitHub账户，点击Settings -- 点击SSH and GPG keys –点击New SSH key,将刚才的内容复制进去即可。
	![5.png](attachments\5.png)
- 接下来回到WebStorm，点击VCS -- 点击Checkout from Version Control -- 点击Git—在本地文件中选择要上传代码的路径—点击Clone，上传成功。
![6.png](attachments\6.png)

#### WebStorm的代码传到GitHub
- 在已经获取了本地ssh的前提下（如果没有获取会报错）：
- 点击VCS – Import into Version Control – Share Project on GitHub – 点击Share即可
![7.png](attachments\7.png)