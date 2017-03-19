---
title: IOS-UIWebView
date: 2017-02-05 00:33:34
tags: ios
---

### UIWebView

##### 方法：

* ｀- (void)loadRequest:(NSURLRequest *)request;｀

	这是加载网页最常用的一种方式，通过一个网页URL来进行加载，这个URL可以是远程的也可以是本地的；

	<pre>
	UIWebView * view = [[UIWebView alloc]initWithFrame:self.view.frame];
    [view loadRequest:[NSURLRequest requestWithURL:[NSURL URLWithString:@"http://www.baidu.com"]]];
    [self.view addSubview:view];
	</pre>

* `- (void)loadHTMLString:(NSString *)string baseURL:(NSURL *)baseURL;`

	这个方法需要将httml文件读取为字符串，其中baseURL是我们自己设置的一个路径，用于寻找html文件中引用的图片等素材。

* `- (void)loadData:(NSData *)data MIMEType:(NSString *)MIMEType textEncodingName:(NSString *)textEncodingName baseURL:(NSURL *)baseURL;`

	这个方式使用的比较少，但也更加自由，其中data是文件数据，MIMEType是文件类型，textEncodingName是编码类型，baseURL是素材资源路径。
	
* `- (void)reload;//重新加载数据`
* `- (void)stopLoading;//停止加载数据`
* `- (void)goBack;//返回上一级`
* `- (void)goForward;//跳转下一级`
* `-(NSString *)stringByEvaluatingJavaScriptFromString:(NSString *)script;//通过JavaScript操作web数据`
	
##### 属性：
* `@property (nonatomic,assign)id <UIWebViewDelegate> delegate;//设置webView的代理`
*  `@property (nonatomic,readonly,retain)UIScrollView *scrollView;//内置的scrollView`
*  `@property (nonatomic,readonly,retain)NSURLRequest *request;//URL请求`
*   `@property (nonatomic,readonly,getter=canGoBack)BOOL canGoBack;//获取能否返回上一级`
*   `@property (nonatomic,readonly,getter=canGoForward)BOOL canGoForward;//获取能否跳转下一级`
*   `@property (nonatomic,readonly,getter=isLoading)BOOL loading;//获取是否正在加载数据`
*   `@property (nonatomic)BOOL scalesPageToFit;//设置是否缩放到适合屏幕大小`
*   `@property (nonatomic)UIDataDetectorTypes dataDetectorTypesNS_AVAILABLE_IOS(3_0);设置某些数据变为链接形式，这个枚举可以设置如电话号，地址，邮箱等转化为链接`
*   `@property (nonatomic)BOOL allowsInlineMediaPlaybackNS_AVAILABLE_IOS(4_0);//设置是否使用内联播放器播放视频`
*   `@property (nonatomic)BOOL mediaPlaybackRequiresUserActionNS_AVAILABLE_IOS(4_0);//设置视频是否自动播放`
*   `@property (nonatomic)BOOL mediaPlaybackAllowsAirPlayNS_AVAILABLE_IOS(5_0);//设置音频播放是否支持ari play功能`
*   `@property (nonatomic)BOOL suppressesIncrementalRenderingNS_AVAILABLE_IOS(6_0);//设置是否将数据加载如内存后渲染界面`
*   `@property (nonatomic)BOOL keyboardDisplayRequiresUserActionNS_AVAILABLE_IOS(6_0);//设置用户交互模式`

##### ios 7.0新特性：
下面这些属性是iOS7之后才有的，通过他们可以设置更加有趣的web体验

* <code>@property (nonatomic)UIWebPaginationMode paginationModeNS_AVAILABLE_IOS(7_0);</code>

* <pre>typedef NS_ENUM(NSInteger, UIWebPaginationMode) { 
    	UIWebPaginationModeUnpaginated,//不使用翻页效果
   		UIWebPaginationModeLeftToRight,//将网页超出部分分页，从左向右进行翻页
    	UIWebPaginationModeTopToBottom,//将网页超出部分分页，从上向下进行翻页
    	UIWebPaginationModeBottomToTop,//将网页超出部分分页，从下向上进行翻页
    	UIWebPaginationModeRightToLeft//将网页超出部分分页，从右向左进行翻页
    };
    </pre>
    
这个属性用来设置一种模式，当网页的大小超出view时，将网页以翻页的效果展示，枚举如下：
<pre>@property (nonatomic)CGFloat pageLengthNS_AVAILABLE_IOS(7_0);//设置每一页的长度
@property (nonatomic)CGFloat gapBetweenPagesNS_AVAILABLE_IOS(7_0);//设置每一页的间距
@property (nonatomic,readonly)NSUInteger pageCountNS_AVAILABLE_IOS(7_0);//获取分页数</pre>

##### webView协议中的方法
<pre>- (BOOL)webView:(UIWebView *)webView shouldStartLoadWithRequest:(NSURLRequest *)request navigationType:(UIWebViewNavigationType)navigationType;
//准备加载内容时调用的方法，通过返回值来进行是否加载的设置
- (void)webViewDidStartLoad:(UIWebView *)webView;//开始加载时调用的方法
- (void)webViewDidFinishLoad:(UIWebView *)webView;//结束加载时调用的方法
- (void)webView:(UIWebView *)webView didFailLoadWithError:(NSError *)error;//加载失败时调用的方法
</pre>

##### [UIWebView保存图片](http://www.cocoachina.com/ios/20160616/16660.html);


