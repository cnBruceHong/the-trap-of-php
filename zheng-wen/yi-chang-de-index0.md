代码：

```php
<?php
$test_array = array();
$test_array['string_index'] = "data in string index";
$test_array[] = "data in index 0";
$test_array[] = "data in index 1";
$test_array[] = "data in index 2";

foreach($test_array as $key => $val)
{
    if($key != 'string_index')
    {
        echo $val."<br>";
    }
}
```

期望输出：

```
data in index 0
data in index 1
data in index 2
```

实际输出：

```
data in index 1
data in index 2
```

剖析：

That's because the 'index 0' data has key 0. In PHP,`0`\(number zero\),`'0'`\(string zero\), and`''`\(empty string\) are all equivalent - they can get typecast to each other. If you'd simply done`print_r($test_array)`, you'd get

```
Array
(
    [string_index] => data in string index
    [0] => data in index 0
    [1] => data in index 1
    [2] => data in index 2
)
```

The other option would have been to use the strict inequality test \(`!==`\) which compares value AND type. In that case,`0 !== 'string index'`evaluates to true and everything works as expected.

