ts-node 関連で tsconfig.json で設定した baseUrl が効かない。

```
❯ npx ts-node-dev src/main.ts
[INFO] 11:15:34 ts-node-dev ver. 1.1.8 (using ts-node ver. 9.1.1, typescript ver. 4.3.5)
Error: Cannot find module 'app.module'
Require stack:
- /Users/yutakaf/Desktop/git/nest-scratch/src/main.ts
    at Function.Module._resolveFilename (internal/modules/cjs/loader.js:885:15)
    at Function.Module._load (internal/modules/cjs/loader.js:730:27)
    at Module.require (internal/modules/cjs/loader.js:957:19)
    at require (internal/modules/cjs/helpers.js:88:18)
    at Object.<anonymous> (/Users/yutakaf/Desktop/git/nest-scratch/src/main.ts:3:1)
    at Module._compile (internal/modules/cjs/loader.js:1068:30)
    at Module._compile (/Users/yutakaf/.npm/_npx/2351b2a15f5189cb/node_modules/source-map-support/source-map-support.js:547:25)
    at Module.m._compile (/private/var/folders/q7/68tj8lvj495f2r1rmkkdbn1w0000gn/T/ts-node-dev-hook-833656002356397.js:69:33)
    at Module._extensions..js (internal/modules/cjs/loader.js:1097:10)
    at require.extensions.<computed> (/private/var/folders/q7/68tj8lvj495f2r1rmkkdbn1w0000gn/T/ts-node-dev-hook-833656002356397.js:71:20)
[ERROR] 11:15:39 Error: Cannot find module 'app.module'
Require stack:
- /Users/yutakaf/Desktop/git/nest-scratch/src/main.ts
```

typescript は path 解決はサポート外であるとのこと。

https://github.com/TypeStrong/ts-node/issues/138#issuecomment-349222070

https://www.npmjs.com/package/tsconfig-paths

Configuration Options
You can set options by passing them before the script path, via programmatic usage or via environment variables.

ts-node --project customLocation/tsconfig.json -r tsconfig-paths/register "test/\*_/_.ts"

`npx ts-node-dev -r tsconfig-paths/register src/main.ts`

```
❯ npx ts-node-dev -r tsconfig-paths/register src/main.ts
[INFO] 11:23:52 ts-node-dev ver. 1.1.8 (using ts-node ver. 9.1.1, typescript ver. 4.3.5)
[Nest] 47049   - 2021/07/26 11:24:00   [NestFactory] Starting Nest application...
[Nest] 47049   - 2021/07/26 11:24:01   [InstanceLoader] AppModule dependencies initialized +663ms
[Nest] 47049   - 2021/07/26 11:24:01   [RoutesResolver] AppController {}: +40ms
[Nest] 47049   - 2021/07/26 11:24:01   [RouterExplorer] Mapped {, GET} route +6ms
[Nest] 47049   - 2021/07/26 11:24:01   [NestApplication] Nest application successfully started +3ms
```

動作するようになった。

参考
https://tech-blog.tkcco21.me/blog/resolve_paths_with_ts-node/
