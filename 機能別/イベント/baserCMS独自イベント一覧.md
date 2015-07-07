#baserCMS独自イベント一覧

##コントローラー
* {CakePHP標準イベント名}（例：beforeRender）  
* {ControllerName}.{CakePHP標準イベント名}（例：Users.beforeRender）  
* Mail.Mail.beforeSendEmail（メール送信直前）  
* Mail.Mail.afterSendEmail（メール送信直後）  
* Blog.BlogPosts.afterAdd （ブログ記事追加直後）  
* Blog.BlogPosts.afterEdit（ブログ記事編集直後）  
* Users.afterAdd（新規ユーザ追加直後）  
* Users.afterEdit（既存ユーザ編集直後）  
* Pages.afterAdd（新規ページ追加直後）  
* Pages.afterEdit（既存ページ編集直後）  

##ビュー
* {CakePHPの標準イベント名}（例：beforeLayout）  
* {ControllerName}.{CakePHPの標準イベント名}（例：Users.beforeLayout）  
* beforeElement（エレメント生成直前）  
* afterElement（エレメント生成直後）  
* {ControllerName}.beforeElement（エレメント生成直前）  
* {ControllerName}.afterElement（エレメント生成直後）  
* header（ヘッダーエレメント生成直後）  
* footer（フッターエレメント生成直後）
* {ControllerName}.header（ヘッダーエレメント生成直後）
* {ControllerName}.footer（フッターエレメント生成直後）

##モデル
* {CakePHP標準イベント名}（例：beforeFind）
* {ModelName}.{CakePHP標準イベント名}（例：User.beforeFind）

##ヘルパー
* Html.beforeGetLink（リンク取得直前）
* Html.afterGetLink（リンク取得直後）
* Form.beforeCreate（フォーム開始タグ生成直前）
* Form.afterCreate（フォーム開始タグ生成直後）
* Form.beforeEnd（フォーム終了タグ生成直前）
* Form.afterEnd（フォーム終了タグ生成直後）
* Form.beforeInput（フォームパーツタグ生成直前）
* Form.afterInput（フォームパーツタグ生成直後）
