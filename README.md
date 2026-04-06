# My API Docs

欢迎使用 My API。本文档提供完整的接口说明、请求示例和错误处理指南。

## 概览

| 项目 | 说明 |
|------|------|
| Base URL | `https://api.example.com/v1` |
| 协议 | HTTPS |
| 数据格式 | JSON |
| 字符编码 | UTF-8 |

## 请求规范

所有请求均需在 Header 中携带认证信息：

```
Authorization: Bearer <your_token>
Content-Type: application/json
```

## 响应结构

所有接口统一返回以下结构：

```json
{
  "code": 0,
  "message": "success",
  "data": { }
}
```

| 字段 | 类型 | 说明 |
|------|------|------|
| `code` | integer | `0` 表示成功，非零为错误码 |
| `message` | string | 结果描述 |
| `data` | object / array | 业务数据 |

## 快速导航

- [快速开始](docs/quickstart.md) — 5 分钟接入指南
- [认证方式](docs/auth.md) — Token 获取与使用
- [用户接口](docs/api-users.md) — 用户注册、登录、信息管理
- [资源接口](docs/api-resources.md) — 资源的增删改查
- [错误码](docs/errors.md) — 完整错误码列表
