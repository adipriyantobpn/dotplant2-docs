#Виджет автокомплит.
Виджет автокомплита используется для автоматической подсказки результатов в форме поиска по сайту. В момент набора запроса в поле для ввода он подгружает подходящие  результаты  и выводит их в виде списка под полем ввода. 
Если среди них есть подходящий результат, можно кликнуть по нему и будет осуществлен переход на соответствующую страницу сайта.

###Минимальный вызов виджета может выглядеть следующим образом:
```php
<?php
$search = new \app\models\Search;
$search->load(Yii::$app->request->get());
$form = \kartik\widgets\ActiveForm::begin(
   [
       'action' => ['/search'],
       'method' => 'get',
       'id' => formid,
   ]
);

echo \app\widgets\AutoCompleteSearch::widget(
   [
       'model' => $search,
       'attribute' => 'q',
   ]
);
\kartik\widgets\ActiveForm::end();
?>
```
Он вызывается внутри виджета формы и генерирует поле ввода `input type=”text”.`
На вход принимает основные параметры :
- `model` => модель поиска,
- `attribute => q`, имя параметра запроса.

Дополнительные параметры:
- `clientOptions` - массив опций http://api.jqueryui.com/autocomplete/ 
- `listClass` - css класс для оформления списка результатов в подсказке
- `route` - маршрут до действия автокомплита, по умолчанию  `'/default/auto-complete-search’`