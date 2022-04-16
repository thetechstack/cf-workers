# 返回另一个站点的响应

使用来自另一个网站（本例中为 example.com）的响应来响应 Worker 请求。

```javascript
addEventListener('fetch', function (event) {
  event.respondWith(handleRequest(event.request));
});
async function handleRequest(request) {
  // Only GET requests work with this proxy.
  if (request.method !== 'GET') return MethodNotAllowed(request);
  return fetch(`https://example.com`);
}
function MethodNotAllowed(request) {
  return new Response(`Method ${request.method} not allowed.`, {
    status: 405,
    headers: {
      Allow: 'GET',
    },
  });
}
```
