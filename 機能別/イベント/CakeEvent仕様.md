
#CakeEvent仕様

* EventDispacher  
	イベントを発動する仕組み
* EventListener  
	イベントを登録する仕組み
* EventManager  
	イベントを管理するクラス
* EventAttach  
	EventMangerにEventListenerに登録する仕組み
* イベント名命名規則（EventNamingRule）  
	Layer.Class.eventName（推奨）
	
	```
	（例）  
	Controller.beforeRender
	Controller.Pages.beforeRender
	```
	
* イベントハンドラで参照できるデータ
 * $event->data		各イベントごとに定義されているデータ
 * $event->subject	呼び出し元のクラスのインスタンス

##コード例

* イベントの発火

	```php
	$this->getEventManager()->dispatch(new 	CakeEvent('Controller.Users.afterEdit', $this, array(
		'user' => $this->request->data
	)));
	```
* イベントの登録

	```php
	App::uses('CustomComponent', 'Controller/Component');
	CakeEventManager::instance()->attach(new CustomComponent());
	```

* イベントリスナークラスの定義

	```php
	App::uses('CakeEventListener', 'Event');
	class CustomComponent implements CakeEventListener {

		public function implementedEvents() {
			return array(
				'Controller.Users.afterEdit' => array(
					'callable'          => 'afterEdit'
				),
				'Controller.initialize'     => array(
					'callable'          => 'test'
				)
			);
		}

		public function afterEdit($event) {
			var_dump($event->data);
			exit();
		}

		public function test() {
			echo 'aaaaaaaaaa';
		}

	}
	```