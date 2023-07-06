# 用户鉴权状态

本部分主要用以协调作为生产者的用户服务和作为消费者的各个服务和应用（通过语言和框架级插件）的鉴权用户模型的设计。

具体来说，是统一用户服务的`qtuser.models.User`、Django用户认证的`django_remote_auth.models.AuthUser`、Flutter用户组件库的`qtuser/auth.dart`的`AuthUser`这几个类，让他们在用户认证相关字段保持一致的设计逻辑。

认证相关字段包括：

- `is_anonymous`: 匿名用户标识。
- `is_active`: 激活用户标识。
- `is_authenticated`: 认证用户标识。
- `is_staff`: 员工用户标识。

基于以上认证字段，我们定义如下认证用户类型。

## 匿名用户

`is_anonymous=True`。

根据Django标准，此时其他所有字段都为`False`，即匿名用户等同于未认证用户。

## 激活用户

`is_active=True`。

此时`is_anonymous=False`，否则系统异常。

默认设置`True`。通过反作弊算法控制设置为`False`，以实现相关账户安全或系统安全逻辑。通过管理后台设置`True`和`False`转换，以实现解封流程；在有相应运营规范的情况下，其他必要的业务逻辑也可授权使用此特性。

## 认证用户

`is_authenticated=True`。

此时`is_active=True`，`is_anonymous=False`，否则系统异常。

符合Django和DRF标准的认证用户，参考官方标准实现即可。

## 员工用户

`is_staff=True`。

此时`is_active=True`，`is_authenticated=True`，`is_anonymous=False`，否则系统异常。

符合Django和DRF的员工用户，参考官方标准实现，并根据企业微信需要的业务逻辑拓展。

## 系统管理员

`is_admin=True`。

此时`is_active=True`，`is_authenticated=True`，`is_anonymous=False`，`is_staff=True`，否则系统异常。

符合Django和DRF的系统管理员用户，参考官方标准实现，并且根据系统初始化需要定制。

**请谨慎授权。**
