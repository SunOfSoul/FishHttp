<h1>FishHttp</h1>

是一个超级轻量级的网络HTTP请求框架<br/>

fishhttp网络框架使用注解和伪Builder方式来配置请求参数， 最大限度的增加便捷性<br/>
对于AndroidStudio的开发者<br/>
准备工作：<br/>
1.Download或者git clone 到本地工程目录中<br/>
2.打开settings.gradle文件添加":fishhttp"在 include ':app', 后面  中间用逗号分隔<br/>
3.打开 module setting （F12快捷键 / F4快捷键） 选择需要使用http框架的工程 然后右边Dependencies -> module dependency :fishhttp<br/>
4.app的AndroidManifest中添加权限 <br/>
android.permission.INTERNET<br/>
android.permission.READ_PHONE_STATE<br/>
android.permission.ACCESS_NETWORK_STATE<br/>
android.permission.ACCESS_WIFI_STATE<br/>
5.在工程的build.gradle的buildscript -> dependencies节点添加<br/>
classpath 'me.tatarka:gradle-retrolambda:3.2.5' 支持lambda表达式<br/>

开始使用：<br/>
1.创建一个RequestHelper的实例 就像这样<br/>
@NetMethod(GET或者POST)<br/>
@NetUrl(你的URL地址～)<br/>
@Result(想在请求中返回的类.class)<br/>
RequestHelper<RESULT> request;<br/>
然后要在调用request之前调用NetInject.inject(this)把注解注入进来<br/>
PS： RequestHelper可以加泛型的 这样直接在回调中会返回想要的类型 方便操作<br/>
2.如果需要拼接URL请求字段 可以调用这个方法：<br/>
request.UrlParam(Serializable obj) 他会返回request自己  所以还可以继续点点点～～<br/>
PS：这个类中 大写字母开头的方法都会返回self的<br/>
3.如果需要添加post请求体数据，可以这样:<br/>
request.PostParam(Serializable obj) 和UrlParam差不多～<br/>
4.你可以设置回调～  <br/>
request.Success(Done<RESULT> done).Failed(Done<String> error msg);<br/>
不去设置也不会出现空指针～<br/>
使用JAVA8的LAMBDA表达式可以这样～<br/>
request.Success((result) -> {//TODO WITH result})<br/>
    .Failed((msg) -> {//TODO with msg});<br/>
最后 调用 request.post或者get(Context, Handler)来发送请求<br/>
<br/>
欢迎拍砖到我的邮箱哦~~<br/>
<br/>
EMAIL: pekphet@126.com<br/>

更新0.2<br/>
移除BASEENTITY的限制  可以解析任何javabean<br/>
<br/>










