# 重定向

将请求从一个 URL 重定向到另一个 URL，或从一组 URL 重定向到另一组。

## 将所有请求重定向到一个 URL

```javascript
const destinationURL = 'https://example.com';
const statusCode = 301;

async function handleRequest(request) {
  return Response.redirect(destinationURL, statusCode);
}

addEventListener('fetch', async event => {
  event.respondWith(handleRequest(event.request));
});
```

## 将请求从一个域名重定向到另一个域名

```javascript
const base = 'https://example.com';
const statusCode = 301;

async function handleRequest(request) {
  const url = new URL(request.url);
  const { pathname, search } = url;

  const destinationURL = base + pathname + search;

  return Response.redirect(destinationURL, statusCode);
}

addEventListener('fetch', async event => {
  event.respondWith(handleRequest(event.request));
});
```
