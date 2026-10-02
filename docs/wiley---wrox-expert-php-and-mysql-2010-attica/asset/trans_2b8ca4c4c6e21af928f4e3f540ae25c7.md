
它们是函数 ZEND_FENTRY 的简写。要定义一个抽象方法，函数入口表看起来会像这样：

```
ZEND_ACC_ABSTRACT(method_name, NULL, NULL, ZEND_ACC_PUBLIC )
```

对于之前的代码，请考虑：

- 第一个参数是方法名，但引用实际函数实现的却是第二个参数，或者因为没有实现而使用 NULL 值。第二个参数在使用 PHP_ME 时会自动从方法名派生，或在使用 PHP_FUNCTION 时从函数名派生。
- 第二个参数是新增的。对于抽象方法它始终为 NULL。
- 第三个参数是参数信息数组，这里为 NULL，因为示例方法没有参数。

很可能在某个时候需要调用一个类的方法。后面会有专门的章节介绍。

## 使用属性

声明属性应在类初始化时进行（在 MINIT 函数中或像前一节建议的那样在辅助函数中）。

声明需要类入口、属性名、字符串长度、默认值以及可见性：

```
zend_declare_property_string(helloworld_ce_ptr, "bar", 3,
"default value", ZEND_ACC_PUBLIC TSRMLS_DC);
```

到现在为止，TSRMLS_DC 常量的含义应该已经清楚了。上面的声明是针对字符串的。与 API 的其他部分一样，其他数据类型也有对应的函数。然而，属性的类型在运行时是可以（暂时）改变的。

设置和获取属性与使用数组的方式类似。将属性设为 double 是这样做的：

```
zend_update_property_double( _this_ce, _this_zval, property_name,
strlen(property_name), 1 TSRMLS_CC)
```

获取属性会返回一个 zval，因此它很可能被包装成类似 Z_VALSTR_P 的形式。倒数第二个参数表示如果属性不存在是否抛出警告（1 表示静默，0 表示详细）：

```
Z_LVAL_P(zend_read_property(_this_ce, _this_zval, property_name,
strlen(property_name), 1 TSRMLS_CC))
```

根据你生成类的方式，头文件中可能存在预定义的宏来封装常见的属性获取功能。检查头文件，看看你的扩展是否已存在这些宏。如果没有，定义一些有用的宏会很有帮助，因为手动传递所有参数会变得很繁琐。

当然，属性也可以像方法一样使用 `ZEND_ACC_STATIC` 声明为静态。属性的读写函数有静态变体，不需要传递对象 zval。

## 使用类常量

类也可以拥有类特定的常量。如第一章所述，类常量始终是 public 且 static。它们在类初始化期间定义：

```
zval *tmp_s;

tmp_s = (zval *) malloc(sizeof(zval));
INIT_PZVAL(tmp_s);
ZVAL_LONG(tmp_s, 255);
zend_symtable_update(&(helloworld_ce_ptr->constants_table), "MY_PI",
    8, (void *) &tmp_s, sizeof(zval *), NULL);
```

代码直接引用了常量的符号表。顺便说一下，符号表还用于各种其他用途，包括存储在全局 PHP 作用域中可用的变量。它们在幕后使用哈希表实现，实际上可以像普通哈希表一样引用。

符号表期望一个 zval，因此在插入表之前必须先初始化它。这是使用 malloc 而不是 emalloc 合适的情况之一，因为后者在请求之间会被垃圾回收器错误地清理。

虽然没有阻止更改常量的机制，但在初始化后更改常量并不是一个好主意。

在应用程序中使用常量有两种方法：

- 最简单的方法是通过预处理器定义它并在代码中引用它，这可以正常工作，因为常量永远不应改变。
- 另一种方法是用 `zend_symtable_find`：
```c
zend_symtable_find(&(helloworld_ce_ptr->constants_table), key,
    strlen(key), (void **)&data );
```

该函数的行为与 `zend_hash_find` 相同，后者有特殊宏来处理数字符号键。

## 创建接口

接口在定义方式上几乎与类相同。区别在于注册方式和方法定义方式。此外，正如你可能从 PHP 中所知，接口不能有属性。此外，所有接口方法都是 public 且没有实现。

按照以下基本步骤操作：

- 1. 按为类定义接口的常规方式定义接口，只是将对 `zend_register_internal_class` 的调用替换为：
```c
helloworld_ce = zend_register_internal_interface(&ce, TSRMLS_CC);
```

