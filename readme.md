Readme of english version refers to [Readme_EN.md](https://github.com/cdhigh/KindleEar/blob/master/readme_EN.md)

# 简介
这是一个运行在Google App Engine(GAE)上的Kindle个人推送服务应用，生成排版精美的杂志模式mobi/epub格式自动每天推送至您的Kindle或其他邮箱。

# 标准部署步骤
1. [申请google账号](https://accounts.google.com/SignUp) 并暂时 [启用不够安全的应用的访问权限](https://www.google.com/settings/security/lesssecureapps) 以便上传程序。  

2. [创建一个Application](https://console.developers.google.com/project)，注意不用申请GCE，那个是60天试用的，而GAE是限额范围内永久免费的。  

3. 安装 [Python 2.7.x](https://www.python.org/downloads/)。  

4. 安装 [GAE SDK](https://cloud.google.com/appengine/downloads)。  

5. 下载 [KindleEar](https://github.com/cdhigh/KindleEar/archive/master.zip) ，解压到一个特定的目录。

6. 在以下三个文件中修改一些参数：  

  文件              |  待修改内容  | 说明                   |  
-------------------|-------------|-----------------------|  
app.yaml           | application | 你的ApplicationId      |  
module-worker.yaml | application | 你的ApplicationId      |  
config.py          | SRC_EMAIL   | 创建GAE工程的GMAIL邮箱   |  
config.py          | DOMAIN      | 你申请的应用的域名        |  

> 如果使用gcloud部署，需要注释掉yaml文件中的application/version项。

7. 转到GAE SDK安装目录(默认为：*C:\Program Files\Google\google_appengine*) 

8. 部署命令：
8.1 使用appcfg.py：  
	* `c:\python27\python.exe appcfg.py update kindleear目录\app.yaml kindleear目录\module-worker.yaml`  
	* `c:\python27\python.exe appcfg.py update kindleear目录`
8.2 使用gcloud：
    * `"C:\Program Files\Google\Cloud SDK\google-cloud-sdk\bin\gcloud.cmd" app deploy --version=1 KindleEar目录\app.yaml KindleEar目录\module-worker.yaml
    * `"C:\Program Files\Google\Cloud SDK\google-cloud-sdk\bin\gcloud.cmd" app deploy --version=1 KindleEar目录
    
9. 全部完成后就可以尝试打开域名：  
*http://appid.appspot.com*  (appid是你申请的application名字)  
比如作者的网站域名为：<http://kindleear.appspot.com/>  
**注：初始用户名为 admin，密码为 admin，建议登录后及时修改密码。**

10. 更详细一点的说明请参照Github上的 [FAQ](http://htmlpreview.github.io/?https://github.com/cdhigh/KindleEar/blob/master/static/faq.html) 或作者网站的 [FAQ](http://kindleear.appspot.com/static/faq.html) 链接。有关部署失败，部署后"internal server error"等问题都有解释。  
**不建议使用GAE Launcher部署KindleEar，除非你知道怎么设置Extra Flags等参数。**
11. 步骤已经说的很详细了，如果自己还是部署不成功，也可以选择直接捐赠给作者50块钱 ([Wiki捐赠页面](https://github.com/cdhigh/KindleEar/wiki/Donate))，然后将gmail地址和密码发给作者（先要提前关闭密码二步验证），作者负责帮你部署成功。有需要自定义抓取和分析其他网站的需求，也可以联系作者有偿实现。

# 使用Gcloud platform部署
1.	[设置电子邮件发件人](https://console.cloud.google.com/appengine/settings/emailsenders?project=zyfs-kindleear)
2.	在[terminal](https://console.cloud.google.com/home/dashboard?project=zyfs-kindleear)中:\
	`git clone https://github.com/Sciroccogti/zyfs-KindleEar.git`\
	`cd zyfs-KindleEar`\
	`gcloud app create`\
	`appcfg.py update app.yaml module-worker.yaml`\
	`update appcfg.py ./`
	
	>更新代码方法：\
	`git pull https://github.com/Sciroccogti/zyfs-KindleEar.git`\
	`appcfg.py update app.yaml module-worker.yaml`\
	`update appcfg.py ./`
	
# 许可协议
KindleEar is licensed under the [AGPLv3](http://www.gnu.org/licenses/agpl-3.0.html) license.  
大体的许可框架是此应用代码你可以任意使用，任意修改，可以商用，但是必须将你修改后的代码开源并保留原始版权声明。

# 主要贡献者
* @rexdf <https://github.com/rexdf> 
* @insert0003 <https://github.com/insert0003> 
* @zhu327 <https://github.com/zhu327> 
* @lord63 <https://github.com/lord63> 
* @th0mass <https://github.com/th0mass> 
* @seff <https://github.com/seff> 
* @miaowm5 <https://github.com/miaowm5> 
