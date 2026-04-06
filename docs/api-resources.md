# 资源接口

## 创建资源

### <span class="badge-post">POST</span> `/v1/resources`

**请求体：**

```json
{
  "name": "我的资源",
  "type": "document",
  "content": "资源内容...",
  "tags": ["标签1", "标签2"],
  "public": false
}
```

| 字段 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `name` | string | 是 | 资源名称，最长 100 字符 |
| `type` | string | 是 | 类型：`document` / `image` / `file` |
| `content` | string | 否 | 文本内容（`document` 类型适用） |
| `tags` | array | 否 | 标签列表 |
| `public` | boolean | 否 | 是否公开，默认 `false` |

**响应示例：**

```json
{
  "code": 0,
  "message": "success",
  "data": {
    "id": "r_abcdef",
    "name": "我的资源",
    "type": "document",
    "tags": ["标签1", "标签2"],
    "public": false,
    "owner_id": "u_123456",
    "created_at": "2025-06-01T10:00:00Z",
    "updated_at": "2025-06-01T10:00:00Z"
  }
}
```

---

## 获取资源详情

### <span class="badge-get">GET</span> `/v1/resources/{id}`

**路径参数：**

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `id` | string | 是 | 资源 ID |

---

## 更新资源

### <span class="badge-patch">PATCH</span> `/v1/resources/{id}`

仅传入需要修改的字段。

**请求体：**

```json
{
  "name": "新名称",
  "public": true
}
```

---

## 获取资源列表

### <span class="badge-get">GET</span> `/v1/resources`

**查询参数：**

| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `page` | integer | 否 | `1` | 页码 |
| `per_page` | integer | 否 | `20` | 每页数量 |
| `type` | string | 否 | - | 按类型筛选 |
| `tag` | string | 否 | - | 按标签筛选 |
| `keyword` | string | 否 | - | 按名称关键词搜索 |

**响应示例：**

```json
{
  "code": 0,
  "message": "success",
  "data": {
    "items": [
      {
        "id": "r_abcdef",
        "name": "我的资源",
        "type": "document",
        "tags": ["标签1"],
        "public": false,
        "created_at": "2025-06-01T10:00:00Z"
      }
    ],
    "total": 1,
    "page": 1,
    "per_page": 20
  }
}
```

---

## 删除资源

### <span class="badge-delete">DELETE</span> `/v1/resources/{id}`

**响应示例：**

```json
{
  "code": 0,
  "message": "success",
  "data": null
}
```
