---
layout: post
title: Github+Jekyll+Markdown搭建个人博客
category: 工具

---

## Github Pages
Github 提供了[Github Pages](https://pages.github.com/)的服务,不仅可以方便的为项目建立介绍站点，也可以用来搭建个人博客。它有以下的优点：
1. 轻量级的博客系统，没有麻烦的配置
2. 使用标记语言，比如[Markdown](http://wowubuntu.com/markdown/)
3. 无需自己搭建服务器
4. 根据Github的限制，对应的每个站有300MB空间
5. 可以绑定自己的域名

#### 步骤一：登录 github,新建一个 username.github.io的仓库，像我的库名为 ：wzq1771993075.github.io
![username.github.io](https://raw.githubusercontent.com/wzq1771993075/wzq1771993075.github.io/master/assets/upload/username.github.io.png)
#### 步骤二： 将[https://github.com/suyan/suyan.github.io](https://github.com/suyan/suyan.github.io)  fork 到自己的仓库里 (此时你的仓库里 应该有两个 username.github.io这样的库了)，再下载到本地。
![fork](https://raw.githubusercontent.com/wzq1771993075/wzq1771993075.github.io/master/assets/upload/fork.png)
#### 步骤三： 将刚创建的username.github.io仓库clone到本地，尽管 里面什么都没有 。然后将suyan.github.io下的文件全部copy 到自己本地的仓库 。
#### 步骤四： 使用github桌面版，提交并同步。这时访问 username.github.io就可以进入suyan 的博客了(因为你的所有东西都是人家的啊  )。
如果不想利用username.github.io访问，可以申请一个域名，如我的wzq1771993075.me然后修改CNAME里的域名为自己的即可。
![yuming](https://raw.githubusercontent.com/wzq1771993075/wzq1771993075.github.io/master/assets/upload/yuming.png)
修改_config.yml文件
![_config](https://raw.githubusercontent.com/wzq1771993075/wzq1771993075.github.io/master/assets/upload/_config.png)
## 申请域名并解析
在万网上申请一个属于自己的域名，这个比较简单。我详细说一下该怎么解析。
点击解析
![jiexi](https://raw.githubusercontent.com/wzq1771993075/wzq1771993075.github.io/master/assets/upload/jiexi.png)
将记录类型勾选为A，这样是将此域名指向一个服务器的IP地址，像github给提供的服务器IP为192.30.252.153/192.30.252.154。
![jiexi1](https://raw.githubusercontent.com/wzq1771993075/wzq1771993075.github.io/master/assets/upload/jiexi1.png)
主机记录，因为我的域名为顶级域名，所以我选@，亲测改为www无效。你也可以通过添加解析按钮，解析多条。然后保存即可，等上10几分钟，通过浏览器访问自己申请的域名就可看到博客内容。

