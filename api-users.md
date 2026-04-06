# 用户接口

## 获取当前用户信息

### <span class="badge-get">GET</span> `/v1/users/me`

返回当前已登录用户的基本信息。

**请求示例：**

```bash
curl -X GET https://api.example.com/v1/users/me \
  -H "Authorization: Bearer YOUR_TOKEN"
```

**响应示例：**

```json
{
  "code": 0,
  "message": "success",
  "data": {
    "id": "u_123456",
    "name": "张三",
    "email": "zhangsan@example.com",
    "avatar": "https://cdn.example.com/avatars/u_123456.png",
    "role": "admin",
    "created_at": "2025-01-01T00:00:00Z"
  }
}
```

---

## 获取用户详情

### <span class="badge-get">GET</span> `/v1/users/{id}`

**路径参数：**

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `id` | string | 是 | 用户 ID |

**响应：** 同上。

---

## 更新用户信息

### <span class="badge-put">PUT</span> `/v1/users/{id}`

**请求体：**

```json
{
  "name": "李四",
  "avatar": "https://cdn.example.com/avatars/new.png"
}
```

| 字段 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `name` | string | 否 | 用户昵称，最长 50 字符 |
| `avatar` | string | 否 | 头像 URL |

**响应示例：**

```json
{
  "code": 0,
  "message": "success",
  "data": {
    "id": "u_123456",
    "name": "李四",
    "email": "zhangsan@example.com",
    "avatar": "https://cdn.example.com/avatars/new.png",
    "role": "admin",
    "created_at": "2025-01-01T00:00:00Z"
  }
}
```

---

## 获取用户列表

### <span class="badge-get">GET</span> `/v1/users`

**查询参数：**

| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `page` | integer | 否 | `1` | 页码 |
| `per_page` | integer | 否 | `20` | 每页数量，最大 100 |
| `role` | string | 否 | - | 按角色筛选：`admin` / `user` |

**响应示例：**

```json
{
  "code": 0,
  "message": "success",
  "data": {
    "items": [
      {
        "id": "u_123456",
        "name": "张三",
        "email": "zhangsan@example.com",
        "role": "admin"
      }
    ],
    "total": 1,
    "page": 1,
    "per_page": 20
  }
}
```

---

## 删除用户

### <span class="badge-delete">DELETE</span> `/v1/users/{id}`

> 此操作不可逆，请谨慎调用。

**响应示例：**

```json
{
  "code": 0,
  "message": "success",
  "data": null
}
```
