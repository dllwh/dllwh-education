> 本文档主要描述直播平台的需求，明确项目需求范围，作为项目相关干系人的沟通基准，确保使各项目干系人能够清楚的了解各方的责任，作为需求评审以及后续开发、维护的依据。


# 在线教育系统

&emsp;&emsp;搭建在线互动教育直播平台，平台入驻教师利用手机、PC端或者其他设备均可进行直播，在线即可收看直播/录播，在线约课，在线即可互动交流、共享讲义，部分直播收费可观看。用直播打造线上教育互动教学、答疑等，形成在线教育行业发展新机遇。平台突破传统远程教育模式，为各行各业有识之士提供了传播知识、分享经验的舞台，令广大学员享受到更丰富、更精准、更实用的教学资源，实现知识经济新时代的教学资源共建、共享、共赢。


## 项目介绍

&emsp;&emsp;xxxx直播平台，是专门为在线教育视频直播业务提供的一个产品。主要特点是：

- 丰富而优质的教学资源
    - 不同人群：专家、教授、学者、名师、达人、大众，既有学术理论，又含实用技能；
    - 不同类型：视频课件、直播课程、文档资料、动画图文，各种表现形态，丰富学习感受
- 独特便捷的授课系统
    - 智能稳定的直播教学系统，为网络课程带来面授般的体验，学员仿佛置身于真实教室，面对面互动学习；具有多种授课模式、即时语音交互，强大的网络环境适应性，全面兼容主流网络终端设备等特点
- 专业的教学配套功能
    - 精心设计了学习笔记、课程标签、学习记录、在线答疑等一系列配套功能，轻松实现随学随记、随记随练、随练随问，全面提升学习体验和效果。
- 丰富的聊天消息类型和消息进阶功能
    - 支持消息类型包括文字、语音、图片等内置消息类型和可实现点赞等功能的自定义消息类型；
    - 支持内容安全管理，包括敏感词设置，聊天内容反垃圾处理等；
    - 支持服务端发送聊天消息，可以实现聊天通知等场景；
- 便捷细致的聊天管理功能
    - 支持聊天用户管理功能，包括加入、禁言、查询、封禁（踢人）等；
    - 支持聊天室实时消息数据统计；
- 文档直播
    - 支持播放直播的同时进行文档直播，文档可由后台进行上传，支持多种格式（Word/Excel/PPT/PDF）播放直播的同时进行文档直播，使直播内容“言之有物”，培训/宣传效果更佳！

## 项目组织架构

|项目编号  |模块 | 说明 |
|--- | --- | --- 
|dllwh-education-auth        |服务鉴权	 |基于SpringSecurity进行安全认证，采用OAuth2.0认证体系，<br/>对客户端、用户进行认证及授权，支持账号密码登录，短信验证码登录
|dllwh-education-config      |配置服务 	 |基于Spring Cloud构建统一配置服务，负责管理所有服务的配置文件 
|dllwh-education-devTools    |开发工具 	 |
|dllwh-education-gateway     |网关服务 	 |构建服务网关
|dllwh-education-monitor     |监控服务	 |对应用状态进行监控，对服务调用进行追踪
|dllwh-education-registry    |服务注册 	 |基于Euraka构建服务注册中心，负责服务注册于发现
|dllwh-education-ops         |运维中心 	 |
|dllwh-education-oms         |管理系统	 |
|dllwh-education-crawler     |爬虫程序          |
|dllwh-education-pay         |聚合支付	 |主要实现支持微信，支付宝等方式
|dllwh-education-common  |基础服务 	 |
|dllwh-education-service     |业务模块	 |
|dllwh-education-service-api |业务模块API |
|dllwh-education-business-message |消息中心 	 |公共基础通知服务<br/>&emsp;支持系统消息、短信、邮件、推送通知
|dllwh-education-business-upms 	  |权限中心 	 |提供角色、资源、授权服务
|dllwh-education-business-uc 	  |用户服务 	 |用户中心
|dllwh-education-business-notice  |通知中心	 |基于RabbitMQ异步通知发送短信、邮件、WebSocket消息
|dllwh-education-business-teacher |讲师管理 	 |基本信息、课程信息以及佣金等
|dllwh-education-business-course  |课程管理	 |讲师管理自有课程，后台具有审核功能
|dllwh-education-businese-sysLog  |日志管理 	 |
|dllwh-education-businese-sysDict |数据字典 	 |
|dllwh-education-businese-media	  |音视频媒体 	 |

## 技术框架

### 功能介绍

#### 前端基础功能

- [ ] 在线视频直播 SDK，由两部分构成
    - [ ] 主播端
        - 讲师端使用的是推流SDK，主播需要把摄像头采集的视频源做编码，然后推到视频直播云上
    - [ ] 观众端
        - 观众端使用的是拉流SDK，观众需要的是把视频从服务端拉倒本地做解码，并展示到手机、PC等终端上,观众端还必须包括一个视频播放器。

#### 直播系统基础功能

- [ ] 直播系统基础功能
    - [ ] 多终端互通
        - PC、Android、iOS多终端的互通直播必不可少，同时需要支持手机、WEB、微信、H5多屏进行观看
    - [ ] 直播分享
        - 直播内容可分享到QQ、微信、朋友圈、QQ空间等多个渠道，为在线课堂吸引更多的学员，增加直播间氛围。
    - [ ] 高清流畅
        - 全网加速，直播视频高清流畅无卡顿
    - [ ] 多屏同步
        - 支持ios/android手机直播及PC三端观看
    - [ ] 独立平台
        - 可单独搭建直播平台或支持现有APP内嵌
    - [ ] 多模式注册/登录
        - 支持微信、微博、QQ、短信等多模式注册及登录
    - [ ] 互动连麦
        - 直播间连麦，支持多路语音同时对话，连麦功能可应用于在线教育课堂的问题讨论，让学员和老师仿佛置身于现实的课堂讨论中。
    - [ ] 聊天互动
        - 支持弹幕评论、点赞、答题、公共、签到等众多互动功能
    - [ ] 美颜特效
        - 支持美颜、瘦脸、磨皮等，提升视觉观看体验
    - [ ] 弹幕功能
        - 用户任性发送弹慕，想说就说
    - [ ] 录播回看
        - 支持视频存储、回放或点播，精彩内容不错过。对于错过课程直播的观众，可以通过录播回看课程内容，同时也可以反复观看，循环学习，对于疑难问题可多次学习。
    - [ ] 自动鉴黄
        - 自动识别视频图像，大幅降低人工审核成本
- [ ] 点播(回放、录播)
- [ ] 直播监控
    - [ ] 直播录制
    - [ ] 直播流截图
    - [ ] 直播视频流状态通知
        - 视频流是否播放
        - 视频是否推流、断流
- [ ] 直播数据统计
    - 直播在线人数
    - 观看人数、次数、时长、地点等数据
    - 有效分享
