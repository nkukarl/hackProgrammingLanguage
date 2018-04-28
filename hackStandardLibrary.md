# Hack Standard Library

### Dict\associate

```php
$my_keys = vec['one', 'two', 'three'];
$my_values = vec[1, 2, 3];
$my_dict = Dict\associate($my_keys, $my_values);

// $my_dict = dict['one' => 1, 'two' => 2, 'three' => 3];
```

```php
$my_keys = vec['red', 'green', 'blue', 'red'];
$my_values = vec[1, 2, 3, 4];
$my_dict = Dict\associate($my_keys, $my_values);

// $my_dict = dict['red' => 4, 'green' => 2, 'blue' => 3];
```

### Dict\merge

```php
$my_dict_1 = dict['red' => 1, 'green' => 2];
$my_dict_2 = dict['red' => 4, 'blue' => 3];
$my_dict = Dict\merge($my_dict_1, $my_dict_2);

// $my_dict = dict['red' => 4, 'green' => 2, 'blue' => 3];
```

### Dict\partition

```php
$my_dict = dict['one' => 1, 'two' => 2, 'three' => 3, 'four' => 4];
list($my_dict_evens, $my_dict_odds) = Dict\partition($my_dict, $val ==> $val % 2 == 0);

// $my_dict_evens = dict['two' => 2, 'four' => 4];
// $my_dict_odds = dict['one' => 1, 'three' => 3];
```

### Dict\partition_with_key

```php
$my_dict = dict['one' => 1, 'two' => 2, 'three' => 3, 'four' => 4];
list($my_dict_starts_with_t, $my_dict_not_starts_with_t) = Dict\partition_with_key($my_dict, $val ==> Str\starts_with($val, 't'));

// $my_dict_starts_with_t = dict['two' => 2, 'three' => 3];
// $my_dict_not_starts_with_t = dict['one' => 1, 'four' => 4];
```

### Dict\equal

```php
$my_dict_1 = dict['one' => 1, 'two' => 2];
$my_dict_2 = dict['one' => 1, 'two' => 2];
$my_dict_3 = dict['one' => 1, 'three' => 3];
$is_equal_1_vs_2 = Dict\equal($my_dict_1, $my_dict_2);
$is_equal_1_vs_3 = Dict\equal($my_dict_1, $my_dict_3);

// $is_equal_1_vs_2 = true;
// $is_equal_1_vs_3 = false;
```

### Dict\select_keys

```php
$my_dict = dict['one' => 1, 'two' => 2, 'three' => 3, 'four' => 4];
$my_dict_selected = Dict\select_keys($my_dict, vec['one', 'two']);

// $my_dict_selected = dict['one' => 1, 'two' => 2];
```

### Dict\flip

```php
$my_dict = dict['one' => 1, 'two' => 2, 'three' => 3];
$my_dict_flipped = Dict\flip($my_dict);

// $my_dict_flipped = dict[1 => 'one', 2 => 'two', 3 => 'three'];
```

### Dict\filter

```php
$my_dict = dict['one' => 1, 'two' => 2, 'three' => 3];
$my_dict_filtered = Dict\filter($my_dict, $value ==> $value === 2);

// $my_dict_filtered = dict['two' => 2];
```

### Dict\filter_keys

```php
$my_dict = dict['one' => 1, 'two' => 2, 'three' => 3];
$my_dict_filtered = Dict\filter_keys($my_dict, $value ==> $value === 'two');

// $my_dict_filtered = dict['two' => 2];
```

### C\contains

```php
$my_vec = vec[1, 2, 3];
$does_my_vec_contain_three = C\contains($my_vec, 3);
$does_my_vec_contain_four = C\contains($my_vec, 4);

// $does_my_vec_contain_three = true;
// $does_my_vec_contain_four = false;
```

### C\find

```php
$my_vec = vec[1, -2, 3, -4];
$first_negative_number_in_my_vec = C\find($my_vec, $val ==> $val < 0);

// $first_negative_number_in_my_vec = -2;
```

```php
$my_vec = vec[1, 2, 3, 4];
$first_negative_number_in_my_vec = C\find($my_vec, $val ==> $val < 0);

// $first_negative_number_in_my_vec = null;
```

### C\find_key

```php
$my_dict = dict['one' => 1, 'two' => 2, 'three' => 3];
$key_to_value_three = C\find_key($my_dict, $val ==> $val === 3);

// $key_to_value_three = 'three';
```

### C\is_empty

```php
$my_non_empty_vec = vec[1, 2, 3];
$is_my_non_empty_vec_emtpy = C\is_empty($my_non_empty_vec);

// $is_my_non_empty_vec_emtpy = false;

$my_empty_vec = vec[];
$is_my_empty_vec_emtpy = C\is_empty($my_empty_vec);

// $is_my_empty_vec_emtpy = true;
```

### C\count

```php
$my_vec = vec[1, 2, 3];
$my_vec_length = C\count($my_vec);

// $my_vec_length = 3;
```

### C\reduce

```php
$my_vec = vec[1, 2, 3];
$res = 0;
$ans = C\reduce($my_vec, ($res, $value) ==> {return $res + $value;}, $res);

// $ans = 6;
```

### C\any

```php
$my_vec = vec[1, 2, 3, 4, 5];
$does_my_vec_contain_evens = C\any($my_vec, $val ==> $val % 2 === 0);

// $does_my_vec_contain_evens = true;
```

### C\every

```php
$my_vec = vec[1, 2, 3, 4, 5];
$does_my_vec_contain_all_evens = C\every($my_vec, $val ==> $val % 2 === 0);

// $does_my_vec_contain_all_evens = false;
```

### Vec\filter

```php
$my_vec = vec[1, 2, 3, 4, 5];
$my_vec_evens = Vec\filter($my_vec, $val ==> $val % 2 === 0);

// $my_vec_evens = vec[2, 4];
```

### Vec\concat

```php
$my_vec_1 = vec[1, 2];
$my_vec_2 = vec[3, 4];
$my_vec = Vec\concat($my_vec_1, $my_vec_2);

// $my_vec = vec[1, 2, 3, 4];
```

### Vec\map

```php
$my_vec = vec[1, 2, 3];
$my_vec_doubled = Vec\map($my_vec, $val ==> $val * 2);

// $my_vec_doubled = vec[2, 4, 6];
```

### Vec\intersect

```php
$allowed_vec = vec[1, 2, 3];
$val1 = 0;
$val2 = 4;

$provided_vec = vec[$val1, $val2];

$flag1 = !C\contains($allowed_vec, $val1) && !C\contains($allowed_vec, $val2);
$flag2 = C\is_empty(Vec\intersect($allowed_vec, $provided_vec));

$allowed_vec = vec[1, 2, 3];
$val1 = 1;
$val2 = 4;

$provided_vec = vec[$val1, $val2];

$flag1 = !C\contains($allowed_vec, $val1) && !C\contains($allowed_vec, $val2);
$flag2 = C\is_empty(Vec\intersect($allowed_vec, $provided_vec));

$allowed_vec = vec[1, 2, 3];
$val1 = 1;
$val2 = 2;

$provided_vec = vec[$val1, $val2];

$flag1 = !C\contains($allowed_vec, $val1) && !C\contains($allowed_vec, $val2);
$flag2 = C\is_empty(Vec\intersect($allowed_vec, $provided_vec));
```

