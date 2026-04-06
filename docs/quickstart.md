# 快速开始

## 1. 获取 API Token

注册账号后，在控制台 **设置 → API 密钥** 页面生成 Token。

## 2. 发起第一个请求

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
    "created_at": "2025-01-01T00:00:00Z"
  }
}
```

## 3. SDK 安装（可选）

```bash
# Node.js
npm install @example/api-sdk

# Python
pip install example-api-sdk
```

```js
import { ApiClient } from '@example/api-sdk'

const client = new ApiClient({ token: 'YOUR_TOKEN' })
const user = await client.users.me()
```

## 常见问题

**Q: Token 有效期多长？**  
默认 30 天，可在控制台手动刷新或设置自动续期。

**Q: 请求频率有限制吗？**  
默认每分钟 60 次，企业版可申请提升上限。
