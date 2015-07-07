#BaserEvent仕様

##基本仕様

* CakePHP標準のイベントの仕組（CakeEvent）は、インターフェイスの定義が必要だったりと、複雑な仕組みの為、baserCMS側でラッピングし簡単にイベントの登録ができるようにした。  
	※ CakeEvent仕様を参照
* MVCHごとに決まったクラスを継承したクラスを /PluginName/Event/ フォルダに作成する事で、自動的にイベント登録を行う事ができる。

##イベントクラスの作成
* クラスファイルは、/PluginName/Event/ ディレクトリ配下に作成する。
* クラス名の命名規則は次のとおりとする。  
	* コントローラー・・・PluginNameControllerEventListener（BcControllerEventListenerを継承）  
	* モデル・・・PluginNameModelEventListener（BcModelEventListenerを継承）  
	* ビュー・・・PluginNameViewEventListener（BcViewEventListenerを継承）  
	* ヘルパ・・・PluginNameHelperEventListener（BcHelperEventListenerを継承）

##イベントの登録

* events プロパティに、イベント名を登録する  
	※ 登録できるイベントは、baserCMS独自イベント一覧を参照  
	※ プラグインのイベントを登録する場合は、Plugin.Class.eventName となる。
* コールバックメソッドは、イベント名から「.」を除外してキャメライズした名称で定義する  

		（例）
		User.beforeFind → userBeforeFind
		Uploader.UploaderFile.beforeFind → uploaderUploaderFileBeforeFind

##コールバックメソッド内でのデータの参照

* イベント固有のデータは、$event->data で参照
* イベントの発火元は、$event->subject で参照

##コード例

SampleControllerEvent.php

```php
class SampleControllerEvent extends BcControllerEventListener {

	public $events = array(
		'Users.beforeRender',
		'Users.afterEdit',
		'initialize'
	);

	public function usersBeforeRender(CakeEvent $event) {
		// ビューにサンプルという文字列を引き渡す
		$Controller = $event->subject();
		$Controller->set('sample', 'sample');
	}

	public function usersAfterEdit(CakeEvent $event) {
		// ユーザー情報変更後のデータを参照
		var_dump($event->data);
	}

	public function initialize(CakeEvent $event) {
		// サンプルヘルパーをコントローラーに追加
		$Controller = $event->subject();
		$Controller->helpers[] = 'Sample';
	}
}
```
