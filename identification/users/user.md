# 用户身份

用户身份（`User`）领域模型是主要的领域模型，用于描述用户的基本信息和状态。
该模型包括[匿名用户](anonymous.md)、[注册用户](registered.md)和[注销用户](deactivated.md)三种类型。

## 匿名用户

匿名用户（`AnonymousUser`）是指尚未进行身份验证或注册的用户。匿名用户的访问权限通常受到限制，并且不能访问或执行某些操作。匿名用户的特征如下：

- 没有用户名、密码或其他身份验证凭证。
- 可以进行一些有限的操作，例如查看公共内容或提交反馈信息。
- 不能访问或使用受限资源。

字段定义如下：

- `id`: ID，UUID格式。匿名用户的唯一标识符。
- `created_at`: 创建时间，ISO-8601日期格式。匿名用户创建的时间戳。
- `updated_at`: 更新时间，ISO-8601日期格式。匿名用户更新的时间戳。

## 注册用户

注册用户（`RegisteredUser`）是指已经注册并登录的用户。注册用户通常有更高的访问权限，并且可以访问或执行更多的操作。注册用户的特征如下：

- 有一个或多个身份验证凭证，例如用户名和密码、电子邮件地址和密码、或第三方身份验证提供商的身份验证令牌。
- 可以访问和使用更多的资源和功能，例如个人资料、私人消息、购物车等。
- 可以管理个人设置和偏好，例如语言、时区、通知频率等。

字段定义如下：

- `id`: ID，UUID格式。注册用户的唯一标识符。
- `username`: 用户名，字符型。注册用户用于登录系统的用户名。
- `email`: 电子邮件地址，字符型，电子邮件格式。注册用户的电子邮件地址。
- `password`: 密码，字符型。注册用户的登录密码，通常会进行加密或散列处理。
- `created_at`: 创建时间，字符型，ISO-8601日期格式。注册用户创建的时间戳。
- `updated_at`: 更新时间，字符型，ISO-8601日期格式。注册用户更新的时间戳。


## 注销用户

注销用户（`DeactivatedUser`）是指已经注销或被禁止的用户，不能再访问或使用系统中的任何资源或功能。注销用户的特征如下：

- 不能再访问或使用系统中的任何资源或功能。
- 个人信息和数据可能会被删除或匿名化，或者被保留以满足法律或合规要求。

字段定义如下：

- `id`: ID，UUID格式。注销用户的唯一标识符。
- `username`: 用户名，字符型。注销用户曾经使用的用户名。
- `email`: 电子邮件地址，字符型。注销用户曾经使用的电子邮件地址。
- `deleted_at`: 删除时间，ISO-8601日期格式。注销用户账户的删除时间戳。

注销用户模型用于描述已经被禁止或注销的用户的特征和行为，包括其唯一标识符、曾经使用的用户名和电子邮件地址以及账户删除时间戳。在实际应用中，可以根据具体需求和场景来扩展和修改该模型，以满足不同的业务需求和安全要求。
