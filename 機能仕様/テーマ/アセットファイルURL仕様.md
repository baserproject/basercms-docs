#アセットファイルURL仕様

##アセットファイルURL生成時の基本仕様

ヘルパーにおけるURL生成時、/app/webroot/ 配下以外のアセットファイルの配置が可能な箇所を走査して存在すればそのアセットファイルへのURLを生成する。  
存在しなければ、/app/webroot/ へのURLを生成する。


##アセットファイルの動的読込

/app/webroot/theme/ 以外の場所にアセットを配置したとしても、同じURLで参照できる。

（例）
下記２つはどちらも /theme/theme-name/css/style.css で参照できる。
```
/app/webroot/theme/theme-name/css/style.css
/app/View/Themed/ThemeName/webroot/css/style.css
```

##アセットファイルの配置パス

* /app/View/Themed/ にテーマを配置する場合  
	CakePHPの基本仕様として、/app/View/Themed/ 内に配置する場合は、アセットファイルの設置において webroot フォルダが必要となる。またテーマ名はキャメルケースとなる。  
	
	``` 
	（例）  
	/app/View/Themed/ThemeName/webroot/css/style.css`
	```
	
* /app/webroot/theme/ にテーマを配置する場合  
	アセットファイルの配置について webroot フォルダは不要となる。

	```
	（例）
	/app/webroot/theme/theme-name/css/style.css
	```

##アセットファイル配置可能箇所

* /app/webroot/
* /app/webroot/theme/theme-name/
* /app/View/webroot/（baser独自仕様）
* /app/View/Themed/ThemeName/webroot/
* /lib/Baser/View/webroot/（baser独自仕様）
* /lib/Baser/View/Themed/ThemeName/webroot/（baser独自仕様）




