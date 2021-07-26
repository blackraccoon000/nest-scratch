# NestJS で Route 情報を追加するには、

```js
@Controller()
export class AppController {
  @Get('/asa')
  getRootRoute() {
    return 'hi there!'
  }
}
```

localhost:3000 アクセス
{"statusCode":404,"message":"Cannot GET /","error":"Not Found"}

http://localhost:3000/asa
hi there!

```js
@Controller('/app')
export class AppController {
  @Get('/asa')
  getRootRoute() {
    return 'hi there!'
  }
}
```

http://localhost:3000/app/asa
