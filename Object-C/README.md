![APPLE](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQtXkljZ3FPu-ghG2UXFYRXnIz5gO0Dw_3TyO55UyJkgZcQTQOs5A)

#Object-C代码规范

## 一、留白与格式


### 1.空格 vs. 制表符
+ 只使用制表符、每层缩进关系使用一个制表符

正确:
```
    NSString *a
    if(1){
        if(1){
            doSomeThing(a)
        }
    }
  
```
错误:
```
  NSString *a
     if(1){
     if(1){
            doSomeThing(a)
        }
       }
  
```

### 2.方法声明和定义

 + 和返回类型之间须使用一个空格，参数列表中只有参数之间可以有空格。
方法应该像这样：

```
- (void)doSomethingWithString:(NSString *)theString {
  ...
}
```

### 3.方法调用
+ 调用时所有参数应该在同一行：

```
[myObject doFooWith:arg1 name:arg2 error:arg3];
```
+ 或者以冒号对齐多行参数

```
[myObject doFooWith:arg1
               name:arg2
              error:arg3];
```

## 二、命名

### 1.类名
类名（以及类别、协议名）应首字母大写，并以驼峰格式分割单词。
```
SomeClass
```

### 2.方法名
+ 方法名应该以小写字母开头，并混合驼峰格式。</br>

```
- (void)aMethodName
```
+ 每个具名参数也应该以小写字母开头。</br>

```
- (void)aMethodWithParamater:(id)aPatameter
```

+ 访问器方法应该与他们 要获取的 成员变量的名字一样，但不应该以get作为前缀。例如：

```
- (id)getDelegate;  // AVOID
- (id)delegate;     // GOOD
```
### 3.变量名
##### 尽量让变量名可以描述自己的作用！！！

+ 除遍历索引i或其他约定俗成的例子外，严禁使用a,b等无意义字母作为变量名。

```
int a; //such a foolish
```
+ 除有非常直观的含义(行数，tableView中的不同row与section)、不会被引用的的viewTag外，严禁使用 <a href="https://zh.wikipedia.org/wiki/魔術數字">maginc number</a>

```
[aInstacne callMethod:10086]  //what the xxx????
```

错误的命名:

```
int w;
int nerr;
int nCompConns;
tix = [[NSMutableArray alloc] init];
obj = [someObject object];
p = [network port];
int numErrors;
int numCompletedConnections;
tickets = [[NSMutableArray alloc] init];
userInfo = [someObject object];
port = [network port];
```

正确的命名:

```
int numErrors;
int numCompletedConnections;
tickets = [[NSMutableArray alloc] init];
userInfo = [someObject object];
port = [network port];
```

### 4.常量


常量名（如宏定义、枚举、静态局部变量等）应该以小写字母 k 开头，使用驼峰格式分隔单词，如：kInvalidHandle，kWritePerm。

## 三、Cocoa 和 Objective-C 特性

### 1.快速定义
+ 定义不可变集合类的时候尽量使用快速定义,在没有可变需求下不使用可变集合类

```
NSDictionary *dic = @{@"array" : @[@1,@2,@3],
                     @"string" : @"hello world",
                     @"number" : @(3127)
                    }
```

### 2.隐藏不必公开的属性与方法
+ 若一个属性或方法不应该被外部调用，在.m文件中使用extension创建

### 3.尽量使用点语法使代码简洁，可读

```
NSString *oldName = myObject.name;
myObject.name = @"Alice";
```

