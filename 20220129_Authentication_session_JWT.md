# 身份认证

## Cookie

Cookie是一段不超过4KB的小型文本数据，由一个名称（Name）、一个值（Value）和其它几个用于控制Cookie有效期、安全性、使用范围的可选属性组成。

### 特性：

1. 自动发送
2. 域名独立
3. 过期时限

## Session

Session与cookie功能效果相同。Session与Cookie的区别在于Session是记录在服务端的，而Cookie是记录在客户端的。

### 两种实现方式

#### 通过cookies实现

把 `session` 的 `id` 放在cookie里面，在请求头中携带cookie，服务器获取到cookie中的 `session` 的 `id` 后进行校验

#### 通过URL重写来实现



## JWT

## What is JSON Web Token（JWT）?

JSON Web Token (JWT) is an open standard ([RFC 7519](https://tools.ietf.org/html/rfc7519)) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the **HMAC** algorithm) or a public/private key pair using **RSA** or **ECDSA**.



## Composition

In its compact form, JSON Web Tokens consist of three parts separated by dots (),

- Header
- Payload
- Signature

Therefore, a JWT typically looks like the following.

```
xxxxx.yyyyy.zzzzz
```

