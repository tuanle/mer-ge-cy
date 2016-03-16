# CakePHP Coding Convention

Bộ quy tắc này được quy ước riêng cho các dự án sử dụng CakePHP Framework.

[Tài liệu gốc](http://book.cakephp.org/2.0/en/contributing/cakephp-coding-conventions.html)


## 1. Khái quát chung

- Code phải tuân theo [PSR-1](psr-1-convention) và [PSR-2](psr-2-convention)

- Tên variable đặt dưới dạng `camelCase`

- Việc đặt tên method, variable có thêm dấu gạch dưới `_` để phân biệt tính visibility của method, variable

- Các tag nên sử dụng trong DocBlocks

- Tên file trong trường hợp không chứa class

## 2. Tên biến

Tên biến được đặt dưới dạng `camelCase` và phải là cụm từ có ý nghĩa

## 3. Phân biệt tính visibility

Các **public** method, variable đặt tên bình thường

```php
<?php
class Foo extends Bar
{
    public $publicVar;

    public function publicFunction()
    {
    }
}
```

Các **protected** method, variable có tên bắt đầu bằng một dấu gạch dưới `_`

```php
<?php
class Foo extends Bar
{
    protected $_protectedVar;

    protected function _protectedFunction()
    {
    }
}
```

Các **private** method, variable có tên bắt đầu bằng hai dấu gạch dưới `_`

```php
<?php
class Foo extends Bar
{
    private $__privateVar;

    private function __privateFunction()
    {
    }
}
```

## 4. Các tag sử dụng trong DocBlocks

DocBLocks của class, method, property may nên chứa các tag theo tài liệu của [phpDocumentor](http://phpdoc.org/docs/latest/index.html)

- [@version](http://phpdoc.org/docs/latest/references/phpdoc/tags/version.html): Version hiện tại.

- [@deprecated](http://phpdoc.org/docs/latest/references/phpdoc/tags/deprecated.html): Cho biết các thành phần nằm trong kế hoạch lược bỏ ở các version tiếp theo.

- [@internal](http://phpdoc.org/docs/latest/references/phpdoc/tags/internal.html): Chỉ ra các yếu tố liên kết nội bộ như là các thư viện, các đoạn mã hoặc là các tài liệu chỉ dẫn cho người phát triển.

- [@link](http://phpdoc.org/docs/latest/references/phpdoc/tags/link.html): Chỉ ra các địa chỉ web liên kết.

- [@param](http://phpdoc.org/docs/latest/references/phpdoc/tags/param.html): Các tham số đầu vào

- [@return](http://phpdoc.org/docs/latest/references/phpdoc/tags/return.html): Các giá trị trả về, đầu ra

- [@throws](http://phpdoc.org/docs/latest/references/phpdoc/tags/return.html): Chỉ ra các hành vi khi xảy ra trường hợp ngoại lệ

- [@see](http://phpdoc.org/docs/latest/references/phpdoc/tags/see.html): Chỉ ra các yếu tố kế thừa hoặc override.

- [@uses](http://phpdoc.org/docs/latest/references/phpdoc/tags/uses.html): Chỉ ra các yêu tố cấu thành trực tiếp.

- [@property](http://phpdoc.org/docs/latest/references/phpdoc/tags/property.html): Cho biết có sử dụng một thành phần nào đó.

- [@license](http://phpdoc.org/docs/latest/references/phpdoc/tags/license.html): Thông tin về bản quyền

## 5. Tên file trong trường hợp không chứa class

Tên file trong trường hợp không chứa class nên được đặt dưới dạng `string_lower_with_underscore.php`
