# 返回JSON

直接从 Worker 脚本返回 JSON，对于构建 API 和中间件很有用。

```javascript
addEventListener('fetch', event => {
  const data = {
    hello: 'world',
  };

  const json = JSON.stringify(data, null, 2);

  return event.respondWith(
    new Response(json, {
      headers: {
        'content-type': 'application/json;charset=UTF-8',
      },
    })
  );
});
```