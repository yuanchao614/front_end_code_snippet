- 关于使用express构建后端接口时，`post`接口`req.body`无法获取参数问题,需要引入`body-parser`模块解析`body`参数。

参考地址： [http://nodejs.cn/learn/get-http-request-body-data-using-nodejs](http://nodejs.cn/learn/get-http-request-body-data-using-nodejs)

```js
const bodyParser = require('body-parser')

app.use(
  bodyParser.urlencoded({
    extended: true
  })
)

app.use(bodyParser.json())

app.post('/todos', (req, res) => {
  console.log(req.body.todo)
})
```