- 2. 接口也可以扩展其他接口。扩展类的代码揭示了 PHP 面向对象编程内部工作原理的一些信息。首先尝试查找被扩展接口的类入口，然后如果找到就扩展它：

```
if (SUCCESS == zend_hash_find(CG(class_table), "interface_to_extend", 8, (void **)&parent_ce)) {
    if (parent_ce) {
        zend_do_inheritance(new_interface_ce_ptr, *parent_ce TSRMLS_CC);
    }
}
```

- 3. 接口方法是抽象的，因此定义它与在传统类中定义抽象方法非常相似。将其输入方法表但不要实现它：

```
ZEND_FENTRY(interfaceMethod, NULL, NULL,
            ZEND_ACC_ABSTRACT | ZEND_ACC_INTERFACE | ZEND_ACC_PUBLIC)
```

- 4. 在类中实现接口。实际上是两个步骤；第二步是实现接口中的所有方法——到现在应该很清楚了——但首先必须将类指定为接口的实现：

```
zend_class_entry **tmp;
if (SUCCESS == zend_hash_find(CG(class_table), "interface_name", 8, (void **)&tmp)) {
    zend_class_implements(helloworld_ce_ptr TSRMLS_CC, 1, *tmp);
}
```

可以同时实现多个接口。倒数第二个参数是正在实现的接口数量。该函数本身是变长的。

正如代码所示，接口不需要与类在同一个扩展中。它会在运行时尝试定位接口。没有接口会影响多态性，但不会影响类的其他功能，因此如果找不到接口，忽略它或发出警告是可以接受的。然而，仍然重要的是记住声明依赖关系。

## 与对象交互

所有类在 PHP 中立即可用。不过，通常也有用的是从 PHP 扩展内部访问类。对于扩展编写的其余过程，PHP 中能做的所有事情在扩展中也能做到。

## 识别对象

对象通过类入口标识。如果对象属于扩展本地，则可以方便地获得指向类入口的指针。对于外部或未知类型的对象，存在检索类入口的方法：

```
zval *my_obj;
zend_class_entry *ce;
...
ce = zend_get_class_entry(my_obj TSRMLS_CC);

/* or */
ce = Z_OBJCE_P(my_obj);
```

仅凭类名也可以检索类入口：

```
zend_class_entry *ce;
ce = zend_lookup_class( class_name, strlen(class_name) );
```

一旦拥有一个或两个类入口，就能做很多事情。其中最有用的之一是识别和检查类之间的关系。类入口和 zval 都可用于检索类名以进行字符串比较或其他需要：

```
char *class_name;
size_t class_name_len;
zend_get_object_class_name( my_obj, &class_name, &class_name_len );

class_name = emalloc( class_entry->name_len*sizeof(char *) );
memcpy( class_name, class_entry->name, class_entry->name_len );
```

前几行代码根据 zval 获取类名，后几行根据类入口对象获取类名。然而，直接对类名进行测试并不是一个好主意。毕竟，多态性会发挥作用。要正确检查，可以改用 instanceof：

```
zend_bool is_instance = instanceof_function( class_entry_1, class_entry_2 );
```

在某些情况下，有必要提前测试类以模拟类型提示行为，并在对象不适合特定情况时抛出警告。

## 调用方法

在对象上调用方法实际上不需要类入口。只需一个 zval 即可。调用方法主要有两个函数——一个用于零参数的方法，另一个用于一个或多个参数的方法：

```
zend_call_method_with_0_params( &my_obj, NULL, NULL, "method_name", &return_val);
```

还有用于一个、两个和三个参数的宏。返回值存储在最后一个参数中（它是一个 zval 指针）。第二个参数用于类入口，用于静态方法，第三个参数用于函数代理（如果使用）。

使用本章的所有工具，很容易接受一个 mysqli_result 对象并遍历所有行：

```
zval *result, *row;
...

zend_call_method_with_0_params( &result, NULL, NULL, "fetch_assoc", &row);

while ( Z_TYPE_P( row ) != IS_NULL ) {
    HashTable *realRow = Z_ARRVAL_P(row);

    /* do something with the row */

    zval_dtor( row );
    zend_call_method_with_0_params( &result, NULL, NULL, "fetch_assoc", &row);
}
```
