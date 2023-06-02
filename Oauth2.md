授权码模式
- a提供一个连接，用户点击后跳转到b授权给a使用
- 链接包含cliend_id，重定向url，scope。要求返回code
- 包含cliend_id是让a知道是谁在请求，url是接受或者拒绝后要跳转的地址，scope是请求权限
- 跳转到b登录页面，询问是否同意授权。同意后会跳转url并传回code
- a拿到code就可以去请求令牌
- b收到请求会颁发令牌
