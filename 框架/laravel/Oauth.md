##### 前言

本票文章主要关于 Oauth 授权，做一个简略的介绍。

##### 简介

Oauth 主要用来进行第三方的认证授权，有四种认证模式，常用的且安全性较高的是授权码模式。

主要的认证流程，以微信登陆为例来说明。在客户端唤起微信授权，获得授权码，请求服务器的相应接口，将授权码作为参数，服务器使用授权码以及 app_secret 去请求微信服务器，拿到 access_token，使用 access_token 去请求微信的用户信息接口拿到用户信息。

这就是一个 Oauth 授权的完整流程，无论是 web 还是 api ，背后的原理都一样。