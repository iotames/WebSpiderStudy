## 网络爬虫概述（概念，分类，流程）


### 爬虫的概念

网络爬虫（英语：web crawler），也叫网络蜘蛛（spider），是一种用来自动浏览万维网的网络机器人。
从一个网络请求页面开始，解析网络响应的数据，再获取新的请求链接，再发起新的网络请求，直到所有页面都爬取完毕为止。
就如同蜘蛛网一般，一个网页为一个结点，通过网页里面的URL链接，与其他网页建立联系，在所有页面节点里抓取数据。

爬虫的本质，就是一个个网络请求的发起和网络响应的解析。


### 爬虫的分类

1. 通用爬虫（泛爬虫）和聚焦爬虫

2. 静态页面和动态的JS渲染页面

3. HTML数据和API数据

4. 网页端和APP端


### 爬虫流程

1. 网站页面分析：检查网页元素和API接口请求，分析URL构造和页面跳转规则
2. 建立数据模型：数据字段映射和类型约束
3. 模拟网络请求：直接构建网络请求，操纵浏览器获取数据
4. 数据清洗和存储：处理异常值、缺失值、重复值...数据存储到PostgreSQL、MongoDB、Mysql...
5. 数据分析和展示：读取分析仓库基础数据，生成导出文件: 如Excel、统计图表


## 爬虫的底层基础

[互联网分层协议栈](InternetLayer.md)


### HTTP协议简介

1. 释名： HTTP 协议是 HyperTextTransferProtocol（超文本传输协议）的缩写。

2. 源流：提到 HTTP 协议，就得提到 TCP/IP 协议，它是全世界互联网数据传输的统一标准和规范。`TCP/IP协议族` 通常分为四层（也有分为五层的），又叫 `TCP/IP四层模型` ：网络接口层（物理层和数据链路层），网络层，传输层，应用层。HTTP 为 `应用层` 协议 ，基于传输层的 TCP 协议。

3. 特点：默认占用服务端 80 端口。在正式的数据传输之前，要先经过 3 次握手确认连接。比 udp 协议速度慢，而可靠性强。内容包含：请求和响应的消息头 header 和消息体 body

4. 应用场景：平时浏览网页和应用程序的接口数据交互。

5. 请求动作：GET,POST,PUT,DELETE 等。


## 数据包的抓取


### Request请求，Response响应和Header头

![HTTP网络请求](images/chromef12.png)


## 网络抓包工具和MITM中间代理人技术

1. 谷歌浏览器开发者工具: 谷歌浏览器 => 更多工具 => 开发者工具（Ctrl+Shift+I）或者直接按F12键

2. 中间代理人工具mitmproxy: https://www.mitmproxy.org/

3. Charles和Fiddler

![HTTP网络请求](images/chrome_http_package.png)

![mitmproxy](images/mitmproxy.png)


## 数据解析和入库

1. CSS选择器和XPATH：HTML和XML
2. JSON解析
3. 正则表达式提取数据


## 爬虫工具和开发框架

| 编程语言 | 类型   | 使用方式 | 名称 |功能| 网址 |
| ----- | --------- | ----------- | ----- | ------- | ----|
| Python | 工具库 | 引入库包 | requests|基础包，简单的HTTP请求|https://github.com/psf/requests|
| Python | 爬虫框架 | 文件框架 |  scrapy | 一体化框架 | https://github.com/scrapy/scrapy|
| Python | 工具库 | 引入库包 |  BeautifulSoup|解析HTML或XML|https://beautifulsoup.readthedocs.io/zh-cn/|
| Python | 工具库 | 引入库包 |  selemiun|解析动态的HTML网页|https://www.selenium.dev/zh-cn/documentation/|
| Python | 工具库 | 引入库包 | DrissionPage |解析动态的HTML网页|https://drissionpage.cn/|
| Go语言 | 工具库 | 引入库包 | net/http|基础包，简单的HTTP请求。原生工具，无需安装| https://pkg.go.dev/net/http |
| Go语言 | 爬虫框架 | 引入库包 | colly| 一体化框架 | https://github.com/gocolly/colly|
| Go语言 | 工具库 | 引入库包 | chromedp|解析动态的HTML网页|https://github.com/chromedp/chromedp|

- Python常用：requests，scrapy，DrissionPage
- Go语言常用：net/http，colly，chromedp


## IP代理池和隧道代理

目的：隐藏真实IP，解除单个IP的访问频率限制

## 常见反爬技术

- 验证码：亚马逊
- 滑块：淘宝
- 限制访问频率
- User-Agent和Referer请求头限制（初级）

## AI辅助

- 通义灵码，可以整合到代码编辑器或IDE https://tongyi.aliyun.com/lingma/
- 通义千问 https://tongyi.aliyun.com/qianwen/
- 深度求索 https://chat.deepseek.com
- KIMI（支持联网搜索） https://kimi.moonshot.cn
- cursor IDE https://www.cursor.com/
- windsurf IDE https://codeium.com/windsurf


## 网络爬虫法律法规


### 相关法规

- 中华人民共和国国家互联网信息办公室-网络爬虫的法律规制：https://www.cac.gov.cn/2019-06/16/c_1124630015.htm

- 中华人民共和国著作权法：未经著作权人许可，复制、发行、展示或传播他人作品的行为可能构成侵权。
- 中华人民共和国个人信息保护法：不得非法收集、使用、加工、传输他人个人信息。
- 中华人民共和国网络安全法：网络运营者应当采取技术措施和其他必要措施，确保网络安全，防止网络数据泄露或者被窃取、篡改。
- 中华人民共和国电子商务法：对电子商务经营者的数据抓取行为进行了规范，不得滥用市场支配地位，不得进行不正当竞争。
- 中华人民共和国民法典：民法典中有关于隐私权和个人信息保护的规定，爬虫行为不得侵犯他人的隐私权。
- 中华人民共和国刑法：如果爬虫行为涉及非法获取计算机信息系统数据、非法控制计算机信息系统等行为，可能构成犯罪，触犯《刑法》的相关条款。


### 爬虫君子协议

虽然robots协议不是法律，但它是网站经营者通过robots.txt文件告知爬虫哪些内容可以爬取，哪些不可以爬取的行业规范。

- https://www.baidu.com/robots.txt
- https://www.amazon.com/robots.txt
