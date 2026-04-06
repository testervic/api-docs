# 认证方式

所有 API 请求均需通过认证。目前支持 **Bearer Token** 认证。

## 获取 Token

### <span class="badge-post">POST</span> `/v1/auth/token`

使用账号密码换取访问 Token。

**请求体：**

```json
{
  "email": "user@example.com",
  "password": "your_password"
}
```

**响应示例：**

```json
{
  "code": 0,
  "message": "success",
  "data": {
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "token_type": "Bearer",
    "expires_in": 2592000
  }
}
```

| 字段 | 类型 | 说明 |
|------|------|------|
| `access_token` | string | 访问令牌 |
| `token_type` | string | 固定为 `Bearer` |
| `expires_in` | integer | 有效期（秒），默认 30 天 |

## 使用 Token

在所有 API 请求的 Header 中携带：

```
Authorization: Bearer <access_token>
```

## 刷新 Token

### <span class="badge-post">POST</span> `/v1/auth/refresh`

Token 过期前可调用此接口续期，无需重新登录。

**请求体：**

```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

**响应：** 同获取 Token 接口。

## 吊销 Token

### <span class="badge-delete">DELETE</span> `/v1/auth/token`

主动登出，使当前 Token 立即失效。

**响应示例：**

```json
{
  "code": 0,
  "message": "success",
  "data": null
}
```
