# BaserAjaxDataList削除処理

## 行削除
## 削除メッセージの指定方法

```
$.baserAjaxDataList.config.methods.del.confirm = '{メッセージ内容}';
```

## 削除処理の実装
admin_ajax_delete メソッドを実装する

最後は exit() で終わる  
成功処理は exit(true)


## 一括削除の実装
_batch_del メソッドを実装する  
$ids をループでまわして削除処理を行う  
boolean を返却