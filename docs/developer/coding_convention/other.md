# Một số quy tắc khác

Dưới đây là một số các quy tắc khác, không được quy định cụ thể.

## 1. Phiên bản PHP

Nên sử dụng phiên bản PHP mới nhất, ít nhất là PHP version >= 5.4

## 2. Sử dụng `[]` thay thế cho `array()`

Với phiên bản PHP >= 5.4, hãy sử dụng `[]` để khai báo array, thay vì dùng `array()`

```php
// Good
$a = [];
$b = [
    $key => $value,
    $key2 => $value2,
];

// Bad
$a = array();
$b = array(
    $key => $value,
    $key2 => $value2,
);
```

## 3. Tên biến kế thừa

Tên biến bình thường được đặt tên dưới dạng `camelCase` tuy nhiên trong các trường hợp muốn phân biệt biến được kế thừa từ class parent chứ không phải sinh ra trực tiếp thì nên đặt dưới dạng `snake_case`.

```php
class AppController extends Controller
{
    public $var_in_super_class = 1;
}

class UsersController extends AppController
{
    // $var_in_super_class is not initialled in here
}

// File View/Users/index.ctp

<?php if ($var_in_super_class) : // But it uses in internal element like here ?>

```

## 4 Khai báo string

Sử dụng dấu `'` đối với một string bình thường. Chỉ dùng `"` khi bên trong có khai triển biến PHP.

```php
$normalString = 'A String';
$specialString = "This is {$normalString}";
```
