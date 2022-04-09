> REST  ：（Representational State Transfer）是一个标准、一种规范，遵循REST风格可以使开发的接口通用，便于调用者理解接口的作用，使用这种风格可以清晰地了解一个请求的目的是什么。  

**RESTful**架构风格规定，数据的元操作，即CRUD（create，read，update和delete，即数据的增查改删）操作，分别对应四种HTTP操作：

 - POST用来新建资源（也可以用于更新资源），

 - GET用来获取资源，

 - PUT用来更新资源，

 - DELETE用来删除资源。

 这样就统一了数据操作的接口，仅通过HTTP方法，就可以完成对数据的所有增查改删工作。即：  

 ◇ GET（READ）：从服务器取出资源（一项或多项）。
 ◇ POST（CREATE）：在服务器新建一个资源。
 ◇ PUT（UPDATE）：在服务器更新资源（客户端提供完整资源数据）。
 ◇ PATCH（UPDATE）：在服务器更新资源（客户端提供需要修改的资源数据）。
 ◇ DELETE（DELETE）：从服务器删除资源。  



### client结构

```go
type Client struct {
Transport RoundTripper
CheckRedirect func(req ＊Request, via []＊Request) error
Jar CookieJar
Timeout time.Duration
}
```

Client的结构相对较为简单，只有四个成员，分别是`Transport、CheckRedirect、Jar和Timeout`。
**Transport**指定执行独立、单次HTTP请求的机制。如果Transport为nil，则使用DefaultTransport。
**CheckRedirect**指定处理重定向的策略。如果CheckRedirect不为nil，客户端会在执行重定向之前调用本函数字段。参数req和via是将要执行的请求和已经执行的请求（切片，越新的请求越靠后）。如果CheckRedirect返回一个错误，本类型的GET方法不会发送请求req，而是返回之前得到的最后一个回复和该错误（包装进url.Error类型里）。如果CheckRedirect为nil，会采用默认策略：连续十次请求后停止。
**Jar**指定Cookie管理器。如果Jar为nil，请求中不会发送Cookie，回复中的Cookie会被忽略。
**Timeout**指定本类型的值执行请求的时间限制。该超时限制包括连接时间、重定向和读取回复
主体的时间。计时器会在Head、Get、Post或Do方法返回后继续运作，并在超时后中断回复主体的
读取。Timeout为零值表示不设置超时。  

### Request类型  

```go
type Request struct {
    Method string // 请求方法
    URL *url.URL // 请求地址
    Proto string // 协议版本， "HTTP/1.0"
    ProtoMajor int // 协议主版本号，“1”
    ProtoMinor int // 协议主副版本号，“0”
    Header Header // 请求头
    Body io.ReadCloser // 请求的Body
    ContentLength int64 // ContentLength记录相关内容的长度
    TransferEncoding []string // TransferEncoding按从最外到最里的顺序列出传输编码
    Close bool // Close在服务端指定是否在回复请求后关闭连接，在客户端指定是否在发送请求后关闭    连接
    Host string // Host指定URL会在其上寻找资源的主机
    Form url.Values // Form是解析好的表单数据，包括URL字段的query参数和POST或PUT的表单数据
    PostForm url.Values // PostForm是解析好的POST或PUT的表单数据
    MultipartForm ＊multipart.Form
    // MultipartForm是解析好的多部件表单，包括上传的文件
    Trailer Header // Trailer指定了会在请求主体之后发送的额外的头域
    RemoteAddr string // RemoteAddr允许HTTP服务器和其他软件记录该请求的来源地址，一般用于日志
    RequestURI string // RequestURI是被客户端发送到服务端的请求中未修改的URI
    TLS *tls.ConnectionState // TLS字段允许HTTP服务器和其他软件记录接收到该请求的TLS连接的信息
}
```

