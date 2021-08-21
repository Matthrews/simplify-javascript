# 浏览器中，JSON Web Tokens\(JWT\)应该存放在哪里？

在客户端我们有三种存储方式，它们各有利弊，接下来我们一一介绍

* Cookie
* localSroage
* sessionStorage

### Cookie

如果你将J`WT`保存在`Cookie`上，每次发起同域请求浏览器都会自动在请求头带上`JWT`信息。但是却很容易收到[`CSRF`](https://en.wikipedia.org/wiki/Cross-site_request_forgery)攻击

我们可以通过在响应头上带上`SameSite=Strict`或者`SameSite=Lax`来防止`CSRF`攻击

响应头带上`httpOnly`可以有助于缓解[`XSS`](https://en.wikipedia.org/wiki/Cross-site_scripting)攻击

`Set-Cookie: id=a3fWa; Expires=Wed, 21 Oct 2015 07:28:00 GMT; SameSite=Strict; Secure; HttpOnly`

优点：

* 浏览器发请求会自动带上cookie给服务器
* 可控性好

缺点：

* 容易受到XSS攻击
* 数量和长度会受到限制，每个域名下最多只能有20个cookie，并且跨域不能共享；每个

  cookie大小不能超过4Kb，否则会被截断

### localStorage



