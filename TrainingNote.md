# 2016.08.01：HTTP访问网络（李世祥）

## Handler的用法

自己的Github仓库中项目：Thread01的handler_step1分支
分支下若干版本（Commit）：

- 使用Handler实现最简单的多线程
- handler+ProgressBar
- Handler+ProgressBar+Loading_Image

Handler更适合于在任意两个线程之间的通信，或者是线程内部的通信

## HttpURLConnection

### 官方文档

<https://developer.android.com/training/basics/network-ops/connecting.html>

## Sunshine项目

### 获取API KEY

网址：

<http://www.openweathermap.org/>

### 在线解析JSON数据

<http://www.jsoneditoronline.org/>

###利用chrome的postman插件，调试网络服务端


####在线安装方法（需要翻墙）
访问 谷歌网上应用商店

<https://www.google.com/chrome/browser/desktop/index.html>

搜索postman

安装之后，运行：

<chrome://apps/>

登录帐号、密码：与Github一样
####离线安装方法
- 文件已经放在百度云上：
  链接: http://pan.baidu.com/s/1bni9Dzp 密码: kkgb
  解压下载的文件“Postman-REST-Client_v0.8.1”，内容文件结构如下：
  如何在Chrome下使用Postman进行rest请求测试
- 安装


  打开Chrome，依次选择“选项”>>"更多工具">>“扩展程序”，
  也可以在地址栏里直接输入：“chrome://extensions/”
  打开后如下图
  勾选“开发者模式”
  然后点击“加载已解压的扩展程序”，选择刚才我们下载并解压出来的文件夹。

- 运行

  打开chrome的“应用”，或者直接在地址栏里输入“chrome://apps/”也可以打开应用页面

- Get请求

  在地址栏里输入请求url：http://localhost:9998/api/user
  选择“GET”方式，
  点击"Url params",添加url params key:id , value:1
  点击“send”得到json数据

- Post请求

  在地址栏里输入请求url：http://localhost:9998/api/user/1
  选择“POST”方式，
  点击"application/x-www-form-urlencoded",
  添加key:name , value:baidu-lulee007
  添加key:sex , value:man

- Json


  如果服务端需要请求类型为json，需要在“headers”添加
  key:Content-Type   , value:application/json



## 程序调试

设置断点；Step In，Step Out

# 2016.08.02：HTML5微信开发（赵伟）

## 讲师简介

赵伟部长：大连东软

QQ:813411853

13841144236

zhaowei@neusoft.edu.cn

## 微信（WeChat）

移动互联网活跃数据

世界各地的WeChat排名

微信号类别：服务号、订阅号、企业号



NLP是神经语言程序学 (Neuro-Linguistic Programming) 的英文缩写。在香港，也有意译为[身心](http://baike.baidu.com/view/1152806.htm)语法程式学的。N (Neuro) 指的是神经系统，包括大脑和思维过程。L (Linguistic) 是指语言，更准确点说，是指从感觉信号的输入到构成意思的过程。P (Programming) 是指为产生某种后果而要执行的一套具体指令。即指我们思维上及行为上的习惯，就如同电脑中的程序，可以透过更新软件而改变。故此，NLP被解释为研究我们的大脑如何工作的学问。也因此，NLP译为“身心语法程式学”或“神经语言程序学”。



[客户关系](http://baike.baidu.com/view/1046465.htm)管理的定义是：企业为提高核心竞争力，利用相应的信息技术以及互联网技术来协调企业与顾客间在销售、营销和服务上的交互，从而提升其[管理方式](http://baike.baidu.com/view/712260.htm)，向客户提供创新式的个性化的客户交互和服务的过程。其最终目标是吸引新客户、保留老客户以及将已有客户转为忠实客户，增加市场份额。

##Chrome浏览器插件：Window Resizer

在Chrome网上应用商店搜索添加。

或采用离线安装方式：

# HTML5

学习网站

<http://www.w3school.com.cn/>

# JQuery

官网：

- <https://code.jquery.com/>
- <http://jquery.com/>
###JQueryMobile

要使用JQueryMobile，一定要在网页中引用对应版本的JQuery，可以从官网的演示实例或文档中看到对应的版本。

```
<link rel="stylesheet" href="http://code.jquery.com/mobile/1.4.5/jquery.mobile-1.4.5.min.css" />
<script src="http://code.jquery.com/jquery-1.11.1.min.js"></script>
<script src="http://code.jquery.com/mobile/1.4.5/jquery.mobile-1.4.5.min.js"></script>
```

# 2016.08.03：JQuery Mobile

## 把HTML页面打包成为APK

常用的两种方法：

- 用Android Studio

  1.  新建一个工程。

  2.  打开MainActivity.java页面，修改oncreate函数

      ```@SuppressLint(&quot;JavascriptInterface&quot;)
              public class MainActivity extends Activity {

              	private WebView webView;

              	@Override
              	protected void onCreate(Bundle savedInstanceState) {
              		super.onCreate(savedInstanceState);
              		setContentView(R.layout.activity_main);
              		
              		initWebview();
              	}
              	
              	private void initWebview() {
              		webView = (WebView) findViewById(R.id.webView1);
              	
              		// String url = "http://www.baidu.com";
              		String url = "file:///android_asset/index.html";
              	
              		WebSettings webSettings = webView.getSettings();
              		// 启用javascript
              		webSettings.setJavaScriptEnabled(true);
              		// 从assets目录下面的加载html
              		webView.loadUrl(url);
              		// web调用Android接口名称
              		webView.addJavascriptInterface(this, "wst");
              		// 覆盖WebView默认使用第三方或系统默认浏览器打开网页的行为，使网页用WebView打开
              		webView.setWebViewClient(new WebViewClient() {
              			@Override
              			public boolean shouldOverrideUrlLoading(WebView view, String url) {
              				// TODO Auto-generated method stub
              				// 返回值是true的时候控制去WebView打开，为false调用系统浏览器或第三方浏览器
              				view.loadUrl(url);
              				return true;
              			}
              		});
              	}
             } 
      ```

  3.  新建assets目录，用来存放html页面。右键app->new->folder->assetsfolder。把html页面放入assets目录。

  4.  预览看一下效果，提示wabpage not available错误，那么我们在AndroidManifest.xml文件中添加权限

         <uses-permission android:name="android.permission.INTERNET"/>

  5.  在Android Studio生成APK

        http://blog.csdn.net/sunylat/article/details/9239595

##微信公众平台开发

## 教程

<http://www.cnblogs.com/txw1958/p/wechat-tutorial.html>

https://mp.weixin.qq.com/wiki/home/index.html

# 2016.08.06 智慧商场购物管理系统解决方案

主讲人：

## [快速Android开发系列网络篇之Retrofit](http://www.cnblogs.com/angeldevil/p/3757335.html)

http://www.cnblogs.com/angeldevil/p/3757335.html

Android 调用C++：JNI

