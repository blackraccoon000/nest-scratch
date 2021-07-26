# ファイルの命名規則

main.ts
-> class AppController
-> class AppModule
-> function bootstrap

アプリコントローラとアプリモジュールを独自のファイルに抽出します。

One class per file (some exceptions)
Class names should include the kind of thing we are creating
Name of class and name of file should always match up
Filename template: name.type_of_thing.ts

1 ファイルに 1 クラス（一部例外あり
クラス名には、どのようなものを作っているのかを含めること
クラス名とファイル名は必ず一致させる
ファイル名のテンプレート：name.type_of_thing.ts

### e.g.

app.controller.ts -> class AppController{}
app.module.ts -> class AppModule {}
