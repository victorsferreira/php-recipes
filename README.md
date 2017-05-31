# php-recipes

Call a method by reference

```php
$functions = ['foo'=>function($var){ echo $var; }];
call_user_func_array($functions[foo],$arguments);
```

call a method by it's name in the given object

```php
call_user_func_array(array(self::$object,$name),$arguments);
```

`array($object,$method_name)` creates a reference.

`call_user_func_array` receives a reference to a callable in the first parameter.

To change the context of a called method, for example, to allow it to use the attributes of a different object.

```php
$reflection = new \ReflectionClass(get_class($this->object));
$closure = $reflection->getMethod($name)->getClosure($this->object);
$closure = $closure->bindTo($this);
call_user_func_array($closure,$arguments);
```

`$this` is the current context and we want to change it to `object` context.

Enabling CORS

```php
 header("Access-Control-Allow-Origin: *");
```

Reading form payload as JSON

```php
$json = file_get_contents('php://input');
$obj = json_decode($json, TRUE);
```
