## 币威开放平台

币威开放平台为第三方开发者提供接入使用币威钱包的一系列服务，分为二种接入方式：
1. H5接入方式，第三方开发的H5网页嵌入到币威钱包，可以利用币威钱包完成用户登录、支付等操作。
2. APP-SDK输出方式，第三方自己的APP可以嵌入币威提供的SDK（Android和iOS平台），完成用户对接，使自己的APP拥有区块链钱包功能。

### 接入流程
1. 不管哪种接入方式，请先联系币威团队开通开发权限，联系邮箱：dev@bitcv.com
2. 根据接入方式的不同，可能需要提交企业账号或服务器回调地址(URL)等信息。成为开发者后，币威会为第三方开发者提供相关 appId、appsecret等账号信息
3. 下载相应SDK代码和demo开始开发

### H5接入指南：
H5接入需要前后端一起对接，其中网页授权登录的流程可采用前后端共同接入或单独后端接入；使用JS-SDK发起支付和分享等操作需要在前端页面接入，并在后端利用appsecret生成签名给前端调用、获取用户信息、生成订单和撤单等。
相关文档：

1. [后端签名机制](./doc/sign.md)  
部分接口调用需要进行数据签名，务必在服务器后端签名，不要把appsecret暴露到网页里。
2. [网页授权登录](./doc/auth.md)  
如果用户在币威钱包客户端中访问第三方网页，可以通过币威钱包网页授权机制，来获取用户基本信息，进而实现业务逻辑。
3. [JS-SDK 使用文档](./doc/JS-SDK.md)  
通过使用币威 JS-SDK，网页开发者可借助币威APP使用支付、分享等能力，未来还将开放更多功能。
4. [订单支付相关](./doc/otcOrder.md)  
后端创建订单，请求币威开放平台获取订单号，再由前端用户发起支付。


### APP-SDK接入指南：
通过嵌入币威 APP-SDK，项目方App无需开发任何和区块链相关的代码，便拥有了钱包的存储、转账等所有基本功能。
1. [APP-SDK 使用文档](./doc/APP-SDK.md)

相关功能介绍：
1. SDK支持全币种，币威钱包支持的币种将会自动体现在SDK中。
2. SDK主要功能：转账和收款
3. 为了安全，资产标准超过3000元需要绑定谷歌验证
4. SDK的数据与币威钱包数据互通
5. 项目方在接入SDK时，遇到需要将一些数字币发放给用户的情况时候，需要先充值到企业钱包（币威生成的，项目方能调用接口，能查询）再用API接口写入
6. 手机号验证的用户可以在任何SDK中修改支付密码。
7. SDK登录有效期7天，如过期需要重新使用手机验证登录
8. 项目方只能通过接口查询该项目币种的数据，不能查询其他币种资产（防止多SDK数据透明）。

