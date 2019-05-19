#### 1. 安装`JSON Server`
```bash
npm install -g cnpm --registry=https://registry.npm.taobao.org
cnpm install -g json-server
```

#### 2. 创建`json`数据文件`db.json`
```json
{
  "posts": [
    { "id": 1, "title": "json-server", "author": "typicode" }
  ],
  "comments": [
    { "id": 1, "body": "some comment", "postId": 1 }
  ],
  "profile": { "name": "typicode" }
}
```
#### 3. 启动`JSON Server`
```
➜  ~ json-server --watch db.json

  \{^_^}/ hi!

  Loading db.json
  Done

  Resources
  http://localhost:3000/posts
  http://localhost:3000/comments
  http://localhost:3000/profile

  Home
  http://localhost:3000

  Type s + enter at any time to create a snapshot of the database
  Watching...
```
#### 请求
```
➜  ~ curl http://localhost:3000/posts/1
{
  "id": 1,
  "title": "json-server",
  "author": "typicode"
}

➜  ~ node
> var aa = {
...   "id": 2,
...   "title": "json api",
...   "author": "fangfang"
... }
> JSON.stringify(aa)
'{"id":2,"title":"json api","author":"fangfang"}'

➜  ~ curl -X POST -H 'Content-type':'application/json' -d '{"id":2,"title":"json api","author":"fangfang"}' http://localhost:3000/posts
{
  "id": 2,
  "title": "json api",
  "author": "fangfang"
}
```
