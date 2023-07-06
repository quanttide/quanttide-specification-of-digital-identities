# 设备模型

- 设备唯一标识
- 设备标签
- 关联用户

## 设备唯一性

- Android、iOS、Win、Mac等客户端通过设备ID来识别。
- Web通过（设备ID和）浏览器ID识别。
- 小米照明弹机制，如果对同一个APP发固定ID，则直接使用即可。
- 无标记的设备发临时ID/半永久ID，客户端只要不被删配置文件就可用，Web只要不被清缓存就可以用。

具体还要根据各个设备的ID机制和缓存持久化的机制决定，需要深入研究设计和反复测试，设计时需要为异常情况设计一个通用的处理机制。

设备唯一性识别可以参考：https://cloud.tencent.com/developer/article/1475342

## 设备枚举类型

- 操作系统设备标签，包括Android、iOS、Windows、Mac、Linux等。
- 框架和自定义设备标签，包括Flutter、小程序、Web、Native等。

### 操作系统标签

可以通过解析UA获取，Python有相关库可以处理。

- 操作系统：iOS，Android，macOS，Windows
- 设备类型：Mobile，Tablet，Desktop
- 渲染类型：Native，Web（浏览器）

### 框架标签

- Flutter类型：iOS，Android，Web，macOS，Windows
- 微信类型：native，APP，H5，etc
- 自定义类型（QtDeviceLabel）：根据内部系统需求定义。

## 设备匹配用户

这是一个many-to-many模型，一个设备可能登陆多个用户，一个用户可能登陆多个设备。
用此表可以采集我们想要的用户数据，用以**数据分析->迭代安全算法**。
