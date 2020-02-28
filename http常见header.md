# http 常见的 header

## get 和 post 的区别

### get

- `GET` 方法请求指定的资源。使用 GET 的请求应该只用于获取数据。

### post

- `POST` 方法发送数据给服务器. 请求主体的类型由 Content-Type 首部指定.
  - 一个 `POST` 请求通常是通过 HTML 表单发送, 并返回服务器的修改结果. 在这种情况下, content type 是通过在 `<form>` 元素中设置正确的 enctype 属性, 或是在 `<input>` 和 `<button>` 元素中设置 formenctype 属性来选择的;
  - 当 POST 请求是通过除 HTML 表单之外的方式发送时, 例如使用 XMLHttpRequest, 那么请求主体可以是任何类型;

### 区别

- `get`只能获取数据，`post`可以发送数据，并返回服务器的修改结果

## http2

随着 web 应用的发展，更多的数据通过 HTTP 传输，HTTP/1.1 链接需要请求以正确的顺序发送，，带来的成本和复杂性堪忧。HTTP/2 应运而生。

HTTP/2 在 HTTP/1.1 有几处基本的不同:

- HTTP/2 是二进制协议而不是文本协议。不再可读，也不可无障碍的手动创建，改善的优化技术现在可被实施。
- 这是一个复用协议。并行的请求能在同一个链接中处理，移除了 HTTP/1.x 中顺序和阻塞的约束。
- 压缩了 headers。因为 headers 在一系列请求中常常是相似的，其移除了重复和传输重复数据的成本。
- 其允许服务器在客户端缓存中填充数据，通过一个叫服务器推送的机制来提前请求。

## https

是`HTTP`的安全版本，即有相应的`SSL`证书。

## 常见的header

### 文件信息

- Content-Tepy：
  - text/plain；普通文本
  - tex/html：html文本
  - application/x-javascript：js
  - application/x-www-form-urlencoded：默认形式表单发包类型
  - multipart/form-data：用在发送文件的post包中
  - application/json：通过json传输
  - application/xml：通过xml传输
- Content-Length:用于指定请求或相应的内容长度
  - 如果存在Transfer-Encoding（chuncked）则在头信息中不能有Content-Type有也会被忽略
  - 如果是短连接则可以通过关闭连接来确定长度
  - Content-Length必须与传输内容长度相同，过长会导致超时，过短会直接截断

### 压缩

- Accept-Encoding
- Content-Encoding

### 代理缓存

- Vary
  - Accept
  - Accept-Encoding
  - Accept-Language
  - Accept-Charset

### 缓存

- Expires：过期时间
- Cache-Control：缓存控制
  - max-age:指示在多少秒之内，缓存方不用向服务器发送这个文件的请求，直接使用缓存。在max-age时间之内，浏览器请求该文件的响应总是为200(from cache)
  - no-cache：强制缓存方必须每次都向服务器发送请求，由服务器决定缓存方保存的是否为最新的文件。如果为最新的，服务器就会返回304(Not Modified)，缓存方直接使用缓存；如果不是最新返回200，并返回最新的文件。一般配合last-modified或Etag一起使用。
  - no-store：强制缓存方永远不缓存该文件，每次都是向服务器请求最新的文件
  - public：表示任何缓存方都可缓存该响应
  - private：只会缓存给该用户不会共享缓存
- Etag/If-None-Match
  - 缓存方第一次请求时，服务器返回的响应头中会包含一个Etag的hash
  - 之后每次缓存方向服务器请求时都会包含一个If-None-Match头信息，内容为服务器返回的Etag，然后服务器对这个头信息进行判断，如果为最新的，服务器就会返回304(Not Modified)，缓存方直接使用缓存；如果不是最新返回200，并返回最新的文件，更新Etag字段。
- Last-Modified/If-Modified-Since：
  - 缓存方第一次请求时，服务器返回的响应头中会包含一个Last-Modified头信息，内容为该文件的最后更新时间
  - 之后每次缓存方向服务器请求时都会包含一个If-Modified-Since头信息，内容为服务器返回的Last-Modified，然后服务器对这个头信息进行判断，如果为最新的，服务器就会返回304(Not Modified)，缓存方直接使用缓存；如果不是最新返回200，并返回最新的文件，更新Last-Modified字段。

## post实例

request：

    POST bilibili.com HTTP/1.1
    accept:*/*
    accept-encoding:gzip, deflate, br
    accept-language: zh-CN,zh;q=0.9

response:

    cache-control: max-age=0, no-cache, no-store, must-revalidate
    content-language: zh-CN
    content-length: 754
    content-type: application/json
    date:Fri, 29 Feb 2020 00:00:00 GMT
    expires:Fri, 29 Feb 2020 00:00:00 GMT
    status: 200
    vary: Cookie
