# 最后修改日期 2022/11/09
## C++基础入门
### 变量
- 变量的作用
  ```cpp
  方便我们管理内存空间
  ```
- 变量使用语法
  ```cpp
  数据类型  变量名 = 变量初始值；
  示例：
  int a = 10;

  cout << "a = " << a << endl;
  ```
  释义：创建变量 a ，输出内容为变量 a 的值。
### 常量
- 常量的作用
  ```cpp
  用于记录程序中不可更改的数据
  ```
- #define 宏常量使用语法
  ```cpp
  #define 常量名 常量值

  宏常量通常定义在最上方
  ```
  释义：#define 通常在文件上方定义，表示一个常量
- const 修饰的常量使用语法
  ```cpp
  const 数据类型 常量名 = 常量值

  修饰变量位置可在最上方也可在调用处上方
  ```
  释义：const通常在变量定义前加关键字const，修饰该变量为常量，不可修改
- 示例：
  ```cpp
  #define Day 365

  const int month = 12；
  ```
### 关键字
- 不要用关键字给变量或常量起名称，否则会产生歧义。

| asm       | auto         | bool        | break            | case     | catch    | char    |
|-----------|--------------|-------------|------------------|----------|----------|---------|
| class     | const        | const_cast  | continue         | default  | delete   | do      |
| double    | dynamic_cast | else        | enum             | explicit | export   | extern  |
| false     | float        | for         | friend           | goto     | if       | inline  |
| int       | long         | mutable     | namespace        | new      | operator | private |
| protected | public       | register    | reinterpret_cast | return   | short    | signed  |
| sizeof    | static       | static_cast | struct           | switch   | template | this    |
| throw     | true         | try         | typedef          | typeid   | typename | union   |
| unsigned  | using        | virtual     | void             | volatile | wchar_t  | while   |

### 标识符命名规则
- 标识符作用：给变量、常量命名
  - 标识符不能是关键字
  - 标识符只能由字母、数字、下划线组成
  - 第一个字符必须为字母或下划线
  - 标识符中字母区分大小写
## 数据类型
C++规定在创建一个变量或常量时，必须要指定出相应的数据类型，否则无法给变量分配内存。
### 数据类型-整型
- 整型变量表示的是整数类型的数据
- C++中能够表示整型的类型有以下几种方式，区别在于所占内存空间不同：

| 数据类型             | 占用空间                                      | 取值范围        |
|--------------------|---------------------------------------------|-----------------|
| short（短整数）        | 2字节                                         | （-2^15 ~2^15-1) |
| int（整型）            | 4字节                                         | （-2^31 ~2^31-1） |
| long（长整型）         | Windows为4字节，Linux为4字节（32位），8字节（64位） | （-2^31 ~2^31-1） |
| long long (长长整型) | 8字节                                         | （-2^63 ~2^63-1） |
### 数据类型sizeof关键字
- 作用：利用sizeof关键字可以统计数据类型所占内存大小
- 语法
  ```cpp
  sizeof（数据类型 / 变量）
  ```
- 示例：
  ```cpp
  int main() {
    short a = 10;
    int b =11;
    long c = 12;
    long long d = 13;
    cout << "short 类型所占内存空间为：" << sizeof(short) << endl;
    cout << "int 类型所占内存空间为：" << sizeof(int) << endl;
    cout << "long 类型所占内存空间为：" << sizeof(long) << endl;
    cout << "long long 类型所占内存空间为：" << sizeof(long long) << endl;
    system("pause");
    system("cls");   //清屏操作
    return 0;
  }
  ```
### 数据类型-实型
- 作用：用于表示小数
- 浮点型变量分为两种：
  - 单精度 float
  - 双精度 double
  - 两者区别在于表示的有效数字范围不同
  
| 数据类型 | 占用空间 | 有效数字范围    |
|----------|--------|------------|
| float    | 4字节    | 7位有效数字     |
| double   | 8字节    | 15~16位有效数字 |
- 默认情况下，输出一个小数，会显示出6位有效数字
- float 类型的变量后一般加一个 f ，否则float的数据类型默认识别为double双精度。
- 示例：
  ```cpp
  int main() {
  float f1 = 3.1415926f;
  double f2 =3.1415926;
  cout << "f1 = " << f1 << endl;
  cout << "f2 = " << f2<< endl;
  
  //科学计数法
  float f3 = 3e2;    //3 * 10^2;
  float f4 = 3e-2；  //3 * 0.1^2;
  // e 后面如果是正数，则代表乘以100^n;
  // e 后面如果是负数，则代表乘以0.1^n;

  system("pause");
  return 0;
  }
  ```
### 数据类型-字符型
- 作用：字符型变量用于显示单个字符
- 语法：
  ```cpp
  char ch = 'a';
  ```
  注意1：在显示字符型变量时，用单引号将字符括起来，不要用双引号
  注意2：单引号内只能有一个字符，不可以用字符串
- C和C++中字符型变量只占用一个字节
- 字符型变量并不是把字符本身放到内存中存储，而是将对应的ASCII编码放入到存储单元
- 示例
  ```cpp
  int main() {
      char ch1 = 'a';
      char ch2 = 'A';

      cout << ch1 << endl;
      cout << (int)ch2 << endl;    //释义1
  system("pause");
  return 0;
  }
  ```
  释义1：输出 char 被强制转化成 int 类型的语句。就是输出 A 的ASCII编码 ‘65’
- ASCII码大致由以下两部分组成：
  - ASCII非打印控制字符：ASCII表上的数字 0-31 分配给了控制字符，用于控制打印机等一些外围设备
  - ASCII打印字符：数字 32-126 分配给了能在键盘上找到的字符，当查看或打印文档时就会出现。
### 数据类型-转义字符
- 作用：用于表示一些不能显示出来的ASCII字符，例如常用的有：\n \\ \t
- 
### 数据类型-字符串型
- 作用：用于表示一串字符
- 注意：字符串值需要用双引号 "" 包含起来，与字符使用的单引号 '' 做区分。
- C风格字符串：char 变量名[] = "字符串值"；
  示例：
  ```cpp
  int main() {
    char str1[] = "hello-world";   //C风格字符串需要在变量名后面加中括号 []
    cout << str1 << endl;
    system("pause");
    return 0;
  }
  ```
- C++风格字符串：string 变量名 = "字符串值"；
  示例：
  ```cpp
  #include<string>   //用C++风格字符串时候，要引用这个头文件
  int main() {
    string str2 = "hello-world";
    cout << str2 << endl;
    system("pause");
    return 0;
  }
  ```
### 布尔类型bool
- 作用：布尔数据类型代表真或假的值
- bool类型只有两个值
  - true  --- 真（本质是1）
  - false --- 假（本质是0）
- bool类型占1个字节大小 
- 示例：
  ```cpp
  int main() {
    bool flag = true;
    cout << flag << endl;   

    flag = false;           //重新赋值
    cout << flag << endl;

    cout << "size of bool =" << sizeof(bool) << endl;

    system("pause");
    return 0;
  }
  ```
### 数据的输入
- 作用：用于从键盘获取数据
- 关键字：cin
- 语法
  ```cpp
  cin >> 变量；
  ```
- 示例：
  ```cpp
  int main() {
    int a = 0;
    cout << "请输入整型变量：" << endl;
    cin >> a;
    cout << a << endl;

    double d =0;
    cout << "请输入浮点型变量：" << endl;
    cin >> d;
    cout << d << endl;

    char ch =0;
    cout << "请输入字符型变量：" << endl;
    cin >> ch;
    cout << ch << endl;

    system("pause");
    return 0;
  }
  ```
## 运算符
作用：用于执行代码的运算
| 运算符类型 | 作用                                  |
|-------|-------------------------------------|
| 算数运算符 | 用于处理四则运算                      |
| 赋值运算符 | 用于将表达式的赋值给变量              |
| 比较运算符 | 用于表达式的比较，并返回一个真值或假值 |
| 逻辑运算符 | 用于根据表达式的值返回真值或假值      |
### 算数运算符
  作用：用于处理四则运算

| 运算符 | 术语       | 示例       | 结果     |
|--------|-----------|------------|----------|
| +      | 正号       | +3         | 3        |
| -      | 负号       | -3         | -3       |
| +      | 加         | 10+5       | 15       |
| -      | 减         | 10-5       | 5        |
| *      | 乘         | 10*5       | 50       |
| /      | 除         | 10/5       | 2        |
| %      | 取模（取余） | 10%3       | 1        |
| ++     | 前置递增   | a=2;b=++a; | a=3;b=3  |
| ++     | 后置递增   | a=2;b=a++; | a=3;b=2  |
| --     | 前置递减   | a=2;b=--a; | a=1;b=1; |
| --     | 后置递减   | a=2;b=a--; | a=1,b=2; |
- 示例：
  ```cpp
  int main() {
    //加减乘除
    int a1 = 10;
    int b1 = 3;

    cout << a1 + b1 << endl;
    cout << a1 - b1 << endl;
    cout << a1 * b1 << endl;
    cout << a1 / b1 << endl;  //两个整数相除，结果依然是整数，将小数部分去除

    int a3 = 10;
    int b3 = 20;
    cout << a3 / b3 << endl;  //结果为0

    int a2 = 10；
    int b2 = 0；
    cout << a2 / b2 << endl;  //错误！两个数相除，除数是不可以为0的

    //两个小数可以相除
    double d1 = 0.5；
    double d2 = 0.25；
    cout << d1 / d2 << endl;  //运算的结果也可以是小数
    
    //取模运算本质就是求余数
    int a4 = 10;
    int b4 = 3;
    cout << a4 % b4 << endl;  //取余为1

    int a5 = 10;
    int b5 = 20;
    cout << a5 % b5 << endl;  //取余为10，当被除的数没有除数大时，取余的值为被除的数值。取模运算的除数不可为0；

    //两个小数时不可以做取模运算的

    //前置与后置的区别
    //前置递增是先让变量+1然后进行表达式运算
    int a6 = 10;
    int b6 = ++a6 * 10;
    cout << a6 << endl;  //输出为11
    cout << b6 << endl;  //输出为110

    //后置递增是先进行表达式运算后让变量+1
    int a7 = 10;
    int b7 = a7++ * 10;
    cout << a7 << endl;  //输出为11
    cout << b7 << endl;  //输出为100

    //前置递减是先让变量-1然后进行表达式运算
    int a8 = 10;
    int b8 = --a8 * 10;
    cout << a8 << endl;  //输出为9
    cout << b8 << endl;  //输出为90

    //后置递减是先进行表达式运算后让变量-1
    int a9 = 10;
    int b9 = a9-- * 10;
    cout << a9 << endl;  //输出为9
    cout << b9 << endl;  //输出为100

    system("pause");
    return 0;
  }
  ```
### 赋值运算符
  作用：用于将表达式的值赋给变量

| 运算符 | 术语   | 示例      | 结果     |
|--------|------|-----------|----------|
| =      | 赋值   | a=2;b=3;  | a=2;b=3; |
| +=     | 加等于 | a=0;a+=2; | a=2;     |
| -=     | 减等于 | a=5;a-=3; | a=2;     |
| * =    | 乘等于 | a=2;a*=2; | a=4;     |
| /=     | 除等于 | a=4;a/=2; | a=2;     |
| %=     | 模等于 | a=3;a%=2; | a=1;     |
- 示例：
  ```cpp
  int main() {
    //加等于 +=
    int a = 10;
    a += 2;             //a = a + 2
    cout << a << endl;  //输出为12

    //减等于 -=
    a = 10;
    a -= 2;             //a = a - 2
    cout << a << endl;  //输出为8

    //乘等于 *=
    a = 10;
    a *= 2;             //a = a * 2
    cout << a << endl;  //输出为20

    //除等于 /=
    a = 10;
    a /= 2;             //a = a / 2
    cout << a << endl;  //输出为5

    //模等于 %=
    a = 10;
    a %= 2;             //a = a % 2
    cout << a << endl;  //输出为0

    system("pause");
    return 0;

  }
  ```
### 比较运算符
  作用：用于表达式的比较，并返回一个真值(1)或假值(0)

| 运算符 | 术语     | 示例 | 结果 |
|--------|--------|------|------|
| ==     | 相等于   | 4==3 | 0    |
| !=     | 不等于   | 4!=3 | 1    |
| <      | 小于     | 4<3  | 0    |
| >      | 大于     | 4>3  | 1    |
| <=     | 小于等于 | 4<=3 | 0    |
| >=     | 大于等于 | 4>=1 | 1    |
- 示例
  ```cpp
  int main() {

    //比较运算符
    int a = 10;
    int b = 20;

    // ==
    cout << (a == b) << endl;  //输出0，值为假

    // !=
    cout << (a != b) << endl;  //输出1，值为真

    // >
    cout << (a > b) << endl;   //输出0，值为假

    // <
    cout << (a < b) << endl;   //输出1，值为真

    // <=
    cout << (a <= b) << endl;  //输出1，值为真

    // >=
    cout << (a >= b) << endl;  //输出0，值为假

    system("pause");
    return 0;
  }
  ```
### 逻辑运算符
- 作用：用于根据表达式的值换货真值或假值
- 运算符号

| 运算符 | 术语 | 示例   | 结果                                                |
|--------|-----|--------|---------------------------------------------------|
| ！      | 非   | !a     | 如果a为假，则!a为真；如果a为真，则!a为假               |
| &&     | 与   | a&&b   | 如果a和b都为真，则结果为真，否则为假                  |
| \|\|   | 或   | a\|\|b | 如果a和b有一个为真，则结果为真，二者都为假时，结果为假 |
- 示例
  ```cpp
  int main() {
    int a = 10;

    //在C++中值除了0都为真
    //非运算，真变假，假变真
    //逻辑运算符  非  ！
    cout << !a << endl;    //输出为0，值为假。非真即为假
    cout << !!a << endl;    //输出为1，值为真。非假即为真

    //同真为真，其余为假
    //逻辑运算符 与   &&
    int b = 10;
    cout << (a && b) << endl;   //输出为1，值为真。
    int a = 0;
    cout << (a && b) << endl;   //输出为0.值为假。
    int b = 0;
    cout << (a && b)  << endl;  //输出为0，值为假，因为变量的值为0时都为假。

    //同假为假，其余为真
    //逻辑运算符 或   ||  
    int a = 10;
    int b = 10; 
    cout << (a || b) << endl;   //输出为1，值为真。
    int a = 0;
    cout << (a || b) << endl;   //输出为1，值为真。
    int b = 0;
    cout << (a || b) << endl;   //输出为0，值为假。

    system("pause");
    return 0;

  }
  ```
## 程序流程结构
C/C++支持最基本的三种程序运行结构：顺序结构、选择结构、循环结构
- 顺序结构：程序按顺序执行，不发生跳转
### 选择结构
#### if 语句
  作用：依据条件是否满足，有选择的执行相应功能，执行满足条件的语句
  if 语句的三种形式
  - 单行格式 if 语句
    语法：if (条件) {条件满足执行的语句}
    插入图片
    示例：
    ```cpp
    int main() {
      //选择结构单行 if 语句
      //用户输入分数，如果分数大于600，视为考上一本大学，在屏幕上输出

      //用户输入分数
      int score = 0;
      cout << "请输入分数：" << endl;
      cin >> score;                    //把输入的值赋值到 score 中

      //打印用户输入的分数
      cout << "您输入的分数：" << score << endl;

      //判断分数是否大于600，如果大于，那么输出
      // if 条件后面不要加分号 ; 
      if (score > 600) {                         //判断score值是否大于600
        cout << "恭喜您考上了一本大学" << endl;
      }

      system("pause");
      return 0;
    }
    ```
  - 多行格式 if 语句
    语法： if (条件) {条件满足执行的语句}else{条件不满足执行的语句}
    ![单行格式if语法](/upload/2022/08/%E5%8D%95%E8%A1%8C%E6%A0%BC%E5%BC%8Fif%E8%AF%AD%E6%B3%95.webp)
    示例：
    ```cpp
    int main() {
      //选择结构  多行 if 语句
      //输入考试分数，如果分数大于等于600，判断考上一本，输出考上一本
      //如果输入分数低于600，则输出未考上一本

      //输入分数
      int score = 0;
      cout << "请输入考试分数：" << endl;
      cin >> score;

      //输出用户输入的分数
      cout << "您输入的分数为：" << score << endl;

      //判断是否满足条件
      if ( score >= 600 ) {                   //判断score是否大于等于600
        cout << "恭喜考上了一本大学" << endl;  //当score大于等于600时，值为真，则输入此语句
      }
      else {
        cout << "未考上一本大学" << endl;      //当score小于600时，值为假，则输出此语句
      }

      system("pause");
      return 0;
    }
    ```
  - 多条件的 if 语句
    语法：if (条件1) {条件1满足执行的语句}else if (条件2) {条件2满足执行的语句}.......else {条件都不满足时执行的语句}
    ![多行if语句](/upload/2022/08/%E5%A4%9A%E8%A1%8Cif%E8%AF%AD%E5%8F%A5.webp)
    示例：
    ```cpp
    int main() {
      //选择结构 多条件 if 语句
      //输入一个分数，如果大于600分，判断考上一本，如果大于等于500分，判断考上二本，如果大于等于400分，则判断考上三本.....如果上述条件都不满足，则判断没考上本科

      //用户输入分数
      int score = 0;
      cout << "请输入分数：" << endl;
      cin >> score;

      //提示用户输入的分数
      cout << "您输入的分数为：" << score << endl;

      //判断
      if (score > 600) {                      //判断score是否大于600
        cout << "您考上了一本" << endl;        //大于600时，值为真，则输出此语句
      }
      else if (score > 500) {                 //判断score是否大于500
        cout << "您考上了二本" << endl;        //大于500时，值为真，则输出此语句
      }
      else if (score > 400) {                 //判断score是否大于400
        cout << "您考上了三本" << endl;        //大于400时，值为真，则输出此语句
      }
      else {                                  //条件都不满足时
        cout << "您没考上本科" << endl;        //输出此语句
      }

      system("pause");
      return 0;
    }
    ```
  - 嵌套 if 语句
    用处：在 if 语句中，可以嵌套使用 if 语句，达到更精确的条件判断
    ![多条件if语句](/upload/2022/08/%E5%A4%9A%E6%9D%A1%E4%BB%B6if%E8%AF%AD%E5%8F%A5.webp)
    示例要求：
    - 提示用户输入一个分数，根据分数做如下判断
    - 分数如果大于600分视为考上一本，大于500分考上二本，大于400分考上三本，其余视为没考上本科
    - 在一本分数中，如果大于700分视考入北大，大于650分视考上清华，大于600分考入人大
  
    示例：
    ```cpp
    int main() {

      int score = 0;

      //提示输入分数
      cout << "请输入考试分数" << endl;
      cin >> score;

      //显示高考分数
      cout << "您输入的分数为：" << score << endl;

      //判断
      //大于600分
      if (score > 600) {
        cout << "您考上了一本。" << endl;
        //大于700分
        if (score > 700) {
          cout << "您考上北大。" << endl;
        }
        //大于650分
        else if (score > 650) {
          cout << "您考上清华。" << endl;
        }
        //未满足条件时
        else {
          cout << "您考上人大。" << endl;
        }
      }
      //大于500分
      else if (score > 500) {
        cout << "您考上了二本。" << endl;
      }
      //大于400分
      else if (score > 400) {
        cout << "您考上了三本。" << endl;
      }
      //条件都不满足时
      else {
        cout << "您未考上本科。" << endl;
      }

      system("pause");
      return 0;
    }
    ```
  - 游戏段位排名划分
    要求：
    - 按照300分为大师、260分为铂金、220分为钻石、180分为黄金划分
    - 超过320分为王者、超过360分为最强王者、超过400分宇宙韩国
    示例：
    ```cpp
    int main() {
      int score = 0;
      cout << "请输入您的排位得分：" << endl;
      if (score > 300) {
        cout << "您的段位已到大师级别" >>
        if （score > 320） {
          cout << "您的世界排名已到王者" << endl;
        }
        else if (score > 360){
          cout << "您的世界排名已到最强王者" << endl;
         }
         else if (score > 400) {
          cout << "您的世界排名已到宇宙韩国" << endl;
         }
         else {
          cout << "抱歉，您的分数还没到世界排名，仅仅是大师级别" << endl;
         }
      }
      else if (score > 260) {
        cout << "您的段位已到铂金级别" << endl;
      }
      else if (score > 220) {
        cout << "您的段位已到钻石级别" << endl;
      }
      else if (score > 180) {
        cout << "您的段位已到黄金级别" << endl;
      }
      else {
        cout << "抱歉，您的排位得分还未达到黄金段位" << endl;
      }

      system("pause");
      return 0;
    }
    ```
#### 三目运算符
  作用：通过三目运算符实现简单的判断
  语法：表达式1 ? 表达式2 : 表达式3
- 释义：
  ```cpp
  如果表达式1的值为真，执行表达式2，并返回表达式2的结果；
  如果表达式1的值为假，执行表达式3，并返回表达式3的结果；
  ```
  示例：
  ```cpp
  int main() {

    int a = 10;
    int b = 20;
    int c = 0;

    c = (a > b ? a : b);         //a > b 的值为假，执行表达式 b ，并且为 c 赋值
    cout << "c =" << c << endl;  

    //在C++中三目运算符返回的是变量，可以继续赋值
    (a > b ? a : b) = 100;       //a > b 的值为假，执行表达式b，并且为 b 赋值
    cout << "a = " << a << endl;  //输出10
    cout << "b = " << b << endl;  //输出100

    (a < b ? a : b) = 100;       //a < b 的值为真，执行表达式a，并且为 a 赋值
    cout << "a = " << a << endl;  //输出100
    cout << "b = " << b << endl;  //输出20

    system("pause");
    return 0;
  }
  ```
#### switch语句
  作用：执行多条件分支语句；
- 语法：
  ```cpp
  switch(表达式) {
    case 结果1:执行语句;
    break;

    case 结果2:执行语句;
    break;

    ......

    default:执行语句;
    break;
  }
  ```
  示例：
  ```cpp
  int main() {
  //给电影打分
  //10~9 经典
  //8~7 非常好
  //6~5 一般
  //5以下 烂片

  //提示用户给电影打分
  cout << "请给电影进行打分" << endl;

  //用户开始进行打分
  int score = 0;
  cin >> score;
  cout << "您打的分数为：" << score << endl;

  //根据用户输入的分数来提示用户最后的结果
  switch (score) {
    case 10:
        cout << "您认为是经典电影" << endl;
        break;
    case 9:
        cout << "您认为是经典电影" << endl;
        break;
    case 8:
        cout << "您认为是非常好的电影" << endl;
        break;
    case 7:
        cout << "您认为是非常好的电影" << endl;
        break;
    case 6:
        cout << "您认为是一般的电影" << endl;
        break;
    case 5:
        cout << "您认为是一般的电影" << endl;
        break;
    default :
        cout << "您认为是烂片" << endl;
        break;
    }
  }
  ```
  if 语句与 switch 区别：
  ```cpp
  switch 缺点：判断时候只能是整型或者字符型，不可以判断一个区间(指定值)
  switch 优点：结构清晰，执行效率高
  注意：case里如果没有break,那么程序会一直向下执行
  ```
### 循环结构
#### while 循环语句
  作用：满足循环条件，执行循环语句
  语法：while(循环条件){循环语句}
  释义：只要循环条件的结果为真，就执行循环语句
  插入图片
- 示例：
  ```cpp
  int main() {

    //从0开始循环输出到9
    //注意事项：在写循环一定要避免死循环
    //在执行循环语句的时候，程序必须提供跳出循环的出口，否则出现死循环
    int num = 0;

    //while ()中填入循环条件
    while (num < 10 ) {
      cout << num << endl;
      num++;
    }

    system("pause");
    return 0;

  }
  ```
  案例：猜数字游戏
  要求：系统随机生成一个1-100之间的数字，玩家进行猜测，如果猜错提示玩家数字过大或过小，如果猜对了提示玩家胜利，并且退出游戏。
  插入图片
  代码：
  ```cpp
  int main() {

    //添加随机数种子，利用当前时间系统生成随机数，防止每次随机数都一样
    srand ( (unsigned int)time(null) );
    //系统生成随机数
    int num = rand()%100+1;     //生成0~99的随机数,+1是指代1-100;
    
    //玩家进行猜测
    int val = 0;
    cout << "请玩家输入猜测的数字：" << endl;

    while (1) {
    cin >> val;
    //判断猜测
    if ( val > num) {             //猜错提示过大,重新返回玩家进行猜测
      cout << "猜测过大" << endl;
    }
    else if (val < num ) {         //猜错提示过小,重新返回玩家进行猜测
      cout << "猜测过小" << endl;
    }
    else {                             //猜对  退出游戏   
      cout << "恭喜你猜对了" << endl;
    }
    }
    system("pause");
    return 0;
    
  }
  ```
#### do...while 循环语句
  作用：满足循环条件，执行循环语句
  语法： do{循环语句} while(循环条件)；
  注意：与while的区别在于do...while会先执行一次循环语句，再判断循环条件
  插入图片
- 示例：
  ```cpp
  int main() {
    //在屏幕中输出0-9这十个数字

    int num = 0;

    do {                     //先输出循环语句
      cout << num << endl;     
      num++;                 
    }while (num < 10);       //判断循环条件

    system("pause");
    return 0;
  }
  ```
  练习案例：水仙花数
  案例描述：水仙花数是指一个3位数，他的每个位上的数字的3次幂之和等于它本身
  例如：1^3+5^3+3^3=153
  请利用 do...while语句，求出所有3位数中的水仙花数
  ```cpp
  #include(math.h)
  int main() {

    int sum  = 100;
    do {
      int a = 0;
      int b = 0;
      int c = 0;
      a = sum / 100;
      b = sum / 10 % 10;
      c = sum % 10;

      if (a*a*a + b*b*b + c*c*c == sum) {
        cout << num << endl;
      }
      num++;
    } while (sum < 1000);                   //别忘记加分号 ; 
    system("pause");
    return 0;
  }
  ```
#### for 循环
  作用：满足循环条件，执行循环语句
  语法： for(起始表达式;条件表达式;末尾循环体){循环语句;}
- 示例：
  ```cpp
  int main(){
    for (int i = 0; i < 10; i++){
      cout << i << endl;
    }

    system("pause");
    return 0;
  }
  ```
  详解：
  ```cpp
  using namespace std;

  int main(){
    //for 循环
    //从数字0打印到数字9
    for (int i = 0; i < 10; i++){
      cout << i << endl;
    }
    system("pause");
    return 0;
  }
  ```
  练习案例：敲桌子
  要求：从1开始数到数字100，如果数字个位含有7或者数字十位含有7，再者该数字是7的倍数，我们打印敲桌子，其余数字直接打印输出。
  ```cpp
  using namespace std;
  int main(){
    //先输出1~100数字
    for (int num = 1;num < 101; num++){
      //从100个数字中找出特殊数字，打印敲桌子
      //如果是7的倍数、个位有7、十位有7，视为特殊数字
      if (num % 7 == 0 || num / 10 == 7 || num / 10 == 7  ) {
        cout << "特殊数字：" << num << " 敲桌子" << endl;
      }
      else {
        cout << num << endl;
      }
    }
    system("pause");
    return 0;
  }
  ```
#### 循环嵌套
  作用：在循环体内再嵌套一层循环，解决矩阵式的实际问题
- 示例：
  ```cpp
  using namespace std;
  int main(){

    for (int i = 0; i < 11; i++){
      for (int j = 0; j < 11; j++){
        cout << "* " ;
      }
    }

    system("pause");
    return 0;
  }
  ```
  案例：乘法口诀表
  示例：
  ```cpp
  using namespace std;
  int main(){
    
    for (int i = 1; i < 10; I++){
      for (int j = 1; j <= i; j++){
        cout << i << "*" << j << "=" << i*j << "  ";
      }
      cout << endl;
    }
    system("pause");
    return 0;
  }
  ```
### 跳转语句
#### break 语句
  作用：用于跳出选择结构或者循环结构
  break 使用的地方：
  - 出现在switch条件语句中，作用是终止 case 并跳出 switch
  - 出现在循环语句中，作用是跳出当前的循环语句
  - 出现在嵌套循环中，跳出最近的内层循环语句
- 示例：
  ```cpp
  using namespace std;
  int main(){
    //出现在 switch 语句中
    cout << "请选择副本难度" << endl;
    cout << "1、普通" << endl;
    cout << "2、中等" << endl;
    cout << "3、困难" << endl;

    int select = 0;  //选择难度结果的变量
    cin >> select;   //等待用户输入

    switch (select){
      case 1:
         cout << "您选择的是普通难度" << endl;
         break;
      case 2:
         cout << "您选择的是中等难度" << endl;
         break;
      case 3:
         cout << "您选择的是困难模式" << endl;
         break;
      default :
         break;
    }
    //出现在循环语句中
    //出现在嵌套循环语句中
    system("pause");
    return 0;
  }
  ```
#### continue 语句
  作用：在循环语句中，跳过本次循环中余下尚未执行的语句，继续执行下一次循环
- 示例：
  ```cpp
  using namespace std;
  int main(){
    for (int i = 0; i <= 100; i++){
      //如果是奇数输出，偶数不输出
      if (i % 2 == 0){     //筛选条件，执行到此就不再向下执行，执行下一次循环
        continue;   //break会退出循环，而continue不会
      }
    }
    system("pause");
    return 0;
  }
  ```
#### goto 语句
  作用：可以无条件跳转语句
  语法：goto 标记；
  释义：如果标记的名称存在，执行到goto语句时，会跳转到标记的位置
- 示例：
  ```cpp
  using namespace std;
  int main(){
    cout << "1" << endl;
    cout << "2" << endl;
    goto FLAG;               //跳转到标记

    cout << "3" << endl;
    cout << "4" << endl;

    FLAG:                    //标记
    cout << "5" << endl;

    system("pause");
    return 0;
  }
  ```
## 数组
  概述：数组时一个集合，里面存放了相同类型的数据元素
  特点：
  - 数组中的每个数据元素都是相同的数据类型
  - 数组是由连续的内存位置组成的
### 一维数组
#### 一维数组定义方式
  一维数组定义的三种方式：
  - 数据类型 数组名[数组长度];
  - 数据类型 数组名[数组长度] = {值1,值2,...};
  - 数据类型 数组名[] = {值1,值2,...};
  
- 示例：
  ```cpp
  using namespace std;
  int main(){
    //数据类型 数组名[数组长度];
    int arr[5];
    //给数组中的元素进行赋值
    //数组元素的下标时从0开始索引的
    arr[0] = 10;
    arr[0] = 20;
    arr[0] = 30;
    arr[0] = 40;
    arr[0] = 50;
    //访问数据元素
    cout << arr[0] << endl;

    //数据类型 数组名[数组长度] = {值1,值2,...};
    //如果在初始化数据的时候，没有全部填写完，会用0填补剩余数据
    int arr2[5] = {100,200,300};
    //利用循环输出数组中的元素
    for (int i = 0; i < 5; i++){
      cout << arr2[i] << endl;
    }

    //数据类型 数组名[] = {值1,值2,...};
    //定义数组的时候，必须有初始的长度
    int arr3[] = {90,80,70,60,50,40,30,20,10};
    for (int j = 0; j < 9; j++){
      cout << arr3[j] << endl;
    }

    system("pause");
    return 0;
  }
  ```
  注意1：数组名的命名规范与变量名命名规范一致，不要和变量重名
  注意2：数组中下标是从0开始索引
#### 一维数组数组名
  一维数组名称的用途：
  - 可以统计整个数组在内存中的长度
    ```cpp
    sizeof(arr)
    sizeof(arr[0])
    ```
  - 可以获取数组在内存中的首地址
    ```cpp
    cout << arr << endl;
    ```
- 示例：
  ```cpp
  using namespace std;
  int main(){

    //可以统计整个数组在内存中的长度
    int arr[10] = {1,2,3,4,5,6,7,8,9,10};
    cout << "整个数组占用内存空间为：" << sizeof(arr) << endl;
    cout << "每个元素占用内存空间：" << sizeof(arr[0]) << endl;
    cout << "数组中元素个数为：" << sizeof(arr) / sizeof(arr[0]) << endl;

    //可以获取数组在内存中的首地址
    cout << "数组首地址为：" << arr << endl;    //输出十六进制的内存地址
    cout << "数组首地址为：" << (int)arr << endl; //输出十进制的内存地址
    cout << "数组中第一个元素地址为：" << (int)&arr[0] << endl; 

    //数组名是常量，不可以进行赋值操作

    system("pause");
    return 0;
  }
  ```
  案例：五只小猪称重
  要求：在一个数组中记录五只小猪的体重，找出并打印最重的小猪体重。
  ```cpp
  using namespace std;
  int main(){

    //创建五只小猪体重的数组
    int arr[5] = {300,350,200,400,250};

    //从数组中找到最大值
    int max = 0;    //先认定一个最大值为0

    for (int i = 0; i < 5; i++){
      //如果访问的数组中的元素比 max 的值还要大，更新 max 值
      if (arr[i] > max){
        max = arr[i]; 
      }
    }

    //打印最大值
    cout << "最重的小猪体重为：" << max << endl;

    system("pause");
    return 0;
  }
  ```
  案例2：数组元素逆置
  要求：请声明一个5元素的数组，并且将元素逆置
  ```cpp
  using namespace std;
  int main(){

    //实现数组元素逆置
    //创建数组
    int arr[5] = {1,3,2,5,4};
    cout << "数组逆置前：" << endl;
    for (int i = 0; i <5; i++){
      cout << arr[i] << endl;
    }

    //实现逆置
    //记录起始下标位置
    int start = 0;

    //记录结束下标位置
    int end = sizeof(arr)/sizeof(arr[0]) - 1; //末尾元素下标

    while (start < end) {

    //起始下标与结束下标的元素互换
    int temp = arr[start];
    arr[start] = arr[end];
    arr[end] = temp;

    //起始位置++，结束位置--。下标更新
    start++;
    end--;
    }
    //循环执行操作，直到起止位置 >= 结束位置
    cout << "数组逆置后：" << endl;
    for (int i = 0; i <5; i++){
      cout << arr[i] << endl;
    }

    system("pause");
    return 0;
  }
  ```
#### 冒泡排序
  作用：最常用的排序算法，对数组内元素进行排序
  - 比较相邻的元素，如果第一个比第二个大，就交换他们两个
  - 对每一堆相邻元素做同样的工作，执行完毕后，找到第一个最大值
  - 重复上述步骤，每次比较次数-1，直到不需要比较
  
- 示例：
  ```cpp
  using namespace std;
  int main(){

    //利用冒泡排序实现升序序列
    int arr[9] = {4,2,8,0,5,7,1,3,9};
    cout << "排序前：" << endl;
    for (int i = 0; i < 9; i++){
      cout << arr[i] << " " ;
    }
    cout << endl;

    //开始冒泡排序
    //总共排序轮数为元素个数 -1 
    for (int i = 0; i < (sizeof(arr)/sizeof(arr[0]) - 1); i++){
      //内层循环对比，次数 = 元素个数 - 当前轮数 - 1
      for (int j = 0; j < ((sizeof(arr)/sizeof(arr[0])) - i - 1); j++){
        //如果第一个数字比第二个数字大，交换两个数字
        if (arr[j] > arr[j + 1]){
          //交换代码
          int temp = arr[j];
          arr[j] = arr[j + 1];
          arr[j + 1] = temp;
        }
      }
    }

    //排序后结果
    cout << "排序后：" << endl;
    for (int i = 0; i < 9; i++){
      cout << arr[i] << " " ;
    }
    cout << endl;

    system("pause");
    return 0;
  }
  ```
### 二维数组
  二维数组就是在一维数组上多加一个维度
  二维数组定义方式：
  - 数据类型 数组名[行数][列数];
  - 数据类型 数组名[行数][列数] = {{数据1,数据2} , {数据3,数据4}};
  - 数据类型 数组名[行数][列数] = {数据1,数据2,数据3,数据4};
  - 数据类型 数组名[  ][列数] = {数据1,数据2,数据3,数据4};
  
- 示例：
  ```cpp
  using namespace std;
  int main(){
    
    //数据类型 数组名[行数][列数];
    int arr[2][3];
    arr[0][0] = 1;
    arr[0][1] = 2;
    arr[0][2] = 3;
    arr[1][0] = 4;
    arr[1][1] = 5;
    arr[1][2] = 6;

    //输出二维数组元素值
    for (int i = 0; i < (sizeof(arr)/sizeof(arr[0][0])/3); i++){
      for (int j = 0; j < (sizeof(arr)/sizeof(arr[0][0])/2); j++){
        cout << arr[i][j] << endl;
      }
    }


    //数据类型 数组名[行数][列数] = {{数据1,数据2} , {数据3,数据4}}; 
    int arr2[2][3] = {
      {1,2,3},
      {4,5,6}
    };
    for (int i = 0; i < (sizeof(arr2)/sizeof(arr2[0][0])/3); i++){
      for (int j = 0; j < (sizeof(arr2)/sizeof(arr2[0][0])/2); j++){
        cout << arr2[i][j] << " " ;
      }
      cout << endl;
    }

    //数据类型 数组名[行数][列数] = {数据1,数据2,数据3,数据4};
    int arr3[2][3] = {1,2,3,4,5,6};
    for (int i = 0; i < (sizeof(arr3)/sizeof(arr3[0][0])/3); i++){
      for (int j = 0; j < (sizeof(arr3)/sizeof(arr3[0][0])/2); j++){
        cout << arr3[i][j] << " " ;
      }
      cout << endl;
    }

    //数据类型 数组名[  ][列数] = {数据1,数据2,数据3,数据4};
    int arr4[][3] = {1,2,3,4,5,6};
    for (int i = 0; i < (sizeof(arr4)/sizeof(arr4[0][0])/3); i++){
      for (int j = 0; j < (sizeof(arr4)/sizeof(arr4[0][0])/2); j++){
        cout << arr4[i][j] << " " ;
      }
      cout << endl;
    }

    system("pause");
    return 0;
  }
  ```
#### 二维数组数组名
  - 查看二维数组所占内存空间
  - 获取二维数组首地址
  
- 示例：
  ```cpp
  using namespace std;
  int main(){

    //查看占用内存空间大小
    int arr[2][3] = {
      {1,2,3},
      {4,5,6}
    };
    cout << "二维数组占用内存空间为：" << (sizeof(arr)) << endl;
    cout << "二维数组第一行占用内存空间为：" << sizeof(arr[0]) << endl; //arr[0]表示第一行

    //查看二维数组首地址
    cout << "二维数组首地址为：" << arr << endl;

    system("pause");
    return 0;
  }
  ```
  案例：考试成绩统计
  要求：有三名同学（张三、李四、王五），考试成绩如下表，请分别输出三名同学的总成绩

| 姓名 | 语文 | 数学 | 英语 |
|----|------|------|------|
| 张三 | 100  | 100  | 100  |
| 李四 | 90   | 50   | 100  |
| 王五 | 60   | 70   | 80   |
  
## 函数
- 作用：将一段经常使用的代码封装起来，减少重复代码
- 一个较大的程序，一般分为若干程序块，每个模块实现特定的功能
### 函数的定义
- 返回值类型
- 函数名
- 参数列表
- 函数体语句
- return表达式
- 语法
  ```cpp
  返回值类型  函数名  (参数列表){
    函数体语句
    return表达式
    }


  //示例：
  int add(int num1,int num2){
    int sum = num1 + num2;
    return sum;
  }
  ```
### 函数的调用
- 功能：使用定义好的函数
- 语法：函数名（参数）
- 示例
  ```cpp
  using namespace std;
  int add(int num1,int num2){   //定义中的num1，num2称为形式参数，简称形参
    int sum =  num1 + num2;
    return sum;
  }

  int main(){
    
    int a = 10;
    int b = 20;
    //调用add函数
    int sum = add(a,b);  //调用时的a，b成为实际参数，简称实参
    cout << "sum = " << sum << endl;

    system("pause");
    return 0;
  }
  ```
### 值传递
- 所谓值传递，就是函数调用时实参将参数数值传入给形参
- 值传递时，如果形参发生改变，并不会影响实参
- 示例：
  ```cpp
  using namespace std;
  
  //定义函数，实现两个数字进行交换函数
  //如果函数不需要返回值，声明的时候可以写void
  void swap(int num1.int num2){
    cout << "交换前：" << endl;
    cout << "num1：" << endl;
    cout << "num2" << endl;

    int temp = num1;
    num1 = num2;
    num2 = temp;

    cout << "交换后：" << endl;
    cout << "num1" << endl;
    cout << "num2" << endl;

  }

  int main(){

    int a = 10;
    int b = 20;

    swap(a,b);

    system("pause");
    return 0;
  }
  ``` 
### 函数的常见样式
- 无参无返
- 有参无返
- 无参有返
- 有参有返
- 示例：
  ```cpp
  using namespace std;
  //函数常见样式
  //1、无参无返
  void test01(){
    //void a = 10;  //无类型不可以创建变量，原因是因为无法分配内存
    cout << "this is test01" << endl;
    //test01();函数调用
  }

  //有参无返
  void test02(int a){
    cout << "this is test02 a = " << a << endl;
  }

  //无参有返
  int test03(){
    cout << "this is test03" << endl;
    return 1000;
  }

  //有参有返
  int test04(int a){
    cout << "this is test04 a = " << a << endl;
    return 1000;
  }

  int main(){

    //无参无返的函数调用
    test01();

    //有参无返的函数调用
    test02(100);

    //无参有返的函数调用
    int num = test03();
    cout << "num = " << num << endl;

    //有参有返的函数调用
    int num2 = test04(10000);
    cout << "num2 = " << num2 << endl;
    
    system("pause");
    return 0;
  }
  ```
### 函数的声明
- 作用：告诉编译器函数名称及如何调用函数，函数的实际主体可以单独定义。
- 函数的声明可以多次，但是函数的定义只能有一次
- 示例
  ```cpp
  using namespace std;

  //比较函数，实现两个整型数字进行比较，返回较大的值
  //定义函数
  int max(int a,int b);           //函数的声明

  int max(int a,int b){           
    return a > b ? a : b;         //函数的定义
  }

  int main(){
    
    int a = 10;
    int b = 20;

    cout << max(a,b) << endl;

    system("pause");
    return 0;
  }
  
  ```
### 函数的分文件编写
- 函数的分文件编写
- 函数分文件编写一般有四个步骤
  - 创建后缀名为 .h 的头文件
  - 创建后缀名为 .cpp 的源文件
  - 在头文件中写函数的声明
  - 在源文件中写函数的定义
- 示例：
  ```cpp
   #include<iostream>
   using namespace std;

   //函数的分文件编写
   //实现两个数字进行交换的函数
   //函数的声明
   void swap(int a,int b);

   //函数的定义
   void swap(int a,int b){
    int temp = a;
    a = b;
    b = temp;
    cout << "a = " << a << endl;
    cout << "b = " << b << endl;
   }

   int main(){

    int a = 10;
    int b = 20;
    swap(a,b);

    system("pause");
    return 0;
   }


  //创建后缀名为 .h 的头文件
  //创建后缀名为 .cpp 的源文件
  //在头文件中写函数的声明
  //在源文件中写函数的定义
  

  //swap.h文件
  #include<iostream>
  using namespace std;
  //实现两个数字交换的函数声明
  void swap(int a,int b);

  //swap.cpp文件
  #include "swap.h"
  
  ```
## 指针
- 作用：可以通过指针间接访问内存
  - 内存编号是从0开始记录的，一般用十六进制数字表示
  - 可以利用指针变量保存地址
### 指针变量的定义和使用
- 示例：
  ```cpp
  using namespace std;
  int main(){

    //定义指针
    int a = 10;

    //指针定义的语法：数据类型 * 指针变量名
    int * p;

    //让指针记录变量 a 的地址
    p = &a;
    cout << "a的地址为：" << &a << endl;
    cout << "a的地址为：" << p << endl;

    //使用指针
    //可以通过解引用的方式来找到指针指向的内存
    //指针前加 * 代表解引用，找到指针指向的内存中的数据
    *p = 1000;
    cout << "a = " << a << endl;
    cout << "*p = " << *p << endl;

    system("pause");
    return 0;
  }
  ```
### 指针所占内存空间
- 指针也是一种数据类型。
- 示例：
  ```cpp
  using namespace std;
  int main(){

    int a = 10;

    int * p;
    p = &a;  //指针指向数据a的地址
    //在32位操作系统下，占用4个字节空间
    //在64位操作系统下，占用8个字节空间
    
    cout << "sizeof(int *) = " << sizeof(p) << endl;
    cout << *p << endl;  //解引用
    cout << sizeof(p) << endl;
    cout << sizeof(char *) << endl;
    cout << sizeof(flot *) << endl;
    cout << sizeof(double *) << endl;

    system("pause");
    return 0;
  }
  ```
### 空指针和野指针
- 空指针：指针变量指向内存中编号为0的空间
- 用途：初始化指针变量
- 注意：空指针指向的内存是不可以访问的
- 示例：
  ```cpp
  using namespace std;
  int main(){
    //空指针用于给指针变量进行初始化
    int * p = NULL;
    //空指针是不可以进行访问的 
    //0~255之间的内存编号是系统占用的，因此不可以访问
    *p = 1000;  //报错：写入权限冲突
    system("pause");
    return 0;
  }
  ```
- 野指针：指针变量指向非法的内存空间
- 示例：
  ```cpp
  using namespace std;
  int main(){
    //野指针变量p指向内存地址编号为0x1100的空间
    //在程序中，尽量避免出现野指针
    int * p = (int *)0x1100;

    //访问野指针报错
    cout << *p << endl;

    system("pause");
    return 0;
  }
  ```
### const修饰指针
- const 修饰指针有三种情况：
  - const修饰指针---常量指针
  - const修饰常量---指针常量
  - const即修饰指针，又修饰常量
- 示例：
  ```cpp
  using namespace std;
  int main(){

    int a = 10;
    int b = 10;

    //const修饰的是指针，指针指向可以改，指针指向的值不可以更改
    //常量指针
    const int * p1 = &a;
    p1 = &b;  //正确
    *p1 = 100;  //错误

    //const修饰的是常量，指针指向不可以改，指针指向的值可以改
    //指针常量
    int * const p2 = &a;
    p2 = &b;  //错误
    *p2 = 20;  //正确

    //const即修饰指针又修饰常量，指针的指向和指针指向的值都不可以改
    const int * const p3 = &a;
    *p3 = 20;  //错误
    p3 = &b;   //错误
    *p3 = 10;  //正确


    system("pause");
    return 0;
  }
  ```
### 指针和数组
- 作用：利用指针访问数组中元素
- 示例：
  ```cpp
  using namespace std;
  int main(){

    //指针和数组
    //利用指针访问数组中的元素

    int arr[10] = {1,2,3,4,5,6,7,8,9,10};
    cout << "第一个元素为：" << arr[0] << endl;

    int * p = arr; //arr就是数组的首地址

    cout << "利用指针访问第一个元素：" << *p << endl;

    p++;  //让指针向后偏移4个字节 
    cout << "利用指针访问第二个元素：" << *p << endl;

    cout << "利用指针遍历数组" << endl;
    int * p2 = arr;
    for (int i = 0; i < 10; i++){
      cout << arr[i] << endl;
      cout << *p2 << endl;
      p2++;
    }

    system("pause");
    return 0;
  }
  ```
### 指针和函数
- 作用：利用指针作函数参数，可以修改实参的值
- 示例：
  ```cpp
  using namespace std;

  //实现两个数字进行交换
  void swap01(int a,int b){
    int temp = a;
    a = b;
    b = temp;

    cout << "swap01 a = " << a << endl;
    cout << "swap01 b = " << b << endl;
  }

  void swap02(int *p1,int *p2){
    int temp = *p1;
    *p1 = *p2;
    *p2 = temp;
  }

  int main(){

    //指针和函数
    //值传递
    int a = 10;
    int b = 20;
    swap01(a,b);

    //地址传递
    //如果是地址传递，可以修饰实参
    swap02(&a,&b);   

    cout << "a = " << a << endl;
    cout << "b = " << b << endl;

    //

    system("pause");
    return 0;
  }
  ```
### 指针、数组、函数
- 案例：封装一个函数，利用冒泡排序，实现对整型数组的升序排序
- 例如：int arr[10] = {4,3,6,9,1,2,10,8,7,5};
- 示例：
  ```cpp
  //冒泡排序函数：参数1是数组的首地址，参数2是数组的长度 
  void bubbleSort(int * arr,int len)   //int * arr 也可以写作int arr[]
  {
    for (int i = 0; i < len; i++){
      for (int j = 0; j < len - 1 -i; j++){
        if (arr[j] > arr[j+1]){
          int temp = arr[j];
          arr[j] = arr[j + 1];
          arr[j + 1] = temp;
        }
      }
    }
  }

  //打印数组
  void printArray(int * arr, int len)
  {
    for (int i = 0; i < len; i++){
      cout << arr[i] << endl;
    }
  }

  int main(){

    //创建一个数组
    int arr[10] = {4,3,6,9,1,2,10,8,7,5};

    //数组长度
    int len = sizeof(arr) / sizeof(arr[0]);

    //创建函数，实现冒泡排序
    bubbleSort(arr, len)

    //打印排序后的数组
    printArray(arr, len);

    system("pause");
    return 0;
  }
  

  ```
## 结构体
- 概念：结构体属于用户自定义的数据类型，允许用户存储不同的数据类型
### 结构体定义和使用
- 语法： struct 结构体名 {结构体成员列表};
- 通过结构体创建变量的方式有三种：
  - struct 结构体名 变量名
  - struct 结构体名 变量名 = {成员1值，成员2值...};
  - 定义结构体时顺便创建变量
- 注意：
  - 定义结构体时的关键字时struct，不可省略
  - 创建结构体变量时，关键字struct可以省略
  - 结构体变量利用操作符" . "访问成员
- 示例：
  ```cpp
  using namespace std;
  #include <string>

  //创建学生数据类型：学生包括（姓名、年龄、分数）
  //自定义数据类型：一些类型集合组成的一个类型
  struct Student{
    //成员列表
    //姓名
    string name;
    //年龄
    int age;
    //分数
    int score;
  }s3;         //在定义结构体时顺便创建结构体变量

  int main(){

    //通过学生类型创建具体学生
    //struct Student s1;
      //struct 关键字可以省略
      struct Student s1;
      //给s1属性赋值，通过 . 访问结构体变量中的属性
      s1.name = "张三";
      s1.age = 18;
      s1.score = 100;
      cout << "姓名：" << s1.name << " 年龄：" << s1.age << " 分数：" << s1.score << endl;

    //struct Student S2 = {...};
    struct Student s2 = {"李四", 19 ,80};
    cout << "姓名：" << s2.name << " 年龄：" << s2.age << " 分数：" << s2.score << endl;

    //在定义结构体时顺便创建结构体变量
    s3.name = "王五";
    s3.age = 19;
    s3.score = 90;
    cout << "姓名：" << s3.name << " 年龄：" << s3.age << " 分数：" << s3.score << endl;

    system("pause");
    return 0;
  }
  ```
### 结构体数组
- 作用：将自定义的结构体放入到数组中方便维护
- 语法：struct 结构体名 数组名[元素个数] = {{},{},...{}};
- 示例：
  ```cpp
  #include <string>
  using namespace std;

  //结构体定义
  struct student{
    //成员列表
    string name;  //姓名
    int age;      //年龄
    int score;    //分数
  }; 

  int main(){

    //结构体数组
    struct student stuArray[3] = {
      {"张三",18,80},
      {"李四",19,90},
      {"王五",18,100}
    };

    //给结构体数组中的元素赋值
    stuArray[2].name = "赵六";
    stuArray[2].age = 17;
    stuArray[2].score = 95;

    stuArray[2] = {"钱七",18,85};

    //遍历结构体数组
    for (int i = 0; i < 3; i++){
      cout << "姓名：" << stuArray[i].name
           << "年龄：" << stuArray[i].age 
           << "分数：" << stuArray[i].score << endl;
    }

    system("pause");
    return 0;
  }
  ```
### 结构体指针
- 作用：通过指针访问结构体中的成员
  - 利用操作符 -> 可以通过结构体指针访问结构体属性
- 示例：
  ```cpp
  #include <string>
  using namespace std;

  //结构体定义
  struct student{
    //成员列表
    string name;  //姓名
    int age;      //年龄
    int score;    //分数
  };

  int main(){

    //创建学生结构体变量
    struct student s = {"张三",18,100};

    //通过指针指向结构体变量
    struct student * p = &s;

    //通过指针访问结构体变量中的数据
    //通过结构体指针 访问结构体中的属性，需要利用" -> "
    cout << "姓名：" << p->name
         << "年龄：" << p->age
         << "分数：" << p->score << endl;

    system("pause");
    return 0;
  }
  ```
### 结构体嵌套结构体
- 作用：结构体中的成员可以是另一个结构体
- 例如：每个老师辅导一个学员，一个老师的结构体中，记录一个学生的结构体
- 示例：
  ```cpp
  #include <string>
  using namespace std;

  //学生结构体定义
  struct student{
    //成员列表
    string name;  //姓名
    int age;      //年龄
    int score;    //分数
  };

  //老师结构体定义
  struct teacher{
    //成员列表
    int id;  //职工编号
    string name;  //教师姓名
    int age;  //教师年龄
    struct student stu;  //子结构体  学生
  };

  int main(){

    //结构体嵌套结构体
    //创建老师
    teacher t;
    t.id = 10000;
    t.name = "老王";
    t.age = 50;
    t.stu.name = "小王";
    t.stu.age = 20;
    t.stu.score = 60;
    cout << "老师编号：" << t.id
         << "老师姓名：" << t.name
         << "老师年龄：" << t.age
         << "老师辅导的学生姓名：" << t.stu.name
         << "学生年龄：" << t.stu.age
         << "学生分数：" << t.stu.score << endl;

    system("pause");
    return 0;
  }
  ```
### 结构体做函数参数
- 作用：将结构体作为参数向函数中传递
- 传递方式有两种：
  - 值传递
  - 地址传递
- 示例：
  ```cpp
  using namespace std;
  #include <string>

  //学生结构体定义
  struct student{
    //成员列表
    string name;  //姓名
    int age;      //年龄
    int score;    //分数
  };

  void printStudent(student stu){
    stu.age =28;
    cout << "子函数中 姓名：" << stu.name 
         << "年龄：" << stu.age
         << "分数：" << stu.score
  }

  //打印学生信息函数
  //值传递
  void printStudent1(struct student s){
    cout << "子函数中打印 姓名：" << s.name << "年龄：" << s.age << "分数：" << s.score << endl;
  }
  //地址传递
  void printStudent2(struct student * p){
    cout << "子函数2中打印 姓名：" << p->name << "年龄：" << p->age << "分数：" << p->score << endl;
  }

  int main(){

    //结构体做函数参数
    //将学生传入到一个参数中，打印学生身上的所有信息

    //创建结构体变量
    struct student s;
    s.name = "张三"；
    s.age = 20;
    s.score = 85;

    //值传递
    printStudent1(s)

    //地址传递
    printStudent2(&s);
    //cout << "main函数中打印 姓名：" << s.name << "年龄：" << s.age << "分数：" << s.score << endl;

    system("pause");
    return 0;
  }
  ```
### 结构体中 const 使用场景
- 作用：用const来防止误操作
- 示例：
  ```cpp
  #include <string>
  using namespace std;

  //学生结构体定义
  struct student{
    //成员列表
    string name;  //姓名
    int age;      //年龄
    int score;    //分数
  };

  //const使用场景
  //将函数中的形参改成指针，可以减少内存空间，而且不会复制新的副本出来
  void printStudent(const student * stu)  //加const防止函数体中的误操作
  {
    //stu->age = 100; //操作失败，因为加了const修饰
    cout << "子姓名：" << stu->name << "年龄：" << stu->age << "分数：" << stu->score << endl;
  }


  int main(){

    //创建结构体变量
    struct student s = { "张三",15,70};

    //通过函数打印结构体变量信息

    system("pause");
    return 0;
  }

  //算法技巧
  void allocateSpace(struct Teacher tArray[] , int len){
    string nameSeed = "ABCDE";
    for (int i = 0; i < len; i++){
      tArray[i].tName = "Teacher_";
      tArray[i].tname += nameSeed[i];
    }
  }
  ```
## C++核心编程
### 内存分区模型
- C++程序在执行时，将内存大方向划分为4个区域
  - 代码区：存放函数体的二进制代码，由操作系统进行管理的
  - 全局区：存放全局变量和静态变量以及常量
  - 栈区：由编译器自动分配释放，存放函数的参数值，局部变量等
  - 堆区：由程序员分配和释放，若程序员不释放，程序结束时由操作系统回收
- 内存四区意义：
  不同区域存放的数据，赋予不同的生命周期，给我们更大的灵活编程
#### 程序运行前
- 在程序编译后，生成了exe可执行程序，未执行该程序前分为两个区域
- 代码区：
  - 存放CPU执行的机器指令
  - 代码区是共享的，共享的目的是对于频繁被执行的程序，只需要在内存中有一份代码即可
  - 代码区是只读的，使其只读的原因是防止程序意外的修改了它的指令
- 全局区：
  - 全局变量和静态变量存放在此
  - 全局区还包含了常量区，字符串常量和其他常量也存放在此
  - 该区域的数据在程序结束后由操作系统释放
  - 示例:
    ```cpp
    using namespace std;

    //创建全局变量
    int b = 10;    //全局变量是指不在函数体内的变量

    //const修饰的全局变量
    const int c_g_a = 10;

    int main(){

      //创建普通局部变量
      int a = 10;

      //静态变量  在普通变量前面加static,属于静态变量
      static int s_a = 10;

      //常量
      //字符串常量
      cout << (int)&"hello world" << endl;

      //const修饰的变量
      //const修饰的全局变量和const修饰的局部变量

      const int c_l_a = 10  //const修饰的局部变量


      system("pause");
      return 0;
    }
    ```
- 总结：
  - C++中在程序运行前分为全局区和代码区
  - 代码区特点是共享和只读
  - 全局区中存放全局变量、静态变量、常量
  - 常量区中存放const修饰的全局变量和字符串常量
#### 程序运行后
- 栈区
  - 由编译器自动分配释放，存在函数的参数值，局部变量等
  - 注意事项：不要返回局部变量的地址，栈区开辟的数据由编译器自动释放
  - 示例：
    ```cpp
    using namespace std;

    //栈区数据注意事项   --- 不要返回局部变量的地址
    //栈区的数据由编译器管理开辟和释放

    int * func()   //形参数据也会放在栈区
    {
      int a = 10;  //局部变量  存放在栈区，栈区的数据在函数执行完后自动释放
      return &a;   //返回局部变量的地址
    }

    int main(){

      //接收func函数的返回值
      int * p = func();
      cout << *p << endl;  //第一次可以打印正确的数字，是因为编译器做了保留
      cout << *p << endl;  //第二次这个数据就不保留了

      system("pause");
      return 0;
    }
    ```
- 堆区
  - 由程序员分配释放，若程序员不释放，程序结束后由操作系统回收
  - 在C++中主要利用new在堆区开辟内存
  - 示例：
    ```cpp
    using namespace std;

    int * func (){
      //利用new关键字，可以将数据开辟到堆区
      //指针本质也是局部变量，放在栈上，指针保存的数据是放在堆区
      int * p = new int(10);
      return p;
    }

    int main(){

      //在堆区开辟数据
      int * p = func();
      cout << *p << endl;
       
      system("pause");
      return 0;
    }
    ```
#### new操作符
- 堆区开辟的数据，由程序员手动开辟，手动释放，释放利用操作符 delete
- 语法： new 数据类型
- 利用 new 创建的数据，会返回该数据对应的类型的指针
- 示例：
  ```cpp
  using namespace std;
  //new的基本语法
  int * func(){
    //在堆区创建整型数据
    //new返回的是该数据类型的指针
    int * p = new int(10);
    return p;
  }
  //在堆区利用new开辟数组
  void test01(){
    int * p = func();
    cout << *p << endl;
    //堆区的数据，由程序员管理开辟，程序员管理释放
    //如果想释放堆区的数据，利用关键字 delete
    delete p;
    cout << *p << endl;  //错误：引发异常，读取访问出错。因为内存已经被释放，再次访问就是非法操作，会报错
  }

  //在堆区利用new开辟数组
  void test02(){
    //创建10整型数组的数组，在堆区
    int * arr = new int[10];   //10代表数组有10个元素

    for (i = 0; i < 10; i++){
      arr[i] = i + 100;  //给10个元素赋值  100~109
    }
    for (int i = 0; i < 10; i++){
      cout << arr[i] << endl;
    }

    //释放堆区数组
    //释放数组的时候，要加[]才可以
    delete [] arr;
  }
  int main(){

    //调用test02()
    test02();

    system("pause");
    return 0;
  }
  ```
### 引用
- 作用：给变量起别名
- 语法：数据类型 &别名 = 原名
- 示例：
  ```cpp
  using namespace std;
  int main(){

    //引用的基本语法
    //数据类型 &别名 = 原名
    int a = 10;

    //创建引用
    int &b = a;

    cout << "a = " << a << endl;
    cout << "b = " << b << endl;

    b = 100;

    cout << "a = " << a << endl;
    cout << "b = " << b << endl;

    system("pause");
    return 0;
  }
  ```
#### 引用注意事项
- 引用必须初始化
- 引用在初始化后，不可以改变
- 示例：
  ```cpp
  using namespace std;
  int main(){

    int a = 10;
    int b = 10;
    //int &c;   //错误，引用必须初始化
    int &c = a; //一旦初始化后，就不可以更改
    c = b; //这是赋值操作，不是更改引用

    cout << "a = " << a << endl;
    cout << "b = " << b << endl;
    cout << "c = " << c << endl;

    system("pause");
    return 0;
  }
  ```
#### 引用做函数参数
- 作用：函数传参时，可以利用引用的技术让形参修饰实参
- 优点：可以简化指针修改实参
- 示例：
  ```cpp
  using namespace std;

  //值传递
  void mySwap01(int a, int b){
    int temp = a;
    a = b;
    b = temp;
    cout << "mySwap01 a = " << a << endl;
    cout << "mySwap01 b = " << b << endl;
  }

  //地址传递
  void mySwap02(int * a; int * b){
    int temp = *a;
    *a = *b;
    *b = temp;
    cout << "mySwap02 a = " << a << endl;
    cout << "mySwap02 b = " << b << endl;
  }

  //引用传递
  void mySwap03(int &a, int &b){
    int temp = a;
    a = b;
    b = temp;
  }

  int main(){

    int a = 10;
    int b = 20;

    mySwap01(a,b);        //值传递，形参不会修饰实参

    mySwap02(&a,&b);      //地址传递，形参会修饰实参

    mySwap03(a,b);        //引用传递，形参会修饰实参

    cout << "a = " << a << endl;
    cout << "b = " << b << endl;

    system("pause");
    return 0;
  }
  ```
- 总结：通过引用参数产生的效果同按地址传递是一样的。引用的语法更清楚简单
#### 引用做函数返回值
- 作用：引用是可以作为函数的返回值存在的
- 注意：不要返回局部变量引用
- 用法：函数调用作为左值
- 示例：
  ```cpp
  using namespace std;

  //引用做函数的返回值
  //不要返回局部变量的引用
  int& test01(){
    int a = 10; //局部变量，存放在四区中的栈区
    return a；
  }

  //函数的调用可以作为左值
  int& test02(){
    static int a = 10;  //静态变量存放在全局区，全局区上的数据在程序结束后系统释放
    return a;
  }

  int main(){

    int &ref = test01();
    cout << "ref = " << ref << endl;   //第一次结果准确，是因为编译器做了保留
    cout << "ref = " << ref << endl;  //第二次结果错误，因为a的内存已经释放

    int &ref2 = test02();
    cout << "ref2 = " << ref2 << endl;
    cout << "ref2 = " << ref2 << endl;
    
    test02() = 1000;  //如果函数的返回值是引用，这个函数调用可以作为左值

    cout << "ref2 = " << ref2 << endl;
    cout << "ref2 = " << ref2 << endl;

    system("pause");
    return 0;
  }
  ```
#### 引用的本质
- 本质：有用的本质再C++内部实现是一个指针常量
- 示例：
  ```cpp
  using namespace std;
  
  //发现是引用，转换为int * const ref = &a;
  void func(int& ref){
    ref = 100;  //ref是引用，转换为*ref = 100;
  }
  int main(){

    int a = 10;
    //自动转换为 int * const ref = &a;指针常量是指针指向不可改，也说明为什么引用不可更改
    int& ref = a;
    ref = 20;  //内部发现ref是引用，自动帮我们转换为：*ref = 20;
    cout << "a : " << a << endl;
    cout << "ref: " << ref << endl;
    
    system("pause");
    return 0;
  }
  ```
#### 常量引用
- 作用：常量引用主要用来修饰形参，防止误操作
- 再函数形参列表中，可以加 const 修饰形参，防止形参改变实参
- 示例：
  ```cpp
  using namespace std;
  //引用使用的场景，通常用来修饰形参
  void showValue(const int& v){
    //v += 10;
    cout << v << endl;
  }

  int main(){

    //常量引用
    //使用场景：用来修饰形参，防止误操作

    int a = 10;
    //int & ref = 10;  引用本身需要一个合法的内存空间，因此这行错误

    const int & ref = 10;  
    //加入const就可以了，编译器优化代码，int temp = 10; const int & ref = temp;

    //ref = 20;    //加入const之后变为只读，不可以修改。
    showValue(a);
    cout << ref << endl;

    system("pause");
    return 0;
  }
  ```
### 函数提高
#### 函数默认参数
- 在C++中，函数的形参列表中的形参是可以有默认值的。
- 语法：返回值类型 函数名 （参数 = 默认值）{}
- 示例：
  ```cpp
  using namespace std;

  //函数默认参数
  //如果我们传入数据，就用自己的数据，如果没有，那么用默认值
  int func(int a, int b = 10; int c = 10){
    return a + b + c;
  }

  //1、如果某个位置参数有默认值，那么从这个位置往后，从左往右，必须都要有默认值
  //2、如果函数声明有默认值，函数实现的时候就不能有默认参数
  
  int func2(int a = 10, int b = 10);
  int func2(int a, int b){
    return a + b;
  }

  int main(){
    system("pause");
    return 0;
  }
  ```
#### 函数占位参数
- C++中函数的形参列表里可以有占位参数，用来做占位，调用函数时必须填补该位置
- 语法：返回值类型 函数名（数据类型）{}
- 示例：
  ```cpp
  using namespace std;

  //函数占位参数，占位参数也可以有默认参数
  void func(int a, int){
    cout << "this is func" << endl;
  }

  int main(){

    func(10,10);//占位参数必须填补
    system("pause");
    return 0;
  }
  ```
#### 函数重载
##### 函数重载概述
- 作用：函数名可以相同，提高复用性
- 函数重载满足条件：
  - 同一个作用域下
  - 函数名称相同
  - 函数参数类型不同或者个数不同或者顺序不同
- 注意：函数的返回值不可以作为函数重载的条件
- 示例：
  ```cpp
  using namespace std;

  //函数重载需要函数都在同一个作用域下
  void func(){ 
    cout << "func的调用" << endl;
  }

  void func(int a){ 
    cout << "func(int a)的调用" << endl;
  }

  void func(double a){ 
    cout << "func(double a)的调用" << endl;
  }

  int main(){

    func();
    func(10);
    func(3.14)

    system("pause");
    return 0;
  }
  ```
##### 函数重载注意事项
- 引用作为重载条件
- 函数重载碰到函数默认参数
- 示例：
  ```cpp
  using namespace std;

  //引用作为重载条件
  void func(int &a){      //int &a = 10;  不合法
    cout << "func (int &a)" << endl;
  }

  void func(const int &a){    //const int &a = 10;
    cout << "func (const int &a)" << endl;
  }

  //函数重载碰到函数默认参数
  void func2(int a, int b = 10){      
    cout << "func2 (int a, int b)" << endl;
  }

  void func2(int a){      
    cout << "func2 (int a)" << endl;
  }

  int main(){

    //int a = 10;
    //func(a);

    func(10);

    //func2(10);  //当函数重载碰到默认参数，出现二义性，报错，尽量避免这种情况

    system("pause");
    return 0;
  }
  ```
### 类和对象
- C++面向对象的三大特性：封装、继承、多态
- C++认为万事万物都皆为对象，对象上有其属性和行为
- 例如：
  ```cpp
  人可以作为对象，属性有姓名、年龄、身高、体重...,行为有走、跑、跳、吃饭、唱歌...
  车也可以作为对象，属性有轮胎、方向盘、车灯...，行为有载人、放音乐、开空调...
  具有相同性质的对象，我们可以抽象称为类，人属于人类，车属于车类
  ```
#### 封装
##### 封装的意义
- 封装是C++面向对象三大特性之一
- 封装的意义
  - 将属性和行为作为一个整体，表现生活中的事务
  - 将属性和行为加以权限控制
- 封装意义一：
  ```cpp
  在设计类的时候，属性和行为写在一起，表现事物
  ```
  - 语法：class 类名{ 访问权限： 属性 / 行为}；
  - 示例1：设计一个圆类，求圆的周长
    ```cpp
    using namespace std;

    //圆周率
    const double PI = 3.14

    //设计一个圆类，求圆的周长
    //class代表设计一个类，类后面紧跟着的就是类名称
    class Circle{

    //访问权限
    //公共权限
    public:
    //属性
    //半径
    int m_r;
    //行为
    //获取圆的周长
    double calculateZC(){
      return 2 * PI * m_r;
    }
    };

    int main(){

    //通过圆类 创建具体的圆（对象）
    //实例化  （通过一个类，创建一个对象的过程）
    Circle c1;

    //给圆对象的属性进行赋值
    c1.m_r = 10;

    cout << "圆的周长为：" << c1.calculateZC() << endl;

    system("pause");
    return 0;
    }

    //封装的意义
    //将属性和行为作为一个整体，用来表现生活中的事物
    ```
  - 示例2：
    ```cpp
    using namespace std;
    #include <string>;

    //学生类
    class Student{

    //权限
    public:

    //类中的属性和行为，我们统一称为成员
    //属性  成员属性 成员变量
    //行为  成员函数  成员方法

    //属性
    string m_Name;
    int m_ID;

    //行为
    void showStudent(){
      cout << "姓名" << m_Name << "学号" << m_ID << endl;
    }

    //给姓名赋值

    void setName(string name){
      m_Name = name;
    }

    }

    int main(){

    //创建一个具体学生   实例化对象
    Student s1;

    //给s1对象进行属性赋值操作
    //s1.m_Name = "张三"；
    s1.setName("张三");
    s1.m_ID = 1;

    //现实学生信息
    s1.showStudent();

    system("pause");
    return 0;
    }
    ```
- 封装意义二：
  - 类在设计时，可以把属性和行为放在不同的权限下，加以控制
  - 访问权限有三种
    - public    公共权限
    - protected 保护权限
    - private   私有权限
  - 示例：
    ```cpp
    using namespace std;

    //访问权限
    //公共权限 public         成员类内可以访问  类外可以访问
    //保护权限 protected      成员类内可以访问  类外不可以访问  继承父子关系可以访问
    //私有权限 private        成员类内可以访问  类外不可以访问  继承父子关系不可以访问
    
    class Person{

      public:
      //公共权限
      string m_name;  //姓名

      protected:
      //保护权限
      string m_Car;  //汽车

      private:
      //私有权限
      int m_Password;  //银行卡密码

      public:
      void func(string a, string b. int c){
        m_Name = a;
        m_Car = b;
        m_Password = c;
      }
    };
    int main(){

      //实例化一个具体对象
      Person p1;
      p1.m_Name = "李四";
      p1.m_Car = "奔驰"   //报错，保护权限内容，在类外访问不到
      p1.m_Password = 123;  //报错，私有权限内容，在类外访问不到

      p1.func("张三", "拖拉机", 123456);  //可以访问，因为两个私有权限在public共有权限套用下,属于类内

      system("pause");
      return 0;
    }
    ```
##### struct和class区别
- 在C++中struct和class唯一的区别就在于默认的访问权限不同
- 区别：
  - struct默认权限为共有
  - class默认权限为私有
- 示例：
  ```cpp
  class c1{
    int m_A;  //默认是私有权限  private
  }；
  struct c2{
    int m_A;  //默认是公有权限  public
  };
  ```
##### 成员属性设置为私有
- 优点1：将所有成员属性设置为私有，可以主机控制读写权限
- 优点2：对于写权限，我们可以检测数据的有效性
- 示例：
  ```cpp
  using namespace std;
  #include <string>
  //成员属性设置为私有
  //1、可以主机控制读写权限
  //2、对于写权限可以检测数据的有效性

  //设计人类
  class Person{

    public:

    //设置姓名 
    void setName(string name){
      m_Name = name;
    }

    //获取姓名
    string getName(){
      return m_Name;   //不能直接反悔name，因为name只在setName里有生存周期；
    }

    //获取年龄  只读权限
    int getAge(){
      m_Age = 0;   //初始化为0岁
      return m_Age;
    }
    //设置年龄  可写（范围0-150）
    void setAge(int Age){
      if (age < 0 || age > 150){
        m_Age = 0;
        cout << "输入年龄有误！" << endl;
        return;
      }
      m_Age = Age;
    }

    //设置情人  只写权限
    void setLover(string lover){
      m_Lover = lover;
    }

    private:

    //姓名  可读可写
    string m_Name;

    //年龄  只读
    int m_Age;

    //情人  只写
    string m_Lover;

  };

  int main(){

    Person p;
    p.setName("张三");   //正确，可以写

    cout << "姓名为：" << p.getName << endl;  //正确，可以读

    p.setAge(18);  //正确，可以写
    cout << "年龄为：" << p.getAge << endl;  //正确，可以读

    //设置情人
    p.setLover("苍井");  //正确，可以写
    cout << "情人为：" << p.getLover << endl;  //错误，不可以读

    system("pause");
    return 0;
  }
  ```
- 案例1：设计立方体类
  - 设计立方体类
  - 求出立方体的面积和体积
  - 分别用全局函数和成员函数判断两个立方体是否相等
  - m_L：长、m_W：宽、m_H：高
- 示例：
  ```cpp
  using namespace std;
  
  //创建立方体类
  class Cub{

    public:

    //行为
    //获取立方体面积
    int calculateS(){
      return 2 * m_L * m_W + 2 * m_W * m_H + 2 * m_L * m_H;
    }

    //获取立方体体积
    int calculateV(){
      return m_L * m_W * m_H;
    }

    //设置获取长宽高
    //设置长
    void setL(int L){
      m_L = L;
    }

    //获取长
    int getL(){
      return m_L;
    }

    //设置高
    void setH(int H){
      m_H = H;
    }

    //获取高
    int getLH(){
      return m_H;
    }

    //设置宽
    void setLW(int W){
      m_W = W;
    }

    //获取宽
    int getW(){
      return m_W;
    }

    //利用成员函数判断两个立方体是否相等
    bool isSnameByClass(Cube &c){
      if(m_L == c.getL() && m_W == c.getW() && m_H == c.getH()){
         return true;
      }
      return false;
    }

    //属性 设置为私有 
    private:
    int m_L;  //长
    int m_W;  //宽
    int m_H;  //高

  };

  //利用全局函数判断，两个立方体是否相等
  bool isSame(Cube &c1 , Cube &c2){        //利用 & 引用的方式去除数据缓存步骤
    if(c1.getL() == c2.getL() && c1.getW() == c2.getW() && c1.getH() == c2.getH()){
      return true;
    }
    return false;
  }

  int main(){

    //创建立方体对象
    Cube c1;
    c1.setL(10);
    c1.setW(10);
    c1.setH(10);

    cout << "c1的面积为：" << c1.calculateS() << endl; 
    cout << "c1的体积为：" << c1.calculateV() << endl; 

    //创建第二个立方体
    Cube c2;
    c2.setL(10);
    c2.setW(10);
    c2.setH(10);

    cout << "c2的面积为：" << c2.calculateS() << endl; 
    cout << "c2的体积为：" << c2.calculateV() << endl;
    
    //利用全局函数判断
    bool ret = isSame(c1,c2);
    if(ret){
      cout << "c1和c2是相等的" << endl;
    }else{
      cout << "c1和c2是不相等的" << endl;
    }

    //利用成员函数判断
    ret = c1.isSameByClass(c2);
    if(ret){
      cout << "成员判断：c1和c2是相等的" << endl;
    }else{
      cout << "成员判断c1和c2是不相等的" << endl;
    }

    system("pause");
    return 0;
  }
  ```
- 练习案例2：点和圆的关系
  - 设计一个圆形类（Circle）和一个点类（Point），计算点和圆的关系
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;

  //点和圆关系案例
  //点类
  class Point {
  public:
    //设置x
    void setX(int x) {
        m_X = x;
    }
    //获取x
    int getX() {
        return m_X;
    }
    //设置y
    void setY(int y) {
        m_X = y;
    }
    //获取y
    int getY() {
        return m_Y;
    }
  private:
    int m_X;
    int m_Y;
  };

  //圆类
  class Circle {
  public:
  //设置半径
    void setR(int r) {
        m_R = r;
    }
    //获取半径
    int getR() {
        return m_R;
    }
    //设置圆心
    void setCenter(Point center) {
        m_Center = center;
    }
    //获取圆心
    Point getCenter() {
        return m_Center;
    }
  private:
    int m_R;  //半径
    Point m_Center;  //圆心
  };

  //判断点和圆关系
  void inInCircle(Circle& c, Point& p) {
    //计算两点之间的平方
    int distance =
        (c.getCenter().getX() - p.getX()) * (c.getCenter().getX() - p.getX()) +
        (c.getCenter().getY() - p.getY()) * (c.getCenter().getY() - p.getY());

    //计算半径的平方
    int rDistance = c.getR() * c.getR();

    //判断关系
    if (distance == rDistance) {
        cout << "点在圆上" << endl;
    }
    else if (distance > rDistance) {
        cout << "点在圆外" << endl;
    }
    else
    {
        cout << " 点在圆内" << endl;
    }
  }
  int main()
  {
    //创建圆
    Circle c;
    c.setR(10);
    Point center;
    center.setX(10);
    center.setY(0);
    c.setCenter(center);
    //创建点
    Point p;
    p.setX(10);
    p.setY(10);
    //判断关系
    inInCircle(c, p);

    system("pause");
    return 0;
  }
  ```
#### 对象的初始化和清理
- 生活中我们买的电子产品都基本会有出厂设置，在某一天我们不用时候也会删除一些自己信息数据保证安全
- 在C++中的面向对象来源于生活，每个对象也都会有初始设置以及对象销毁前的清理数据的设置
##### 构造函数和析构函数
- 对象的初始化和清理也是两个非常重要的安全问题
  - 一个对象或者变量没有初始状态，对其使用后果是未知
  - 同样的使用完一个对象或变量，没有及时清理，也会造成一定的安全问题
- C++利用了构造函数和析构函数解决上述问题，这两个函数将会被编译器自动调用，完成对象初始化和清理工作。
- 对象的初始化和清理工作是编译器强制要我们做的事情，因此如果我们不提供构造和析构，编译器会提供
- 编译器提供的构造函数和析构函数是空实现。
  - 构造函数：主要作用在于创建对象时为对象的成员属性赋值，构造函数由编译器自动调用，无需手动调用。
  - 析构函数：主要作用在于对象销毁前系统自动调用，执行一些清理工作。 
- 构造函数语法：类名(){}
  -  构造函数没有返回值也不写void
  -  函数名称与类名相同
  -  构造函数可以有参数，因此可以发生重载
  -  程序在调用对象时候会自动调用构造，无需手动调用，而且只会调用一次
- 析构函数语法：~类名(){}
  - 析构函数没有返回值也不写void
  - 函数名称与类名相同，在名称前加上符号 ~ 
  - 析构函数不可以有参数，因此不可以发生重载
  - 程序在对象销毁前会自动调用析构，无需手动调用，而且只会调用一次
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //对象的初始化和清理
  //1、构造函数 进行初始化操作
  class Person {
  public:
    //1.1、构造函数
    //没有返回值 不用写void
    //函数名 与类名相同
    //构造函数可以有参数，可以发生重载
    //创建对象的时候，构造函数会自动调用，而且只调用一次
    Person() {
        cout << "Person 构造函数的调用" << endl;
    }

    //2、析构函数 进行清理的操作
    //没有返回值 不写void
    //函数名和类名相同 在名称前面加 ~
    //析构函数不可以有参数的，不可以发生重载
    //对象在销毁前，会自动调用析构函数，而且只会调用一次
    ~Person() {
        cout << "Person的析构函数调用" << endl;
    }
  };

  //构造和析构都是必须有的实现，如果我们自己不提供，编译器会提供一个空实现的构造和析构
  void test01() {
    Person p; //在栈上的数据，test01执行完毕后，释放这个对象
  }
  int main()
  {
    test01();

    //Person p;

    system("pause");
    return 0;
  }
  ```
##### 构造函数的分类及调用
- 两种分类方式
  - 按参数分为：有参构造和无参构造
  - 按类型分为：普通构造和拷贝构造
- 三种调用方式
  - 括号法
  - 显示法
  - 隐式转换法
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //1、构造函数的分类及调用
  //分类
  //按照参数分类   无参构造函数（默认构造）和有参构造函数
  //按照类型分类   普通构造函数和拷贝构造函数

  class Person {
  public:
    //构造函数
    Person() {                 //无参构造函数
        cout << "Person的无参构造函数调用" << endl;
    }

    Person(int a) {            //有参构造函数
        age = a;
        cout << "Person的有参构造函数调用" << endl;
    }

    //拷贝构造函数
    Person(const Person &p) {
        //将传入的所有属性，拷贝到参数身上
        age = p.age;
        cout << "Person的拷贝构造函数调用" << endl;
    }

    ~Person() {                //析构函数
        cout << "Person的析构函数调用" << endl;
    }

    int age;
  };

  //调用 
  void test01() {

    //1、括号法
    //Person p1;  //默认构造函数调用
    //Person p2(10); //有参构造函数
    //Person p3(p2);  //拷贝构造函数
    //注意事项
    //调用默认构造函数的时候，不要加()
    //因为下面这行代码，编译器会认为式一个函数的声明，不会认为在创建对象
    //Person p1();
    /*cout << "p2的年龄为：" << p2.age << endl;
    cout << "p3的年龄为：" << p3.age << endl;*/

    //2、显示法
    //Person p1;
    //Person p2 = Person(10);  //有参构造
    //Person p3 = Person(p2);  //拷贝构造
    /*Person(10);*/  //匿名对象  特点：当前行执行结束后，系统会立即回收掉匿名对象
    //cout << "aaaa" << endl;
    //注意事项2
    //不要利用拷贝构造函数 初始化匿名对象,编译器会认为Person(p3)等价于Person p3（对象声明）
    /*Person(p3);*/

    //3、隐式转换法
    Person p4 = 10;  //相当于写了 Person p4 = Person(10); 相当于有参构造
    Person p5 = p4;  //拷贝构造
  }
  int main()
  {
    test01();

    system("pause");
    return 0;
  }
  ```
##### 拷贝构造函数调用时机
- C++种拷贝构造函数调用时机通常有三种情况
  - 使用一个已经创建完毕的对象来初始化一个新对象
  - 值传递的方式给函数参数传值
  - 以值方式返回局部对象
- 示例
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //拷贝构造函数调用时机

  class Person {
  public:
    
    Person() {                 //无参构造函数
        cout << "Person的无参构造函数调用" << endl;
    }

    Person(int age) {            //有参构造函数
        m_Age = age;
        cout << "Person的有参构造函数调用" << endl;
    }

    //拷贝构造函数
    Person(const Person & p) {
        //将传入的所有属性，拷贝到参数身上
        m_Age = p.m_Age;
        cout << "Person的拷贝构造函数调用" << endl;
    }

    ~Person() {                //析构函数
        cout << "Person的析构函数调用" << endl;
    }

    int m_Age;
  };

  //1、使用一个已经创建完毕的对象来初始化一个新对象
  //void test01() {
  //    Person p1(20);  //有参构造函数
  //    Person p2(p1);  //拷贝构造函数
  //
  //    cout << "p2的年龄为" << p2.m_Age << endl;
  //}

  //2、值传递的方式给函数参数传值
  //void doWork(Person p) {
  //
  //}
  //
  //void test02() {
  //    Person p;
  //    doWork(p);
  //}

  //3、值方式返回局部对象
  Person doWork2() {
    Person p1;
    cout << (int*)&p1 << endl;
    return p1;
  }

  void test03() {
    Person p = doWork2();
    cout << (int*)&p << endl;
  }

  int main()
  {
    //test01();


    system("pause");
    return 0;
  }
  ```
##### 构造函数调用规则
- 默认情况下，C++编译器至少给一个类添加3个函数
  - 默认构造函数（无参，函数体为空）
  - 默认析构函数（无参，函数体为空）
  - 默认拷贝构造函数，对属性进行值拷贝
- 构造函数调用规则如下
  - 如果用户定义有参构造函数，C++不在提供默认无参构造，但是会提供默认拷贝构造
  - 如果用户定义拷贝构造函数，C++不会再提供其他构造函数
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //构造函数的调用规则
  //1、创建一个类，C++编译器会给每个类都添加至少三个函数
  //默认构造（空实现）
  //析构函数（空实现）
  //拷贝构造（空实现）

  //2、如果我们写了有参构造函数，编译器就不再提供默认构造，依然提供拷贝构造
  //如果我们写了拷贝构造函数，编译器就不再提供其他普通构造函数

  class Person {
  public:
    
    Person() {                 //无参构造函数
       cout << "Person的无参构造函数调用" << endl;
    }

    Person(int age) {            //有参构造函数
        m_Age = age;
        cout << "Person的有参构造函数调用" << endl;
    }

    //拷贝构造函数
    Person(const Person & p) {
        //将传入的所有属性，拷贝到参数身上
        m_Age = p.m_Age;
        cout << "Person的拷贝构造函数调用" << endl;
    }

    ~Person() {                //析构函数
        cout << "Person的析构函数调用" << endl;
    }

    int m_Age;
  };

  void test01() {
    Person p;
    p.m_Age = 18;
    Person p2(p);

    cout << "p2的年龄为" << p2.m_Age << endl;
  }

  void test02() {
    Person p;
  }

  int main()
  {
    //test01();   //示例1
    test02();

    system("pause");
    return 0;
  }
  ```
##### 深拷贝与浅拷贝
- 深浅拷贝是面试经典问题，也是常见的一个坑
- 浅拷贝：简单的赋值拷贝操作
- 深拷贝：在堆区重新申请空间，进行拷贝操作
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //深拷贝与浅拷贝
  //浅拷贝带来的问题就是堆区的内存重复释放
  //浅拷贝的问题要利用深拷贝进行解决

  class Person {
  public:
    
    Person() {                 //无参构造函数
       cout << "Person的无参构造函数调用" << endl;
    }

    Person(int age,int height) {            //有参构造函数
        m_Age = age;
        m_Height = new int(height);
        cout << "Person的有参构造函数调用" << endl;
    }

    //自己实现拷贝构造函数解决浅拷贝带来的问题
    Person(const Person &p) {
        cout << "Person拷贝构造函数调用" << endl;
        //将传入的所有属性，拷贝到参数身上
        m_Age = p.m_Age;
        //m_Height = p.m_Height;   编译器默认实现的就是这行代码
        //深拷贝操作
        m_Height = new int(*p.m_Height);
    }

    //析构代码，将堆区开辟数据做释放操作
    //析构时候，构造函数执行先进后出，谁先执行谁最后释放
    ~Person() {                //析构函数
        if (m_Height != NULL) {
            delete m_Height;  //清空堆区内存
            m_Height = NULL;  //防止野指针出现
        }
        cout << "Person的析构函数调用" << endl;
    }

    int m_Age;      //年龄
    int *m_Height;  //身高
  };

  void test01() {
    Person p1(18 ,160);
    cout << "p1的年龄为" << p1.m_Age << "身高为：" << *p1.m_Height << endl;

    Person p2(p1);
    cout << "p1的年龄为" << p2.m_Age << "身高为：" << *p2.m_Height << endl;
  }

  void test02() {
    Person p;

  }

  int main()
  {
    test01();   //示例1
    test02();

    system("pause");
    return 0;
  }
  ```
##### 初始化列表
- 作用：C++提供了初始化列表语法，用来初始化属性
- 语法：构造函数()：属性1(值1)，属性2(值2)...{}
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //初始化列表

  class Person {
  public:
    
    //传统初始化操作
    /*Person(int a, int b, int c) {
        m_A = a;
        m_B = b;
        m_C = c;
    }*/

    //初始化列表初始化属性
    Person(int a, int b, int c) :m_A(a), m_B(b), m_C(c) {
      cout << "m_A = " << m_A << endl;
      cout << "m_B = " << m_B << endl;
      cout << "m_C = " << m_C << endl;
    }
  private:
    int m_A;
    int m_B;
    int m_C;
  };

  void test01() {
    //Person p(10, 20, 30);
    Person p(30,20,10);
    
  }

  int main()
  {
    test01();   //示例1

    system("pause");
    return 0;
  }
  ```
##### 类对象作为类成员
- C++类中的成员可以是另一个类的对象，我们称该成员为 对象成员
- 示例：
  ```cpp
  class A{}
  class B{
    A a;
  }
  ```
- B类中有对象A作为成员，A为对象成员
- A与B的构造和析构的顺序示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //类对象作为类成员

  //手机类
  class Phone {
  public:

    Phone(string pName) {
        m_PName = pName;
        cout << "Phone的构造函数调用" << endl;
    }

    ~Phone() {
        cout << "Phone的析构函数调用" << endl;
    }


    //手机品牌名称
    string m_PName;
  };

  //人类
  class Person {
  public:

    //Phone m_Phone = pName  隐式转换法
    Person(string name, string pName) :m_Name(name), m_Phone(pName) {
        cout << "Person的构造函数调用" << endl;
    }

    ~Person() {
        cout << "Person的析构函数调用" << endl;
    }

    //姓名
    string m_Name;
    //手机
    Phone m_Phone;
  };

  //当其他的类的对象作为本类成员，构造时候先构造类对象，再构造自身。
  //析构的顺序与构造的顺序相反
  void test01() {
    Person p("张三", "苹果");
    cout << p.m_Name << "拿着" << p.m_Phone.m_PName << endl;
  }

  int main()
  {
    test01();   //示例1

    system("pause");
    return 0;
  }
  ```
##### 静态成员
- 静态成员就是再成员变量和成员函数前加上关键字static，称为静态成员
- 静态成员分成：
  - 静态成员变量
    - 所有对象共享同一份数据
    - 在编译阶段分配内存
    - 类内声明，类外初始化
  - 静态成员函数
    - 所有对象共享同一个函数
    - 静态成员函数只能访问静态成员变量
- 示例1：静态成员变量
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>
  //静态成员变量
  class Person {
  public:
    //1、所有对象都共享同一份数据
    //2、编译阶段就分配内存
    //3、类内声明，类外初始化操作
    static int m_A;

    //静态成员变量也是有访问权限的
  private:
    static int m_B;
  };

  int Person:: m_A = 100;    //类外初始化

  int Person::m_B = 300;

  void test01() {
    Person p;
    //打印出来100
    cout << p.m_A << endl;

    Person p2;
    p2.m_A = 200;
    //打印出来200
    cout << p2.m_A << endl;
  }

  void test02() {
    //静态成员变量 不属于某个对象上，所有对象都共享同一份数据
    //因此静态成员变量有两种访问方式

    //1、通过对象进行访问
    Person p;
    cout << p.m_A << endl;

    //2、通过类名进行访问
    cout << Person::m_A << endl;

    //cout << Person::m_B << endl;  类外访问不到私有静态成员变量
  }

  int main()
  {
    //test01();   //test01
    test02();     //test02

    system("pause");
    return 0;
  }
  ```
- 示例2：静态成员函数
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //静态成员函数
  //所有对象共享同一个函数
  //静态成员函数只能访问静态成员变量

  class Person {
  public:

    //静态成员函数
    static void func() {
        m_A = 100;
        //m_B = 200;  静态成员函数不可以访问非静态成员变量
        cout << "static void func调用" << endl;
    }

    //静态成员变量
    static int m_A;

    //非静态成员变量
    int m_B;    

    //静态成员函数也是有访问权限的
  private:
    static void func2() {
        cout << "static void fun2调用" << endl;
    }
  };

  int Person::m_A = 0;

  //有两种访问方式
  void test01() {
    //1、通过对象访问
    Person p;
    p.func();

    //2、通过类名访问
    Person::func();

    //Person::func2();  类外访问不到私有静态成员函数
  }

  int main()
  {
    //test01();   //示例1

    system("pause");
    return 0;
  }
  ```
#### C++对象模型和this指针
##### 成员变量和成员函数分开存储
- 在C++中，类内的成员变量和成员函数分开存储，只有非静态成员变量才属于类的对象上
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //成员变量和成员函数是分开存储的

  class Person {
    int m_A;  //非静态成员变量  属于类的对象上面

    static int m_B;   //静态成员变量 不属于类对象上

    //非静态成员函数  不属于类的对象上
    void func() {

    }

    //静态成员函数 不属于类的对象上
    static void func2() {

    }
  };

  int Person::m_B = 10;

  //void test01() {
  //    Person p;
  //
  //    //空对象占用内存空间为：1字节
  //    //C++编译器会给每个空对象也分配一个字节空间，是为了区分空对象占内存的位置
  //    //每个空对象也应该有一个独一无二的内存地址
  //    cout << "size of p = " << sizeof(p) << endl;
  //}

  void test02() {
    Person p;
    //
    cout << "size of p = " << sizeof(p) << endl;
  }

  int main()
  {
    //test01();   //示例1

    system("pause");
    return 0;
  }
  ```
##### this指针概念
- 在C++中成员变量和成员函数是分开存储的
- 每一个非静态成员函数只会生成一份函数实例，多个同类型的对象会共用一块代码
- C++通过提供特殊的对象指针，this指针解决区分哪个对象调用自己的代码。
- this指针指向被调用的成员函数所属的对象
- this指针式隐含每一个非静态成员函数内的一种指针
- this指针不需要定义，直接使用
- this指针的用途
  - 当形参和成员变量同名时，可用this指针来区分
  - 在类的非静态成员函数中返回对象本身，可使用return *this
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  class Person {
  public:

    Person(int age) {
        //this指针指向被调用的成员函数所属的对象
        this->age = age;
    }

    Person& PersonAddAge(Person &p) {
        this->age += p.age;

        //this指向p2的指针，而*this指向的就是p2这个对象本体 
        return *this;
    }
    int age;
  };

  //1、解决名称冲突
  void test01() {
    Person p1(18);
    cout << "p1的年龄为：" << p1.age << endl;
  }
  //2、返回对象本身用 *this
  void test02() {
    Person p1(10);
    Person p2(10);
    //链式编程思想
    p2.PersonAddAge(p1).PersonAddAge(p1).PersonAddAge(p1);

    cout << "p2的年龄为：" << p2.age << endl;
  }

  int main()
  {
    //test01();   //示例1

    test02();

    system("pause");
    return 0;
  }
  ```
##### 空指针访问成员函数
- C++中空指针也是可以调用成员函数的，但是也要注意有没有用到this指针
- 如果用到this指针，需要加以判断保证代码的健壮性
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //空指针访问成员函数
  class Person {
  public:
    void showClassName() {
        cout << "this is Person class" << endl;
    }
    void showPersonAge() {
        //报错原因是因为传入的指针是为NULL
        //用if判断指针是否为空，防止崩溃
        if (this == NULL) {
            return;
        }
        cout << "age = " << m_Age << endl;
    }
    int m_Age;
  };

  void test01() {
    Person* p = NULL;
    p->showClassName();
    p->showPersonAge();  //报错原因是因为传入的指针是为NULL
  }

  int main()
  {
    //test01();   //示例1

    system("pause");
    return 0;
  }
  ```
##### const修饰成员函数
- 常函数：
  - 成员函数后加const后我们称为这个函数为常函数
  - 常函数内不可以修改成员属性
  - 成员属性声明时加关键字mutable后，在常函数中依然可以修改
- 常对象：
  - 声明对象前加const称该对象为常对象
  - 常对象只能调用常函数
- 示例:
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //常函数
  class Person {
  public:

    //this指针的本质，是指针常量，指针的指向是不可以修改的
    //Person * const this;
    //在成员函数后面加const，修饰的是this指向，让指针指向的值也不可以修改
    void showPerson() const {
        this->m_B = 100;
        //this->m_A = 100;
        //this = NULL;  this指针不可以修改指针的指向的
    }

    void func() {

    }

    int m_A;
    mutable int m_B;  //特殊变量，即使在常函数中，也可以修改这个值，加关键字mutable
  };
  //常对象
  void test() {
    const Person p;   //在对象前加const，变为常对象
    //p.m_A = 100;   错误
    p.m_B = 100;   //m_B是特殊值，在常对象下也可以修改

    //常对象只能调用常函数
    p.showPerson();
    //p.func();  错误，因为常对象不可以调用普通成员函数，因为普通成员函数可以修改属性
  }

  void test01() {
    Person p;
    p.showPerson();
  }
  int main()
  {
    //test01();   //示例1

    system("pause");
    return 0;
  }
  ```
#### 友元
- 在程序里，有些私有属性也想让类外特殊的一些函数或者类进行访问，就需要用到友元的技术
- 友元的目的就是让一个函数或者类访问另一个类中私有成员
- 友元的关键字为 friend
- 友元的三种实现
  - 全局函数做友元
  - 类做友元
  - 成员函数做友元
##### 全局函数做友元
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //建筑类
  class Building {

    //goodDay全局函数是Building好朋友，可以访问Building中私有成员
    friend void goodGay(Building* building);
  public:
    Building() {
        m_SittingRoom = "客厅";
        m_BedRoom = "卧室";
    }
  public:
    string m_SittingRoom;   //客厅

  private:
    string m_BedRoom;   //卧室
  };

  //全局函数
  void goodGay(Building *building) {
    cout << "好朋友的全局函数 正在访问：" << building->m_SittingRoom << endl;

    cout << "好朋友的全局函数 正在访问：" << building->m_BedRoom << endl;
  }

  void test() {
    Building building;
    goodGay(&building);
  }

  int main()
  {
    //test01();   //示例1

    system("pause");
    return 0;
  }
  ```
##### 类做友元
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //类做友元
  class Building;
  class GoodDay {
  public:

    GoodDay();

    void visit();  //参观函数  访问Building中的属性
    Building* building;
  };

  class Building {
    friend class GoodDay;    //GoodDay类是本类的好友，可以访问本类私有的成员
  public:
    Building();
  public:
    string m_SittingRoom;  // 客厅

  private:
    string m_BedRoom;  //卧室
  };

  //类外写成员函数
  Building::Building() {
    m_BedRoom = "客厅";
    m_SittingRoom = "卧室";
  }

  GoodDay::GoodDay() {
    //创建一个建筑物对象
    building = new Building; 
  }

  void GoodDay::visit(){
    cout << "好友类正在访问：" << building->m_SittingRoom << endl;
    cout << "好友类正在访问：" << building->m_BedRoom << endl;
  }

  void test01() {
    GoodDay gg;
    gg.visit();
  }
  int main()
  {
    //test01();   //示例1

    system("pause");
    return 0;
  }
  ```
##### 成员函数做友元
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //成员函数做友元
  class Building;

  class GoodDay {
  public:
    GoodDay();

    void visit();    //让visit函数可以访问Building中私有成员
    void visit2();   //让visit2函数不可以访问Building中私有成员

    Building* building;
  };

  class Building {

    //告诉编译器  GoodDay类下的visit成员函数作为本类好友，可以访问私有成员
    friend void GoodDay::visit();

  public:
    Building();

  public:
    string m_SittingRoom;  //客厅

  private:
    string m_BedRoom;  //卧室
  };

  //类外实现成员函数
  GoodDay::GoodDay() {
    building = new Building;
  }

  Building::Building() {
    m_SittingRoom = "客厅";
    m_BedRoom = "卧室";
  }

  void GoodDay::visit() {
    cout << "visit函数正在访问：" << building->m_SittingRoom << endl;
    cout << "visit函数正在访问：" << building->m_BedRoom << endl;
  }

  void GoodDay::visit2() {
    cout << "visit2函数正在访问：" << building->m_SittingRoom << endl;
  }

  void test01() {
    GoodDay gg;
    gg.visit();
    gg.visit2();
  }

  int main()
  {
    //test01();   //示例1

    system("pause");
    return 0;
  }
  ```
#### 运算符重载
- 运算符重载概念：对已有的运算符重新进行定义，赋予其另一种功能，以适应不同的数据类型
##### 加号运算符重载
- 作用：实现两个自定义数据类型相加的运算
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //加号运算符重载
  class Person {
  public:

    //1、成员函数重载加号  +
    /*Person operator+(Person& p) {
        Person temp;
        temp.m_A = this->m_A + p.m_A;
        temp.m_B = this->m_B = p.m_B;
        return temp;
    }*/

    int m_A;
    int m_B;

  };

  //2、全局函数重载加号  +
  Person operator+(Person& p1, Person& p2) {
    Person temp;
    temp.m_A = p1.m_A + p2.m_A;
    temp.m_B = p1.m_B + p2.m_B;
    return temp;
  }

  //3、函数重载的版本
  Person operator+(Person& p1, int num) {
    Person temp;
    temp.m_A = p1.m_A + num;
    temp.m_B = p1.m_B + num;
    return temp;
  }

  void test01() {
    Person p1;
    p1.m_A = 10;
    p1.m_B = 10;

    Person p2;
    p2.m_A = 10;
    p2.m_B = 10;

    //成员函数重载本质调用
    /*Person p3 = p1.operator+(p2);*/

    //全局函数重载本质调用
    /*Person p3 = operator+(p1 , p2);*/

    Person p3 = p1 + p2;

    //运算符重载也可以发生函数重载
    Person p4 = p1 + 100;

    cout << "p3.m_A = " << p3.m_A << endl; 
    cout << "p3.m_B = " << p3.m_B << endl;

    cout << "p4.m_A = " << p4.m_A << endl;
    cout << "p4.m_B = " << p4.m_B << endl;
  }
  int main()
  {
    test01();   //示例1

    system("pause");
    return 0;
  }

  ```
- 总结：
  - 1、对于内置的数据类型的表达式的运算符是不可能改变的
  - 2、不要滥用运算符重载
##### 左移运算符重载
- 可以输出自定义数据类型
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>
  
  //左移运算符重载

  class Person {

    //友元
    friend ostream& operator<<(ostream& cout, Person& p);

  public:
    //构造函数提供接口赋值
    Person(int a, int b) {
        m_A = a;
        m_B = b;
    }
  private:
    //利用成员函数重载 左移运算符  p.operator<<(cout)  简化版本   p << cout
    //不会利用成员函数重载 << 运算符，因为无法实现 cout在左侧
    /*void operator<<(cout) {

    }*/

    int m_A;
    int m_B;
  };

  //只能利用全局函数重载左移运算符
  //cout 属于 ostream 输出流  属性属于ostream  注意  operator前需要加引用符 &
  ostream & operator<<(ostream &cout , Person &p ) {   //本质 operator<<(cout,p)  简化 cout << p
    cout << "m_A = " << p.m_A << " m_B = " << p.m_B;
    return cout;
  }

  void test01() {
    Person p(10,10);
    cout << p << endl;
  }

  int main()
  {
    test01();   //示例1

    system("pause");
    return 0;
  }
  ```
##### 递增运算符重载
- 作用：通过重载递增运算符，实现自己的整数数据
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //递增运算符重载

  //自定义整形
  class MyInteger {

    //友元
    friend ostream& operator<<(ostream& cout, MyInteger myint);

  public:
    MyInteger() {
        m_Num = 0;
    }

    //重载前置++运算符  返回引用为了一直对一个数据进行递增操作
    MyInteger & operator++() {
        //先进行++运算
        m_Num++;
        //再将自身作为返回
        return *this;
    }
    //重载后置++运算符
    // void operator++(int)里的int代表占位参数，可以用于区分前置和后置递增
    MyInteger operator++(int) {
        //先记录当时结果
        MyInteger temp = *this;
        //再递增
        m_Num++;
        //最后将记录结果做返回
        return temp;
    }

  private:
    int m_Num;
  };

  //重载<<运算符
  ostream& operator<<(ostream &cout, MyInteger myint) {
    cout << myint.m_Num;
    return cout;
  }

  void test01() {
    MyInteger myint;

    cout << ++myint << endl;
  }

  void test02() {
    MyInteger myint;

    cout << myint++ << endl;

    cout << myint << endl;

  }
  int main()
  {
    test01();   //示例1
    test02();

    system("pause");
    return 0;
  }
  ```
##### 赋值运算符重载
- C++编译器至少给一个类添加4个函数
  - 默认构造函数（无参，函数体为空）
  - 默认析构函数（无参，函数体为空）
  - 默认拷贝构造函数，对属性进行值拷贝
  - 赋值运算符operator=,对属性进行值拷贝
- 如果类中有属性指向堆区，做赋值操作时也会出现深浅拷贝
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //赋值运算符重载

  class Person {
  public:
    Person(int age) {
        m_Age = new int(age);
    }

    ~Person() {
        if (m_Age != NULL) {
            delete m_Age;
            m_Age = NULL;
        }
    }

    //重载  赋值运算符
    Person& operator=(Person &p) {
        //编译器是提供的浅拷贝
        //m_Age = p.m_Age;

        //应该先判断时候有属性在堆区，如果有先释放干净，然后再深拷贝
        if (m_Age != NULL) {
            delete m_Age;
            m_Age = NULL;
        }
        //深拷贝操作 
        m_Age = new int(*p.m_Age);

        //返回对象本身
        return *this;
    }

    int* m_Age;
  };

  void test01() {
    Person p1(18);
    Person p2(20);

    p2 = p1;   //赋值操作

    cout << "p1的年龄为：" << p1.m_Age << endl;
    cout << "p2的年龄为：" << p2.m_Age << endl;
  }

  int main()
  {
    test01();   //示例1
    test02(); 

    system("pause");
    return 0;
  }
  ```
##### 关系运算符重载
- 作用：重载关系运算符，可以让两个自定义类型对象进行对比操作
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //重载关系运算符
  class Person {
  public:
    Person(string name, int age) {
        m_Name = name;
        m_Age = age;
    }

    //重载 == 号关系运算符
    bool operator==(Person &p) {
        if (this->m_Name == p.m_Name && this->m_Age == p.m_Age) {
            return true;
        }
        return false;
    }

    //重载 !=号关系运算符
    bool operator!=(Person &p) {
        if (this->m_Name == p.m_Name && this->m_Age == p.m_Age) {
            return false;
        }
        return true;
    }

    string m_Name;
    int m_Age;
  };

  void test01() {
    Person p1("Tom", 18);
    Person p2("Tom", 18);
    if (p1 == p2) {
        cout << "p1和p2相同" << endl;
    }
  }

  int main()
  {
    test01();   //示例1

    system("pause");
    return 0;
  }
  ```
##### 函数调用运算符重载
- 函数调用运算符()也可以重载
- 由于重载后使用的方式非常像函数的调用，因此称为仿函数
- 仿函数没有固定写法，非常灵活
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //函数调用运算符重载
  class MyPrint {
  public:

    //重载函数调用运算符
    void operator()(string text) {
        cout << text << endl;
   }
  };

  void test01() {
    MyPrint myPrint;
    myPrint("hello world");  //由于使用起来非常类似于函数调用，因此称为仿函数
  }

  //仿函数非常灵活，没有固定的写法
  //加法

  class MyAdd {
  public:
    int operator()(int num1, int num2) {
        return num1 + num2;
    }
  };

  void test02() {
    MyAdd myadd;
    int ret = myadd(100, 100);
    cout << "ret = " << ret << endl;

    //匿名函数对象
    cout << MyAdd()(100, 100) << endl;
  }

  int main()
  {
    test01();   //示例1
    test02();

    system("pause");
    return 0;
  }
  ```
#### 继承
- 继承是面向对象三大特性之一
- 继承的技术可以减少重复代码
##### 集成的基本语法
- 基本语法：class 子类 : 继承方式  父类 {...};
- class A : public B {...};
- A:子类：称为派生类
- B:父类：称为基类
##### 继承方式
- 继承方式一共有三种：
  - 公共继承
  - 保护继承
  - 私有继承
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //继承方式
  class Basel {
  public:
    int m_A;
  protected:
    int m_B;
  private:
    int m_C;
  };

  //公共继承
  class Son1 :public Basel {
  public:
    void func() {
        //父类中的公关权限成员 到子类中依然是公共权限
        m_A = 10;  
        //父类中的保护权限成员 到子类中依然是保护权限
        m_B = 10;
        //父类中的私有权限成员 子类访问不到
        //m_C = 10;
    }
  };

  //保护继承
  class Son2 :protected Basel {
  public:
    void func() {
        //父类中的公共成员，到子类中变为保护权限
        m_A = 100;
        //父类中保护成员，到子类中变为保护权限
        m_B = 100;

        //父类中的私有成员 子类访问不到
        //m_C = 100;
    }
  };

  //私有继承
  class Son3 :private Basel {
  public:
    void func() {
        //父类中公共成员 到子类中变为私有成员
        m_A = 100;
        //父类中保护乘员 到子类中变为私有成员
        m_B = 100;

        //父类中私有的成员，子类访问不到
        //m_C = 100;
    }
  };

  class GrandSon3 :public Son3 {
  public:
    void func() {
        //到了Son3中 m_A变为私有  此子类也访问不到
        //m_A = 1000;
        // 到了Son3中 m_B变为私有  此子类也访问不到
        //m_B = 1000;
    }
  };

  void test01() {
    Son1 s1;
    s1.m_A = 100;

    //到Son1中 m_B是保护权限  类外访问不到
    //s1.m_B = 10;
  }

  void test02() {
    Son2 s2;
    //s1.m_A = 1000;     在Son2中 m_A变为保护权限，因此类外访问不到
    //是。m_B = 1000；   在Son2中 m_B保护权限  类外不可以访问
  }

  void test03() {
    Son3 s3;

    //s3.m_A = 100;   在Son3中 m_A变为私有成员  类外访问不到
    //s3.m_B = 100;   在Son3中 m_B变为私有成员  类外访问不到
  }

  int main()
  {
    test01();   //示例1
    test02();

    system("pause");
    return 0;
  }
  ```
##### 继承中的对象模型
- 问题：从父类继承过来的成员，哪些属于子类对象中的
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //继承中的对象模型
  class Base {
  public:
    int m_A;
  protected:
    int m_B;
  private:
    int m_C;
  };

  class Son :public Base {
  public:
    int m_D;
  };

  void test01() {

    //父类中所有非静态成员属性都会被子类继承下去
    //父类中私有成员属性 是被编译器给隐藏了 因此访问不到 但是确实被继承下去了
    //可在vs 开发人员命令提示符里查看对象模型  cd到具体的文件路径下
    //命令 cl /d1 reportSingleClassLayout"类名" "文件命"  “tab补全”  （第一个是L第二个是数字1）
    cout << "size of Son = " << sizeof(Son) << endl;   //16
  }

  int main()
  {
    test01();   //示例1
   
    system("pause");
    return 0;
  }

  ```
##### 继承中构造和析构顺序
- 子类继承父类后，当创建子类对象，也会调用父类的构造函数
- 父类和子类的构造和析构顺序
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //继承中的构造和析构的顺序
  class Base {
  public:
    Base() {
        cout << "Base构造函数" << endl;
    }

    ~Base() {
        cout << "Base析构函数" << endl;
    }
  };

  class Son :public Base {
  public:
    Son() {
        cout << "Son构造函数" << endl;
    }

    ~Son() {
        cout << "Son析构函数" << endl;
    }
  };

  void test01() {
    //Base b;
    //继承中的构造和析构顺序如下：
    //先构造父类，再构造子类  析构的顺序与构造的顺序相反
    Son s;
  }

  int main()
  {
    test01();   //示例1
   
    system("pause");
    return 0;
  }
  ```
##### 继承同名成员处理方式
- 当子类与父类出现同名的成员，通过子类对象访问子类与父类同名的数据方法：
  - 访问子类同名成员直接访问即可
  - 访问父类同名成员需要加作用域
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //继承同名成员处理方式
  class Base {
  public:
    Base() {
        m_A = 100;
    }

    void func() {
        cout << "Base - func()调用" << endl;
    }

    void func(int a) {
        cout << "Base - func(int a)调用" << endl;
    }

    int m_A;
  };

  class Son :public Base {
  public:
    Son() {
        m_A = 200;
    }

    void func() {
        cout << "Son - func()调用" << endl;
    }

    int m_A;
  };

  //同名成员属性处理方式
  void test01() {
    Son s;
    cout << "Son m_A = " << s.m_A << endl;

    //如果通过子类对象访问父类中同名成员需要加作用域
    cout << "Base m_A = " << s.Base::m_A << endl;
  }

  //同名成员函数处理方式
  void test02() {
    Son s;
    s.func();  //直接调用  调用是子类中的同名成员

    //调用父类中同名成员函数
    s.Base::func();

    //如果子类中出现和父类同名的成员函数，子类的同名成员会隐藏掉父类中所有同名成员函数
    //如果想访问到父类中被隐藏的同名成员函数，需要加作用域
    //s.func(100);  报错
    s.Base::func(100);
  }

  int main()
  {
    test01();   //示例1
    test02();

    system("pause");
    return 0;
  }
  ```
##### 继承同名静态成员处理方式
- 继承中同名的静态成员在子类对象上与非静态成员处理方式一致
  - 访问子类同名成员 直接访问即可
  - 访问父类同名成员 需要加作用域
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //继承同名静态成员处理方式
  class Base {
  public:
    static void func() {
        cout << "Base - staitc void func()" << endl;
    }

    static void func(int a) {
        cout << "Base - staitc void func(int a)" << endl;
    }
    static int m_A;
  };

  int Base::m_A = 100;

  class Son :public Base {
  public:
    static int m_A;
    static void func() {
        cout << "Son - staitc void func()" << endl;
    }
    static int m_A;
  };
  int Son::m_A = 200;

  //同名静态成员属性处理方式
  void test01() {

    //1、通过对象访问
    cout << "通过对象访问：" << endl;
    Son s;
    cout << "Son m_A = " << s.m_A << endl;
    cout << "Base m_A = " << s.Base::m_A << endl;

    //2、通过类名访问
    cout << "通过类名访问：" << endl;
    cout << "Son m_A = " << Son::m_A << endl;
    //第一个:: 代表通过类名方式访问  第二个::代表访问父类作用域下
    cout << "Base m_A = " << Son::Base::m_A << endl;

  }

  //同名静态成员函数处理方式
  void test02() {
    //1、通过对象访问
    cout << "通过对象访问：" << endl;
    Son s;
    s.func();
    s.Base::func();

    //通过类名访问
    cout << "通过类名访问：" << endl;
    Son::func();
    Son::Base::func();

    //子类出现和父类同名静态成员函数，也会隐藏父类中所有同名成员函数
    //如果想访问父类中被隐藏同名成员，需要加作用域
    Son::Base::func(100);
  }

  int main()
  {
    test01();   //示例1
    test02();

    system("pause");
    return 0;
  }
  ```
##### 多继承语法
- C++允许一个类继承多个类
- 语法：class 子类:继承方式 父类1, 继承方式 父类2...
- 多继承可能会引发父类中有同名成员出现，需要加作用域区分
- 注意：C++实际开发中不建议用多继承
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //多继承语法
  class Base {
  public:
    Base() {
        m_A = 100;
    }
     int m_A;
  };

  class Base2 {
  public:
    Base2() {
        m_A = 100;
    }
    int m_A;
  };

  //子类 需要继承Base和Base2
  //语法：class 子类 :继承方式 父类1, 继承方式 父类2 ...
  class Son :public Base , public Base2 {
  public:
    Son() {
        m_C = 300;
        m_D = 400;
    }
    int m_C;
    int m_D;
  };

  void test01() {
    Son s;
    cout << "sizeof Son = " << sizeof(s) << endl;

    //当父类中出现同名成员，需要加作用域区分
    cout << "Base m_A = " << s.Base::m_A << endl;
    cout << "Base2 m_A = " << s.Base2::m_A << endl;
    }

  int main()
  {
    test01();   //示例1
    
    system("pause");
    return 0;
  }
  ```
##### 菱形继承
- 菱形继承概念：
  - 两个派生类继承同一个基类
  - 又有某个类同时继承这两个派生类
  - 菱形继承也成为钻石继承
- 菱形继承问题：
  - 当两个派生类同时继承基类，继承这两个派生类的新类使用数据时，就会产生二义性
  - 新类继承基类的数据继承了两份，这份数据中只需要一份就可以
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //动物类
  class Animal {
  public:
    int m_Age;
  };

  //利用虚继承 解决菱形继承的问题
  // 继承之前  加上关键字 virtual 变为虚继承
  // Animal类称为 虚基类
  //羊类
  class Sheep :virtual public Animal {

  };

  //驼类
  class Tuo :virtual public Animal {

  };

  //羊驼类
  class SheeoTuo :public Sheep, public Tuo {

  };

  void test01() {
    SheeoTuo st;
    st.Sheep::m_Age = 18;
    st.Tuo::m_Age = 28;
    //当出现菱形继承，有两份父类拥有相同的数据，需要加以作用域区分
    cout << "st.Sheep::m_Age = " << st.Sheep::m_Age << endl;
    cout << "st.Tuo::m_Age = " << st.Tuo::m_Age << endl;
    cout << "st.m_Age = " << st.m_Age << endl;

    //这份数据知道只要有一份就可以了，菱形继承导致了数据有两份，资源浪费

  }

  //虚继承
  //vbptr  ---- vbtable   指向虚基类表
  //v - virtual  虚
  //b - base  基类
  //ptr - pointer 指针

  int main()
  {
    test01();   //示例1
    
    system("pause");
    return 0;
  }
  ```
#### 多态
##### 多态的基本概念
- 多态是C++面向对象三大特性之一
- 多态分为两类
  - 静态多态：函数重载和运算符重载属于静态多态，复用函数名
  - 动态多态：派生类和虚函数实现运行时多态
- 静态多态和动态多态区别：
  - 静态多态的函数地址早绑定 - 编译阶段确定函数地址
  - 动态多态的函数地址晚绑定 - 运行阶段确定函数地址
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //多态

  //动物类
  class Animal {
  public:
    //speak函数就是虚函数
    //函数前面加上virtual关键字，变成虚函数，那么编译器在编译的时候就不能确定函数调用了
    virtual void speak() {
        cout << "动物再说话" << endl;
   }
  };

  //猫类
  class Cat :public Animal {
  public:
    //重写  函数返回值类型  函数名称  参数列表  完全相同
    void speak() {
        cout << "小猫在说话" << endl;
    }
  };

  //狗类
  class Dog :public Animal {
  public:
    void speak() {
        cout << "小狗在说话" << endl;
    }
  };

  //执行说话的函数
  //地址早绑定  在编译阶段就确定函数地址
  /如果想执行让猫说话，那么这个函数地址就不能提前绑定，需要在执行阶段进行绑定，地址晚绑定

  //动态多态满足条件
  //1、有继承关系
  //2、子类要重写父类的虚函数

  //动态多态使用
  //父类的指针或者引用 指向子类对象
  
  //我们希望传入什么对象，那么久调用什么对象的函数
  //如果函数地址在编译阶段就能确定，就是静态联编
  //如果函数地址在运行阶段才能确定，就是动态联编

  void doSpeak(Animal& animal) {    //Animal & animal =  cat;
    animal.speak();               //动物在说话
  }

  void test01() {
    Cat cat;
    doSpeak(cat);

    Dog dog;
    doSpeak(dog);
  }

  int main()
  {
    test01();   //示例1
    
    system("pause");
    return 0;
  }
  ```
##### 多态案例---计算器类
- 多态的优点
  - 代码组织结构清晰
  - 可读性强
  - 利于后期和前期的扩展以及维护
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  ////分别利用普通写法和多态技术实现计算器

  //普通写法
  class Calculator {
  public:

    int getRestlt(string oper) {
        if (oper == "+") {
            return m_Num1 + m_Num2;
        }
        else if (oper == "-") {
            return m_Num1 - m_Num2;
        }
        else if (oper == "*") {
            return m_Num1 * m_Num2;
        }
        else if (oper == "/") {
            return m_Num1 / m_Num2;
        }

    //如果想扩展新的功能，需要修改源码
    //在正式开发环境中，提倡开闭原则
    //在开闭原则：对扩展进行开放，对修改进行关闭44

    }

    int m_Num1;  //操作数 1 
    int m_Num2;  //操作数 2
  };

  void test01() {

    //创建计算器对象
    Calculator c;
    c.m_Num1 = 10;
    c.m_Num2 = 10;
    
    cout << c.m_Num1 << " + " << c.m_Num2 << " = " << c.getRestlt("+") << endl;
  }

  //利用多态实现计算器
  //多态好处：
  // 1、组织结构清晰
  // 2、可读性强
  // 3、对于前期和后期扩展以及维护性高
  //实现计算器抽象类
  class AbstractCalculator {
  public:

    virtual int getResult() {
        return 0;;
    }

    int m_Num1;
    int m_Num2;
  };

  //加法计算器类
  class addCalculator :public AbstractCalculator {
  public:
    int getResult() {
        return m_Num1 + m_Num2;
    }
  };

  //减法计算器类
  class SubCalculator :public AbstractCalculator {
  public:
    int getResult() {
        return m_Num1 - m_Num2;
    }
  };

  //乘法计算器类
  class MulCalculator :public AbstractCalculator {
  public:
    int getResult() {
        return m_Num1 * m_Num2;
    }
  };

  void test02() {
    //多态使用条件
    //父类指针或者引用指向子类对象

    //加法运算
    AbstractCalculator* abc = new addCalculator;
    abc->m_Num1 = 10;
    abc->m_Num2 = 10;

    cout << abc->m_Num1 << " + " << abc->m_Num2 << " = " << abc->getResult() << endl;
    delete abc;

    //减法运算
    abc = new SubCalculator;
    abc->m_Num1 = 100;
    abc->m_Num2 = 10;
    cout << abc->m_Num1 << " - " << abc->m_Num2 << " = " << abc->getResult() << endl;
    delete abc;
  }

  int main()
  {
    test01();   //示例1
    test02();   //示例2
    system("pause");
    return 0;
  }
  ```
- 总结：C++开发提倡利用多态设计程序架构，因为多态优点很多
##### 纯虚函数和抽象类
- 在多态中，通常父类中虚函数的实现是毫无意义的，主要都是调用子类重写的内容，因此可将虚函数改为纯虚函数
- 纯虚函数语法：virtual 返回值类型 函数名 (参数列表) = 0;
- 当类中有了纯虚函数，这个类也成为抽象类
- 抽象类特点：
  - 无法实例化对象
  - 子类必须重写抽象类中的纯虚函数，否则也属于抽象类
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //纯虚函数和抽象类

  class Base {
  public:
    //纯虚函数
    //只要有一个纯虚函数，这个类称为抽象类
    //抽象类特点：
    //1、无法实例化对象
    //2、抽象类的子类必须要重写父类中的纯虚函数，否则也属于抽象类
    virtual void func() = 0;
  };

  class Son :public Base {
  public:
    virtual void func() {
        cout << "func函数调用" << endl;
    }
  };

  void test01() {
    //Base b；//抽象类是无法实例化对象的
    //new Base；抽象类是无法实例化对象的

    //Son s;  //子类必须重写父类中的纯虚函数，否则无法实例化对象

    Base* base = new Son;
    base->func();
    delete base; //记得销毁
  }

  void test02() {
  
  }

  int main()
  {
    test01();   //示例1
    
    system("pause");
    return 0;
  }
  ```
##### 多态案例---制作饮品
- 案例描述：
  - 流程：煮水、冲泡、倒入杯中-加入辅料
  - 利用多态技术实现，提供抽象制作饮品基类，提供子类制作咖啡和茶叶
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //多态案例2   制作饮品

  class AbstractDrinking {
  public:

    //煮水
    virtual void Boil() = 0;

    //冲泡
    virtual void Brew() = 0;

    //倒入杯中
    virtual void PourInCup() = 0;

    //加入辅料
    virtual void PutSomething() = 0;

    //制作饮品
    void makeDrink() {
        Boil();
        Brew();
        PourInCup();
        PutSomething();
    }
  };

  //制作咖啡
  class Coffee :public AbstractDrinking {
  public:
    //煮水
    virtual void Boil() {
        cout << "煮农夫山泉" << endl;
    }

    //冲泡
    virtual void Brew() {
        cout << "冲泡咖啡" << endl;
    }

    //倒入杯中
    virtual void PourInCup() {
        cout << "倒入杯中" << endl;
    }

    //加入辅料
    virtual void PutSomething() {
        cout << "加入糖和牛奶" << endl;
    }
  };

  //制作茶水
  class Tea :public AbstractDrinking {
  public:
    //煮水
    virtual void Boil() {
        cout << "煮农夫山泉" << endl;
    }

    //冲泡
    virtual void Brew() {
        cout << "冲泡茶叶" << endl;
    }

    //倒入杯中
    virtual void PourInCup() {
        cout << "倒入杯中" << endl;
    }

    //加入辅料
    virtual void PutSomething() {
        cout << "加入柠檬" << endl;
    }
  };

  //制作的函数
  void doWork(AbstractDrinking* abs) {  //AbstractDrinking * abs = new Coffee
    abs->makeDrink();
    delete abs;  //手动释放

  }

  void test01() {
    //制作咖啡
    doWork(new Coffee);

    cout << "--------------------------" << endl;

    //制作茶叶
    doWork(new Tea);
  }

  void test02() {
  
  }

  int main()
  {
    test01();   //示例1
    
    system("pause");
    return 0;
  }
  ```
##### 虚析构和纯虚析构
- 多态使用时，如果子类中有属性开辟到堆区，那么父类指针在释放时无法调用到子类的析构代码
- 解决方式：将父类中的析构函数改为虚析构或者纯虚析构
- 虚析构额纯虚析构共性：
  - 可以解决父类指针释放子类对象
  - 都需要有具体的函数实现
- 虚析构和纯虚析构区别
  - 如果是纯虚析构，该类属于抽象类，无法实例化对象
- 虚析构语法
  - virtual ~类名(){}
- 纯虚析构语法
  - virtual ~类名() = 0;
  - 类名::~类名(){}
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>

  //虚析构和纯虚析构

  class Animal {
  public:

    Animal() {
        cout << "Animal构造函数调用" << endl;
    }

    //利用虚析构可以解决父类指针释放子类对象时不干净的问题
    /*virtual ~Animal() {
        cout << "Animal虚析构函数调用" << endl;
    }*/

    //纯虚析构  需要声明也需要实现
    //有了纯虚析构之后，这个类也属于抽象类，无法实例化对象
    virtual ~Animal() = 0;

    //纯虚函数
    virtual void speak() = 0;

  };

  Animal::~Animal() {
    cout << "Animal纯虚析构函数调用" << endl;
  }

  class Cat :public Animal {
  public:

    Cat(string name) {

        cout << "Cat构造函数调用" << endl;
        m_Name = new string(name);
    }

    virtual void speak() {
        cout << *m_Name << "小猫在说话" << endl;
    }
    
    ~Cat() {
        if (m_Name != NULL) {

            cout << "Cat析构函数调用" << endl;
            delete m_Name;
            m_Name = NULL;
        }
    }

    string* m_Name;
  };

  void test01() {
    Animal* animal = new Cat("Tom");
    animal->speak();
    //父类指针在析构时候，不会调用子类中析构函数，导致子类如果有堆区属性，出现内存泄露
    delete animal;
  }

  void test02() {
  
  }

  int main()
  {
    test01();   //示例1
    
    system("pause");
    return 0;
  }
  ```
- 总结：
  - 1、虚析构或纯虚析构就是用来解决通过父类指针释放子类对象
  - 2、如果子类中没有堆区数据，可以不写为虚析构或纯虚析构
  - 3、拥有纯虚析构函数的类也属于抽象类
### 文件操作
- 通过文件可以将数据持久化
- C++中对文件操作需要包含头文件<fstream>
- 文件类型分为两种
  - 文本文件：文件以文本的ASCII码形式存储在计算机中
  - 二进制文件“文件以文本的二进制形式存储在计算机中，用户一般不能直接读懂它们
- 操作文件的三大类
  - ofstream：写操作
  - ifstream：读操作
  - fstream：读写操作
#### 文本文件
##### 写文件
- 写文件步骤如下：
  - 包含头文件
    - #include <fstream>
  - 创建流对象
    - ofstream ofs;
  - 打开文件
    - ofs.open("文件路径",打开方式);
  - 写数据
    - ofs <<"写入数据";
  - 关闭文件
    - ofs.close();
- 文件打开方式：

| 打开方式    | 释义                     |
|-------------|------------------------|
| ios::in     | 为读文件而打开文件       |
| ios::out    | 为写文件而打开文件       |
| ios::ate    | 初始位置：文件尾          |
| ios::app    | 追加方式写文件           |
| ios::trunc  | 如果文件存在先删除再创建 |
| ios::binary | 二进制方式               |

- 注意：文件打开方式可以配合使用，利用|操作符
- 例如：用二进制方式写文件 iso::binary | ios::out   二进制方式写文件
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>
  #include <fstream>

  //文本文件  写文件

  void test01() {
    
    //1、包含头文件fstream

    //2、创建流对象

    ofstream ofs;

    //3、指定打开方式

    ofs.open("test.txt", ios::out);

    //4、写内容

    ofs << "姓名：张三" << endl;
    ofs << "性别：男" << endl;

    //5、关闭文件
    ofs.close();
  }

  void test02() {
  
  }

  int main()
  {
    test01();   //示例1
    
    system("pause");
    return 0;
  }
  ```
##### 读文件
- 读文件步骤：
  - 包含头文件
    - #include <fstream>
  - 创建流对象
    - ifstream ifs;
  - 打开文件并判断文件是否打开成功
    - ifs.open("文件路径",打开方式);
  - 读数据
    - 四种方式读取
  - 关闭文件
    - ifs.close();
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>
  #include <fstream>

  //文本文件  读文件

  void test01() {
    
    //1、包含头文件fstream

    //2、创建流对象

    ifstream ifs;

    //3、指定打开方式

    ifs.open("test.txt", ios::in);

    if (!ifs.is_open()) {
        cout << "文件打开失败" << endl;
        return;
    }

    //4、读数据
    //第一种
    /*char buf[1024] = { 0 };
    while (ifs >> buf) {
        cout << buf << endl;
    }*/

    //第二种
    /*char buf[1024] = { 0 };
    while (ifs.getline(buf,sizeof(buf)))
    {
        cout << buf << endl;
    }*/

    //第三种
    string buf;
    while (getline(ifs,buf))
    {
        cout << buf << endl;
    }

    //第四种
    //char c;
    //while ((c=ifs.get())!=EOF)   //EOF end of file
    //{
    //    cout << c;
    //}

    //5、关闭文件
    ifs.close();
  }

  void test02() {
  
  }

  int main()
  {
    test01();   //示例1
    
    system("pause");
    return 0;
  }
  ```
#### 二进制
- 以二进制的方式对文件进行读写操作
- 打开方式要指定为 ios::binary
##### 写文件
- 二进制方式写文件主要利用流对象调用成员数write
- 函数原型：ostream& write(const char * buffer,int len);
- 参数解释：字符指针buffer指向内存种一段存储空间。len是读写的字节数
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>
  #include <fstream>

  //二进制文件  写文件

  class Person {
  public:
    char m_Name[64];  //姓名
    int m_Age;  //年龄
  };

  void test01() {
    
    //1、包含头文件fstream

    //2、创建流对象

    ofstream ofs("Person.txt", ios::out | ios::binary);

    //3、指定打开方式
    //ofs.open("Person.txt", ios::out | ios::binary);
    
    //4、写数据
    Person p = { "张三",18 };
    ofs.write((const char *)&p,sizeof(Person));

    //5、关闭文件
    ofs.close();
  }

  void test02() {
  
  }

  int main()
  {
    test01();   //示例1
    
    system("pause");
    return 0;
  }
  ```
##### 读文件
- 二进制方式读文件主要利用流对象调用成员函数read
- 函数原型：istream& read(char * buffer,int len);
- 参数解释：字符指向buffer指向内存中一段存储空间。len是读写的字节数
- 示例：
  ```cpp
  #include <iostream>
  using namespace std;
  #include <string>
  #include <fstream>

  //二进制文件  读文件

  class Person {
  public:
    char m_Name[64];  //姓名
    int m_Age;  //年龄
  };

  void test01() {
    
    //1、包含头文件fstream

    //2、创建流对象

    ifstream ifs;

    //3、指定打开方式
    ifs.open("Person.txt", ios::in | ios::binary);

    if (ifs.is_open()) {
        cout << "文件打开失败" << endl;
        return;
    }
    
    //4、读数据
    Person p;
    ifs.read((char*)&p, sizeof(Person));
    cout << "姓名：" << p.m_Name << " 年龄：" << p.m_Age << endl;

    //5、关闭文件
    ifs.close();
  }

  oid test02() {
  
  }

  int main()
  {
    test01();   //示例1
    
    system("pause");
    return 0;
  }
  ```

## C++提高编程
- C++泛型编程和STL技术
### 模板
#### 模板的概念
- 作用：建立通用的模具，大大提高复用性
- 特点：
  - 模板不可以直接使用，它只是一个框架
  - 模板的通用并不是万能的
#### 函数模板
- C++另一种编程思想称为泛型编程，主要利用的技术就是模板
- C++提供两种模板机制：【函数模板】和【类模板】
##### 函数模板语法
- 函数模板作用：
  - 建立一个通用函数，其函数返回值类型和形参类型可以不具体制定，用一个虚拟的类型来代表
- 语法：
  ```cpp
  template<typename T>
  //函数声明或定义
  ```
- 释义：
  - template --- 声明创建模板
  - typename --- 表示其后面的符号是一种数据类型，可以用class代替
  - T --- 通用的数据类型，名称可以替换，通常为大写字母
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;

  //函数模板
  //交换两个整型函数
  void swapInt(int& a, int& b)
  {
	int temp = a;
	a = b;
	b = temp;
  }

  //交换两个浮点型函数
  void swapDouble(double& a, double& b)
  {
	double temp = a;
	a = b;
	b = temp;
  }

  //函数模板
  //声明一个模板，告诉编译器后面代码中紧跟着的【T】不要报错，【T】是一个通用数据类型
  template<typename T>  //【typename】可以替换成class
  //通用交换函数
  void mySwap(T& a, T& b)
  {
	T temp = a;
	a = b;
	b = temp;
  }


  //测试
  void test01()
  {
	int a = 10;
	int b = 20;

	//swapInt(a, b);
	//利用函数模板交换
	//两种方式使用函数模板

	//1、自动类型推到
	//mySwap(a, b);
	
	//2、显示指定类型
	mySwap<int>(a,b);

	cout << "a = " << a << endl;
	cout << "b = " << b << endl;

	//double c = 1.1;
	//double d = 2.2;
	//swapDouble(c, d);
	//cout << "c = " << c << endl;
	//cout << "d = " << d << endl;
  }


  int main()
  {
	//测试
	test01();

	system("pause");
	return 0;
  }
  ```
- 总结：
  - 函数模板利用关键字【template】
  - 使用函数模板有两种方式：
    - 自动类型推导
    - 显式指定类型
  - 模板的目的是为了提高复用性，讲类型参数化

##### 函数模板注意事项
- 注意事项
  - 自动类型推导，必须推导出一致的数据类型T才可以使用
  - 模板必须要确定处T的数据类型，才可以使用
- 示例
  ```cpp
  #include<iostream>
  using namespace std;

  //函数模板
  //声明一个模板，告诉编译器后面代码中紧跟着的【T】不要报错，【T】是一个通用数据类型
  template<typename T>  //【typename】可以替换成class
  //通用交换函数
  void mySwap(T& a, T& b)
  {
	T temp = a;
	a = b;
	b = temp;
  }

  //函数模板注意事项
  //1、自动类型推导，必须推导出一致的数据类型T才可以使用
  void test01()
  {
	int a = 10;
	int b = 20;
	mySwap(a, b);  //正确

	char c = 'c';
	//mySwap(a, c); // 错误！推到不出一致的T类型

	cout << "a = " << a << endl;
	cout << "b = " << b << endl;
  }

  //2、模板必须要确定处T的数据类型，才可以使用
  template<typename T>
  void func()
  {
	cout << "func 调用";
  }

  void test02()
  {
	//func();    //错误，模板不能独立使用，必须确定出【T】的类型
	func<int>(); //利用显示指定类型的方式，给T一个类型，才可以使用该模板
  }

  int main()
  {
	//测试
	test01();

	system("pause");
	return 0;
  }
  ```

##### 案例
- 案例描述
  - 利用函数模板封装一个排序的函数，可以对不同数据类型数组进行排序
  - 排序规则从小到大，排序算法为选择排序
  - 分别利用char数组和int数组进行测试
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;

  //实现通用 对数组进行排序的函数
  //规则 从大到小
  //算法 选择
  //测试 char数组、int数组

  //交换函数模板
  template<typename T>
  void mySwap(T& a, T& b)
  {
	T temp = a;
	a = b;
	b = temp;
  }

  //排序算法
  template<typename T>
  void mySort(T arr[],int len)
  {
	for (int i = 0; i < len; i++)
	{
		int max = i; //认定最大值的下标
		for (int j = i + 1; j < len; j++)
		{
			//认定的最大值比遍历出的数值要小，说明【j】下标的元素才是真正的最大值
			if (arr[max] < arr[j])
			{
				max = j;//更新最大值下标
			}
		}
		if (max != i)
		{
			//交换【max】和【i】下标元素
			mySwap(arr[i], arr[max]);
		}
	}
  }

  //提供打印数组模板
  template<typename T>
  void printArray(T arr[], int len)
  {
	for (int i = 0; i < len; i++)
	{
		cout << arr[i] << " ";
	}
	cout << endl;
  }

  //测试
  void test01()
  {
	//测试char数组
	char charArr[] = "badcfe";

	//计算数组长度
	int num = sizeof(charArr) / (sizeof(char));

	//传入排序函数模板参数
	mySort(charArr, num);
	//传入打印函数模板参数
	printArray(charArr,num);
  }

  void test02()
  {
	//测试int数组
	int intArr[] = { 7,5,1,3,9,2,4,6,8 };
	//计算数组长度
	int num = sizeof(intArr) / (sizeof(int));

	//传入排序函数模板参数
	mySort(intArr, num);
	//传入打印函数模板参数
	printArray(intArr, num);
  }

  int main()
  {
	//测试
	test01();

	test02();

	system("pause");
	return 0;
  }
  ```
##### 普通函数与函数模板的区别
- 区别：
  - 普通函数调用时可以发生自动类型转换（隐式类型转换）
  - 函数模板调用时，如果利用自动类型推导，不会发生隐式类型转换
  - 如果利用显示指定类型的方式，可以发生隐式类型转换
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;

  //普通函数与函数模板区别

  //1、普通函数调用可以发生隐式类型转换

  //2、函数模板 用自动类型推导，不可以发生隐式类型转换

  //3、函数模板 用显示指定类型，可以发生隐式类型转换

  //普通函数
  int myAdd01(int a, int b)
  {
	return a + b;
  }

  //函数模板
  template<typename T>
  T myAdd02(T a, T b)
  {
	return a + b;
  }

  //测试
  void test01()
  {
	int a = 10;
	int b = 20;

	char c = 'c';
	//区别 1
	cout << myAdd01(a, c) << endl;

	//自动类型推导  不可以发生隐式类型转换
	//cout << myAdd02(a, c) << endl;;

	//显示指定类型  可以发生隐式类型转换
	cout << myAdd02<int>(a, c) << endl;
  }

  int main()
  {
	//测试
	test01();

	system("pause");
	return 0;
  }
  ```
##### 普通函数与函数模板的调用规则
- 调用规则如下：
  - 如果函数模板和普通函数都可以实现，优先调用普通函数
  - 可以通过空模板参数列表来强制调用函数模板
  - 函数模板也可以发生重载
  - 如果函数模板可以产生更好的匹配，优先调用函数模板
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;

  //普通函数与函数模板调用规则
  //1、如果函数模板和普通函数都可以实现，优先调用普通函数
  //2、可以通过空模板参数列表来强制调用函数模板
  //3、函数模板也可以发生重载
  //4、如果函数模板可以产生更好的匹配，优先调用函数模板

  void myPrint(int a, int b)
  {
    cout << "调用的普通函数" << endl;
  }

  template<typename T>
  void myPrint(T a, T b)
  {
    cout << "调用的模板函数" << endl;
  }

  template<typename T>
  void myPrint(T a, T b, T c)
  {
    cout << "调用的模板函数" << endl;
  }

  //测试
  void test01()
  {
    int a = 10;
    int b = 20;
    int c = 30;

    //1、如果函数模板和普通函数都可以实现，优先调用普通函数
    //myPrint(a, b);

    //2、通过空模板参数列表来强制调用函数模板
    //myPrint<>(a, b);

    //3、函数模板也可以发生重载
    //myPrint(a, b, c);

    //4、如果函数模板可以产生更好的匹配，优先调用函数模板
    char c1 = 'a';
    char c2 = 'b';
    myPrint(c1, c2);
  }

  int main()
  {
    //测试
    test01();

    system("pause");
    return 0;
  }
  ```
##### 模板的局限性
- 局限性
  - 模板的通用性并不是万能的
- 例如：
  ```cpp
  template<typename T>
  void f(T a,T b)
  {
    a = b;
  }
  ```
- 上述代码中提供的赋值操作，如果传入的a和b是一个数组，就无法实现
- 例如：
  ```cpp
  template<typename T>
  void f(T a,T b)
  {
    if(a > b)
    {
      ...
    }
  }
  ```
- 如果T的数据类型传入的是像Person这样的自定义数据类型，也无法正常运行
- C++为了解决这种问题，提供模板的重载，可以为这些特定的类型提供具体化的模板
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //模板局限性
  //模板并不是万能的，有些特定数据类型，需要用具体化方式做特殊实现

  class Person
  {
  public:
    Person(string name, int age)
    {
      this->m_Name = name;
      this->m_Age = age;
    }
    //姓名
    string m_Name;
    //年龄
    string m_Age;
  };

  //对比两个数据是否相等函数
  template<typename T>
  bool myCompare(T& a, T& b)
  {
    if (a == b)
    {
      return true;
    }
    else
    {
      return false;
    }
  }

  //利用具体化Person的版本来实现代码，具体化优先调用
  template<> bool myCompare(Person& p1, Person& p2)
  {
    if (p1.m_Name == p2.m_Name && p1.m_Age == p2.m_Age)
    {
      return true;
    }
    else
    {
      return false;
    }
  }

  //测试
  void test01()
  {
    int a = 10;
    int b = 20;

    bool ret = myCompare(a, b);

    if (ret)
    {
      cout << "a == b" << endl;
    }
    else
    {
      cout << "a != b" << endl;
    }
  }

  //自定义类型对比
  void test02()
  {
    Person p1("Tom", 10);
    Person p2("Tom", 10);

    bool ret = myCompare(p1, p2);

    if (ret)
    {
      cout << "p1 == p2" << endl;
    }
    else
    {
      cout << "p1 != p2" << endl;
    }
  }

  int main()
  {
    //测试
    test01();

    test02();

    system("pause");
    return 0;
  }
  ```
- 总结
  - 利用具体化的模板，可以解决自定义类型的通用化
  - 学习模板并不是为了写模板，而是在STL能够运用系统提供的模板
#### 类模板
- 作用：
  - 建立一个通用类，类中的成员数据类型可以不具体制订，用一个虚拟的类型来代表
##### 类模板语法
- 语法：
  ```cpp
  template<typename T>
  类
  ```
- 解释：
  - template --- 声明创建模板
  - typename --- 表明其后面的符号是一种数据类型，可以用class代替
  - T --- 通用的数据类型，名称可以替换，通常为大写字母
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //类模板
  template<class NameType,class AgeType>
  class Person
  {
  public:
    Person(NameType name, AgeType age)
    {
      this->m_Name = name;
      this->m_Age = age;
    }

    void showPerson()
    {
      cout << "name: " << this->m_Name << "	age: " << this->m_Age << endl;
    }

    string m_Name;
    int m_Age;
  };

  //测试
  void test01()
  {
    Person<string, int> p1("孙悟空", 999);
    p1.showPerson();
  }

  int main()
  {
    //测试
    test01();

    system("pause");
    return 0;
  }
  ```
- 总结：类模板和函数模板语法相似，在声明模板template后面加类，此类称为类模板
##### 类模板与函数模板区别
- 类模板与函数模板区别主要有两点
  - 类模板没有自动类型推导的使用方式
  - 类模板在模板参数列表中可以有默认参数
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //类模板与函数模板的区别
  template<class NameType,class AgeType = int> //<默认参数列表>
  class Person
  {
  public:
    Person(NameType name, AgeType age)
    {
      this->m_Name = name;
      this->m_Age = age;
    }

    void showPerson()
    {
      cout << "name: " << this->m_Name << "	age: " << this->m_Age << endl;
    }

    string m_Name;
    int m_Age;
  };

  //1、类模板没有自动类型推导使用方法
  void test01()
  {
    //Person p1("孙悟空", 999);错误  无法用自动类型推导

    Person<string, int> p1("孙悟空", 999);  //正确   只能用显式指定类型
    p1.showPerson();
  }

  //2、类模板在模板参数列表中可以有默认参数
  void test02()
  {
    Person<string> p2("猪八戒", 1000); //类模板中的模板参数列表  可以指定默认参数
    p2.showPerson();
  }

  int main()
  {
    //测试
    test01();
    test02();

    system("pause");
    return 0;
  }
  ```
- 总结：
  - 类模板使用只能用显示指定类型方式
  - 模板中的模板参数列表可以有默认参数
##### 类模板中成员函数创建时机
- 类模板中成员函数和普通类中成员函数创建时机是有区别的：
  - 普通类中的成员函数一开始就可以创建
  - 类模板中的成员函数在调用时才创建
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //类模板中成员函数创建时机
  //类模板中成员函数在调用时采取创建

  class Person1
  {
  public:
    void showPerson1()
    {
      cout << "Person1 show" << endl;
    }
  };

  class Person2
  {
  public:
    void showPerson2()
    {
      cout << "Person2 show" << endl;
    }
  };

  template<class T>
  class MyClass
  {
  public:
    T obj;

    //类模板中的成员函数并不是一开始就创建的，而是在模板调用时再生成
    void func1()
    {
      obj.showPerson1();
    }

    void func2()
    {
      obj.showPerson2();
    }
  };

  void test01()
  {
    MyClass<Person1>m;
    m.func1();
    //m.func2();   //编译会出错，说明函数调用才会去创建成员函数
  }

  int main()
  {
    //测试
    test01();
    
    system("pause");
    return 0;
  }
  ```
##### 类模板对象做函数参数
- 类模板实例化出的对象，向函数传参的方式
- 一共有三种传入方式：
  - 指定传入的类型 --- 直接显示对象的数据类型
  - 参数模板化 --- 将对象中的参数变为模板进行传递
  - 整个类模板化 --- 将这个对象类型模板化进行传递
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //类模板的对象做函数参数
  template<class T1,class T2>
  class Person
  {
  public:
      Person(T1 name, T2 age)
      {
          this->m_Name = name;
          this->m_Age = age;
      }

      void showPerson()
      {
          cout << "姓名：" << this->m_Name << " 年龄：" << this->m_Age << endl;
      }

      T1 m_Name;
      T2 m_Age;

  };

  //1、指定传入类型
  void printPerson01(Person<string, int>&p)
  {
      p.showPerson();
  }

  void test01()
  {
      Person<string, int> p("孙悟空", 999); 
      printPerson01(p);
  }

  //2、参数模板化
  template<class T1,class T2>
  void printPerson02(Person<T1, T2>&p2)
  {
      p2.showPerson();
      cout << "T1 的类型为：" << typeid(T1).name() << endl;
      cout << "T2 的类型为：" << typeid(T2).name() << endl;
  }

  void test02()
  {
      Person<string, int> p2("猪八戒", 1000);
      printPerson02(p2);
  }

  //3、整个类模板化
  template<class T>
  void printPerson03(T &p)
  {
      p.showPerson();
      cout << "T 的类型为：" << typeid(T).name() << endl;
  }

  void test03()
  {
      Person<string, int> p3("唐僧", 30);
      printPerson03(p3);
  }


  int main()
  {
      //测试
      test01();

      test02();

      test03();

      system("pause");
      return 0;
  }
  ```
- 总结：
  - 通过类模板创建的对象，可以有三种方式向函数中进行传参
  - 使用比较广泛是第一种：指定传入的类型
##### 类模板与继承
- 当类模板碰到继承时，需要注意以下几点：
  - 当子类继承的父类是一个类模板时，子类在声明的时候，要指定出父类中T的类型
  - 如果不指定，编译器无法给子类分配内存
  - 如果想灵活指定出父类中T的类型，子类也需变为类模板
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //类模板与继承
  template<class T>
  class Base
  {
      T m;
  };

  //class Son :public Base  //错误，必须要知道父类中的T类型，才能继承给子类
  class Son:public Base<int>
  {

  };

  void test01()
  {
      Son s1;
  }

  //如果想灵活指定父类中T类型，子类也需要变类模板
  template<class T1,class T2>
  class Son2 :public Base<T2>
  {
  public:
      Son2()
      {
          cout << "T1的类型为：" << typeid(T1).name() << endl;
          cout << "T2的类型为：" << typeid(T2).name() << endl;
      }
      T1 obj;
  };

  void test02()
  {
      Son2<int, char>S2;
  }

  int main()
  {
      //测试
      test01();
      test02();
      system("pause");
      return 0;
  }
  ```
##### 类模板成员函数类外实现
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //类模板与继承
  template<class T1,class T2>
  class Person
  {
  public:
      //成员函数类内声明
      Person(T1 name, T2 age);
      /*{
          this->m_Name = name;
          this->m_Age = age;
      }*/

      void showPerson()
      /*{
          cout << "姓名：" << this->m_Name << " 年龄：" << this->m_Age << endl;
      }*/

      T1 m_Name;
      T2 m_Age;
  };

  //构造函数 类外实现
  template<class T1,class T2>
  Person<T1,T2>::Person(T1 name, T2 age)
  {
      this->m_Name = name;
      this->m_Age = age;
  }

  //成员函数 类外实现
  template<class T1, class T2>
  void Person<T1,T2>::showPerson()
  {
      cout << "姓名：" << this->m_Name << " 年龄：" << this->m_Age << endl;
  }

  void test01()
  {
      Person<string, int> p("tom", 20);
      p.showPerson();
  }

  int main()
  {
      //测试
      test01();
    
      system("pause");
      return 0;
  }
  ```
- 总结：类模板中成员函数类外实现时，需要加上模板参数列表
##### 类模板份文件编写
- 类模板成员函数分文件编写产生的问题以及解决方式
- 问题：
  - 类模板中成员函数创建时机是在调用阶段，导致分文件编写时链接不到
- 解决：
  - 解决方式1：直接包含.cpp源文件
  - 解决方式2：将声明和实现写到同一个文件中，并更改后缀名为.hpp，hpp是约定的名称，并不是强制
- 示例：
  person.hpp代码：
  ```cpp
  #pragma once
  #include<iostream>
  using namespace std;
  #include<string>

  //类模板分文件编写问题以及解决
  template<class T1, class T2>
  class Person
  {
  public:

      Person(T1 name, T2 age);
      /*{
          this->m_Name = name;
          this->m_Age = age;
      }*/

      void showPerson();
      /*{
          cout << "姓名：" << this->m_Name << " 年龄：" << this->m_Age << endl;
      }*/

      T1 m_Name;
      T2 m_Age;
  };

  //构造函数类外实现
  template<class T1, class T2>
  Person<T1, T2>::Person(T1 name, T2 age)
  {
      this->m_Name = name;
      this->m_Age = age;
  }

  //成员函数类外实现
  template<class T1, class T2>
  void Person<T1, T2>::showPerson()
  {
      cout << "姓名：" << this->m_Name << " 年龄：" << this->m_Age << endl;
  }
  ```
  main主函数入口.cpp
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  //第一种解决方式，直接包含 源文件
  #include"person.cpp"

  //第二种解决方式，将.h和.cpp种的内容写到一起，将后缀名改为.hpp文件
  #include"person.hpp"

  //#include<string>
  //
  ////类模板分文件编写问题以及解决
  //template<class T1,class T2>
  //class Person
  //{
  //public:
  //
  //    Person(T1 name, T2 age);
  //    /*{
  //        this->m_Name = name;
  //        this->m_Age = age;
  //    }*/
  //
  //    void showPerson();
  //    /*{
  //        cout << "姓名：" << this->m_Name << " 年龄：" << this->m_Age << endl;
  //    }*/
  //
  //    T1 m_Name;
  //    T2 m_Age;
  //};

  ////构造函数类外实现
  //template<class T1,class T2>
  //Person<T1,T2>::Person(T1 name, T2 age)
  //{
  //    this->m_Name = name;
  //    this->m_Age = age;
  //}
  //
  ////成员函数类外实现
  //template<class T1, class T2>
  //void Person<T1,T2>::showPerson()
  //{
  //    cout << "姓名：" << this->m_Name << " 年龄：" << this->m_Age << endl;
  //}

  void test01()
  {
      Person<string, int> p("tom", 20);
      p.showPerson();
  }

  int main()
  {
      //测试
      test01();
    
      system("pause");
      return 0;
  }
  ```
- 总结：主流的解决方式是第二种，将类模板成员函数写到一起，并将后缀名改为.hpp
##### 类模板与友元
- 类模板配合友元函数的类内和类外实现
- 全局函数雷内实现 - 直接在类内声明友元即可
- 全局函数类外实现 - 需要提前让编译器知道全局函数的存在
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //通过全局函数配合友元  打印Person信息

  //提前让编译器知道Person类存在
  //先做函数模板声明，下方再做函数模板定义，再做友元
  template<class T1,class T2>
  class Person;

  //全局函数  类外实现  可以先声明函数模板，让编译器提前知道这个函数的存在
  template<typename T1, typename T2>
  void PrintPerson2(Person<T1, T2>p);

  template<typename T1,typename T2>
  class Person
  {
      //全局函数  类内实现
      friend void PrintPerson(Person<T1, T2>p)
      {
          cout << "姓名：" << p.m_Name << " 年龄：" << p.m_Age << endl;
      }

      //全局函数  类外实现
      //加空模板参数列表 【 < > 】
      //如果全局函数  是类外实现，需要让编译器提前知道这个函数的存在
      friend void PrintPerson2<>(Person<T1,T2>p);

  public:
      Person(T1 name, T2 age)
      {
          this->m_Name = name;
          this->m_Age = age;
      }

  private:
      T1 m_Name;
      T2 m_Age;
  };

  //全局函数  类外实现
  template<typename T1, typename T2>
  void PrintPerson2(Person<T1, T2>p)
  {
      cout << "类外实现---姓名：" << p.m_Name << " 年龄：" << p.m_Age << endl;
  }

  //1、全局函数在类内实现
  void test01()
  {
      Person<string, int>p("Tom", 20);
      PrintPerson(p);
  }

  //2、全局函数在类外实现
  void test02()
  {
      Person<string, int>p1("Cat", 5);
      PrintPerson2(p1);
  }

  int main()
  {
      //测试
      test01();
      test02();
    
      system("pause");
      return 0;
  }
  ```
- 总结：建议全局函数做类内实现，用法简单，而且编译器可以直接识别
##### 类模板案例
- 案例描述：实现一个通用的数组类，要求如下
  - 可以对内置数据类型以及自定义数据类型的数据进行存储
  - 将数组中的数据存储到堆区
  - 构造函数中可以传入数组的容量
  - 提供对应的拷贝构造函数以及operator=防止浅拷贝问题
  - 提供尾插法和尾删法对数组中的数据进行增加和删除
  - 可以通过下标的方式访问数组中的元素
  - 可以获取数组中当前元素个数和数组的容量
- 示例：
  MyArray.hpp
  ```cpp
  //自己通用的数组类
  #pragma once
  #include<iostream>
  using namespace std;

  template<class T>
  class MyArray
  {
  public:
    //有参构造  参数 容量
    MyArray(int capacity)
    {
      cout << "MyArray 有参构造调用" << endl;
      this->m_Capacity = capacity;
      this->m_Size = 0;
      this->pAddress = new T[capacity];
    }

    //拷贝构造
    MyArray(const MyArray& arr)
    {
      cout << "MyArray 拷贝构造调用" << endl;
      this->m_Capacity = arr.m_Capacity;
      this->m_Size = arr.m_Size;

      //浅拷贝的问题会导致堆区数据重复释放
      //this->pAddress = arr.pAddress;

      //深拷贝
      this->pAddress = new T[arr.m_Capacity];

      //将arr中的数据都拷贝过来
      for (int i = 0; i < this->m_Size; i++)
      {
        //如果T为对象，而且还包含指针，必须重载【=】操作符，因为这个等号不是构造而是赋值
        //普通类型可以直接【=】，但是指针类型需要深拷贝
        this->pAddress[i] = arr.pAddress[i];
      }
    }

    //operator= 防止浅拷贝问题
    MyArray& operator=(const MyArray &arr)
    {
      cout << "MyArray 的operator=调用" << endl;
      //先判断原来堆区是否有数据，如果有先释放
      if (this->pAddress != NULL)
      {
        delete[]this->pAddress;
        this->pAddress = NULL;
        this->m_Capacity = 0;
        this->m_Size = 0;
      }

      //深拷贝
      this->m_Capacity = arr.m_Capacity;
      this->m_Size = arr.m_Size;
      this->pAddress = new T[arr.m_Capacity];
      for (int i = 0; i < this->m_Size; i++)
      {
        this->pAddress[i] = arr.pAddress[i];
      }
      return *this;
    }
    
    //尾插法
    void Push_Back(const T& val)
    {
      //先判断容量时候等于大小
      if (this->m_Capacity == this->m_Size)
      {
        return;
      }
      this->pAddress[this->m_Size] = val;  //再数组末尾插入数据
      this->m_Size++;//更新数组长度
    }

    //尾删法
    void Pop_Back()
    {
      //让用户访问不到最后一个元素，即为尾删，逻辑删除
      if (this->m_Size == 0) //判断数组长度是否为0，如果为0，代表数组无数据
      {
        return;
      }

      this->m_Size--; //更新数组长度

    }

    //通过下标方式访问数组中的元素  函数调用返回一个左值，需要返回一个引用【&】
    //重载【 [] 】操作符 arr[0]
    T& operator[](int index)
    {
      return this->pAddress[index];//不考虑越界，用户自己去处理
    }

    // 返回数组容量
    int getCapacity()
    {
      return this->m_Capacity;
    }

    //返回数组长度
    int getSize()
    {
      return this->m_Size;
    }

    //析构函数
    ~MyArray()
    {
      cout << "MyArray 析构调用" << endl;
      if (this->pAddress != NULL)
      {
        delete[]this->pAddress;
        this->pAddress = NULL;
      }
    }

  private:
    T* pAddress;//指针指向堆区开辟的真实数组
    int m_Capacity;//数组容量
    int m_Size;//数组长度
  };
  ```
  主函数.cpp
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include"MyArray.hpp"

  //打印函数  引用传递方式
  void printInArray(MyArray<int>& arr)
  {
      //i < MyArray里面的getm_Size的int类型返回值
      for (int i = 0; i < arr.getSize(); i++)
      {
          cout << arr[i] << endl;
      }
  }


  //1、全局函数在类内实现
  void test01()
  {
      //创建一个MyArry类型数组 传入变量类型为int  数组容量为5
      MyArray <int>arr1(5);
      for (int i = 0; i < 5; i++)
      {
          //利用尾插法向数组中插入数据
          //传入i的值
          arr1.Push_Back(i);
      }
      cout << "arr1的打印输出：" << endl;
      //向打印函数中传数组  
      printInArray(arr1);
      //查看数组容量与长度
      cout << "arr1的容量为：" << arr1.getCapacity() << endl;
      cout << "arr1的长度为：" << arr1.getSize() << endl;

      //创建一个MyArry类型数组 传入变量类型为int arr2数组值等于arr1数组的值  深拷贝 new一个新空间
      MyArray<int>arr2(arr1);

      //尾删
      arr2.Pop_Back();
      printInArray(arr2);
      cout << "arr2尾删后：" << endl;
      cout << "arr2的容量为：" << arr2.getCapacity() << endl;
      cout << "arr2的长度为：" << arr2.getSize() << endl;

      //创建一个MyArry类型数组 传入变量类型为int  数组容量为100
      MyArray<int>arr3(100);
      ////创建一个MyArry类型数组 传入变量类型为int arr3数组值等于arr1数组的值  深拷贝 new一个新空间 operator= 防止浅拷贝问题
      arr3 = arr1;
  }

  //测试自定义数据类型
  class Person
  {
  public:

      Person() {};
      Person(string name, int age)
      {
          this->m_Name = name;
          this->m_Age = age;
      }

      string m_Name;
      int m_Age;
  };

  //打印数组
  void printPersonArray(MyArray<Person>&arr)
  {
      for (int i = 0; i < arr.getSize(); i++)
      {
          cout << "姓名：" << arr[i].m_Name << " 年龄：" << arr[i].m_Age << endl;
      }
  }

  void test02()
  {
      MyArray<Person>arr(10);
      Person p1("孙悟空", 999);
      Person p2("韩信", 30);
      Person p3("妲己", 20);
      Person p4("赵云", 25);
      Person p5("安其拉", 27);

      //将数据插入到数组中
      arr.Push_Back(p1);
      arr.Push_Back(p2);
      arr.Push_Back(p3);
      arr.Push_Back(p4);
      arr.Push_Back(p5);
      //打印函数调用
      printPersonArray(arr);
      //输出容量
      cout << "arr容量为：" << arr.getCapacity() << endl;
      //输出长度
      cout << "arr长度为：" << arr.getSize() << endl;

  }

  int main()
  {
      //测试
      test01();
      test02();
    
      system("pause");
      return 0;
  }
  ```
  打印结果：
  ```cpp
  0
  1
  2
  3
  4
  arr1的容量为：5
  arr1的长度为：5
  MyArray 拷贝构造调用
  0
  1
  2
  3
  arr2尾删后：
  arr2的容量为：5
  arr2的长度为：4
  MyArray 有参构造调用
  MyArray 的operator=调用
  MyArray 析构调用
  MyArray 析构调用
  MyArray 析构调用
  MyArray 有参构造调用
  姓名：孙悟空 年龄：999
  姓名：韩信 年龄：30
  姓名：妲己 年龄：20
  姓名：赵云 年龄：25
  姓名：安其拉 年龄：27
  arr容量为：10
  arr长度为：5
  MyArray 析构调用
  ```
- 总结：能够利用所学知识点实现通用的数组
### STL初识
#### STL的诞生
- 软件界一直希望建立一种可重复利用的东西
- C++的面向对象和泛型编程思想，目的就是复用性的提升
- 数据结构和算法都未能有一套标准，导致被迫从事大量重复工作
- 建立数据结构和算法的一套标准，诞生了STL
#### STL基本概念
- STL(Standard Template Library,标准模板库)
- STL从广义上分为：容器(container)算法(algorithm)迭代器(iterator)
- 容器和算法之间通过迭代器进行无缝连接
- STL几乎所有的代码都采用了模板类或者模板函数
#### STL六大组件
- STL答题分为六大组件，分别是：容器、算法、迭代器、仿函数、适配器(配接器)、空间配置器
  - 容器：各种数据结构，如vector、list、deque、set、map等，用来存放数据
  - 算法：各种常用的算法，如sort、find、copy、for_each等
  - 迭代器：扮演了容器与算法之间的胶合剂
  - 仿函数：行为类似函数，可作为算法的某种策略
  - 适配器：一种用来修饰容器或者仿函数或迭代器接口的东西
  - 空间配置器：负责空间的配置与管理
#### STL中容器、算法、迭代器
- 容器：置物之所也
- STL容器就是将运用最广泛的一些数据结构实现出来
- 常用的数据结构：数组、链表、树、栈、队列、集合、映射表等
- 这些容器分为序列式容器和关联式容器两种
  - 序列式容器：强调值的排序，序列式容器中的每个元素均有固定的位置
  - 关联式容器：二叉树结构，各元素之间没有严格的物理上的顺序关系
- 算法：问题之解法也
- 有限的步骤，解决逻辑或数学上的问题，这一门学科我们叫做算法(Algorithms)
- 算法分为质变算法和非质变算法
  - 质变算法：是指运算过程中会更改区间内的元素的内容。例如拷贝、替换、删除等
  - 非质变算法：是指运算过程中不会更改区间内的元素内容，例如查找、计数、遍历、寻找极值等等
- 迭代器：容器和算法之间粘合剂
- 提供一种方法，使之能够依序寻访某个容器所含的各个元素，而又无需暴露该容器的内部表示方式
- 每个容器都有自己专属的迭代器
- 迭代器使用非常类似于指针，初学阶段我们可以先理解迭代器为指针
- 迭代器种类

| 种类           | 功能                                                   | 支持运算                        |
|--------------|------------------------------------------------------|-----------------------------|
| 输入迭代器     | 对数据的只读访问                                       | 只读，支持++、==、!=               |
| 输出迭代器     | 对数据的只写访问                                       | 只写、支持++                     |
| 前向迭代器     | 读写操作，并能向前推进迭代器                            | 读写、支持++、==、!=               |
| 双向迭代器     | 读写操作，并能向前和向后操作                            | 读写，支持++、--                  |
| 随机访问迭代器 | 读写操作，可以以跳跃的方式访问任意数据，功能最强的迭代器 | 读写，支持++、--、[n]、-n、<、<=、>、>= |

- 常用的容器种迭代器种类为双向迭代器，和随机访问迭代器
#### 容器算法迭代器初识
- STL中最常用的容器为vector，可以理解为数组，下面我们将学习如果向这个容器中插入数据，并遍历这个容器
##### vector存放内置数据类型
- 容器：vector
- 算法：for_each
- 迭代器：vector<int>::iterator
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<vector>
  #include<algorithm>  //标准算法头文件

  //vector容器存放内置数据类型
  void myPrint(int val)
  {
    cout << val << endl;
  }

  void test01()
  {
    //创建一个vector容器，数组   需要包含#include<vector>  vector的头文件
    vector<int> v;

    //向容器中插入数据
    v.push_back(10);
    v.push_back(20);
    v.push_back(30);
    v.push_back(40);
    v.push_back(50);

    
    //通过迭代器访问容器中的数据
    //vector<int>::iterator 拿到vector<int>这种容器的迭代器类型
    vector<int>::iterator itBegin = v.begin();  //起始迭代器 指向容器中第一个元素
    vector<int>::iterator itEnd = v.end();  //结束迭代器，指向容器中最后一个元素的下一个位置

    //第一种遍历方式
    while (itBegin != itEnd)
    {
      cout << *itBegin << endl;
      itBegin++;
    }
    cout << endl;

    //第二种遍历方式
    for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
    {
      cout << *it << endl;
    }
    cout << endl;

    //第三章遍历方式  利用STL提供遍历算法
    for_each(v.begin(), v.end(), myPrint);

  }

  int main()
  {
    //测试
    test01();

    system("pause");
    return 0;
  }
  ```
  运行结果
  ```cpp
  10
  20
  30
  40
  50

  10
  20
  30
  40
  50

  10
  20
  30
  40
  50
  ```
##### vector存放自定义数据类型
- 学习目标：vector中存放自定义数据类型，并打印输出
- 示例
  ```cpp
  #include<iostream>
  using namespace std;
  #include<vector>
  #include<algorithm>  //标准算法头文件
  #include<string>

  //vector容器存放自定义数据类型
  class Person
  {
  public:
    Person(string name, int age)
    {
      this->m_Name = name;
      this->m_Age = age;
    }

    string m_Name;
    int m_Age;
  };

  void test01()
  {
    vector<Person> v;

    Person p1("aaa", 10);
    Person p2("bbb", 15);
    Person p3("ccc", 20);
    Person p4("ddd", 25);
    Person p5("eee", 30);

    //向容器中添加数据
    v.push_back(p1);
    v.push_back(p2);
    v.push_back(p3);
    v.push_back(p4);
    v.push_back(p5);

    //遍历容器中的数据
    cout << "自定义类型存数据" << endl;
    for (vector<Person>::iterator it = v.begin(); it != v.end(); it++)
    {
      cout << "*解引用  姓名：" << (*it).m_Name << " 年龄：" << (*it).m_Age << endl;
      cout << "this指针 姓名：" << it->m_Name << " 年龄：" << it->m_Age << endl;
      cout << endl;
    }
  }

  //存放指定值数据类型  指针
  void test02()
  {
    vector<Person*> v;

    Person p1("aaa", 10);
    Person p2("bbb", 15);
    Person p3("ccc", 20);
    Person p4("ddd", 25);
    Person p5("eee", 30);

    //向容器中添加数据  传址
    v.push_back(&p1);
    v.push_back(&p2);
    v.push_back(&p3);
    v.push_back(&p4);
    v.push_back(&p5);

    //遍历容器
    cout << endl;
    cout << "自定义类型存地址" << endl;
    for (vector<Person*>::iterator it = v.begin(); it != v.end(); it++)
    {
      cout << "this指针 姓名：" << (*it)->m_Name << " 年龄：" << (*it)->m_Age << endl;
      cout << "*解引用  姓名：" << (*(*it)).m_Name << " 年龄：" << (*(*it)).m_Age << endl;
      cout << endl;
    }
  }

  int main()
  {
    //测试
    test01();
    test02();

    system("pause");
    return 0;
  }
  ```
  运行结果
  ```cpp
  *解引用  姓名：bbb 年龄：15
  this指针 姓名：bbb 年龄：15

  *解引用  姓名：ccc 年龄：20
  this指针 姓名：ccc 年龄：20

  *解引用  姓名：ddd 年龄：25
  this指针 姓名：ddd 年龄：25

  *解引用  姓名：eee 年龄：30
  this指针 姓名：eee 年龄：30


  自定义类型存地址
  this指针 姓名：aaa 年龄：10
  *解引用  姓名：aaa 年龄：10

  this指针 姓名：bbb 年龄：15
  *解引用  姓名：bbb 年龄：15

  this指针 姓名：ccc 年龄：20
  *解引用  姓名：ccc 年龄：20

  this指针 姓名：ddd 年龄：25
  *解引用  姓名：ddd 年龄：25

  this指针 姓名：eee 年龄：30
  *解引用  姓名：eee 年龄：30
  ```
##### vector容器嵌套容器
- 容器中嵌套容器，将所有数据进行遍历输出
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<vector>
  #include<algorithm>  //标准算法头文件
  #include<string>

  //vector容器嵌套容器
   void test01()
  {
    vector<vector<int>> v;

    //创建小容器
    vector<int> v1;
    vector<int> v2;
    vector<int> v3;
    vector<int> v4;

    //向小容器中添加数据
    for (int i = 0; i < 4; i++)
    {
      v1.push_back(i + 1);
      v2.push_back(i + 2);
      v3.push_back(i + 3);
      v4.push_back(i + 4);
    }

    //将小容器插入到大容器中
    v.push_back(v1);
    v.push_back(v2);
    v.push_back(v3);
    v.push_back(v4);

    //通过大容器，把所有数据遍历
    for (vector<vector<int>>::iterator it = v.begin(); it != v.end(); it++)
    {
      //  (*it) --- 指的是容器vector<int>
      for (vector<int>::iterator vit = (*it).begin(); vit != (*it).end(); vit++)
      {
        cout << *vit << " ";
      }
      cout << endl;
    }

  }

  int main()
  {
    //测试
    test01();

    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  1 2 3 4
  2 3 4 5
  3 4 5 6
  4 5 6 7
  ```
### STL-常用容器
#### string容器
##### string基本概念
- 本质：
  - string是C++风格的字符串，而string本质上是一个类
- string和char * 区别：
  - char *是一个指针
  - string是一个类，类内部封装了char*，管理这个字符串，是一个char*型容器
- 特点：
  - string类内部封装了很多成员方法
  - 例如：查找find、拷贝copy、删除delete、替换replace、插入insert
  - string管理char*所分配的内存，不用担心复制越界和取值越界等，由类内部进行负责
##### string构造函数
- string();                     //创建一个空的字符串 例如：string str;
- string(const char * s);       //使用字符串s初始化
- string(const string & str);   //使用一个string对象初始化另一个string对象
- string(int n,char c);         //使用n个字符c初始化
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //string构造函数
  void test01()
  {
    //默认构造
    string s1;

    //初始化
    const char* str = "hello world";
    string s2(str);

    cout << "s2 = " << s2 << endl;

    //拷贝构造
    string s3(s2);
    cout << "s3 = " << s3 << endl;

    ////使用n个字符初始化
    string s4(10, 'a');
    cout << "s4 = " << s4 << endl;
  }

  int main()
  {
    //测试
    test01();

    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  s2 = hello world
  s3 = hello world
  s4 = aaaaaaaaaa
  ```
- 总结：string的多种构造方式没有可比性，灵活使用即可
##### string赋值操作
- 功能描述：给string字符串进行赋值
- 赋值的函数原型
  - string& openator=(const char* s);   //char*类型字符串  赋值给当前的字符串
  - string& openator=(const string &s)  //把字符串s赋值给当前的字符串
  - string& openator=(char c);          //字符赋值给当前的字符串
  - string& assign(const char *s);      //把字符串s赋给当前的字符串
  - string& assign(const char *s,int n);//把字符串s的前n个字符赋给当前的字符串
  - string& assign(const string &s);    //把字符串s赋给当前字符串
  - string& assign(int n,char c);       //把n个字符c赋给当前字符串
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //string赋值操作
  void test01()
  {
    //第一种方法
    string str1;
    str1 = "hello world";
    cout << "第一种方法  str1 = " << str1 << endl;

    //第二种方法
    string str2;
    str2 = str1;
    cout << "第二种方法  str2 = " << str2 << endl;

    //第三种方法
    string str3;
    str3 = 'a';
    cout << "第三种方法  str3 = " << str3 << endl;

    //第四种方法
    string str4;
    str4.assign("hello C++");
    cout << "第四种方法  str4 = " << str4 << endl;

    //第五种方法
    string str5;
    str5.assign("hello C++", 5);
    cout << "第五种方法  str5 = " << str5 << endl;

    //第六种方法
    string str6;
    str6.assign(str5);
    cout << "第六种方法  str6 = " << str6 << endl;

    //第七种方法
    string str7;
    str7.assign(10, 'w');
    cout << "第七种方法  str7 = " << str7 << endl;

  }

  int main()
  {
    //测试
    test01();

    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  第一种方法  str1 = hello world
  第二种方法  str2 = hello world
  第三种方法  str3 = a
  第四种方法  str4 = hello C++
  第五种方法  str5 = hello
  第六种方法  str6 = hello
  第七种方法  str7 = wwwwwwwwww
  ```
- 总结：string的赋值方式很多，一般 operator= 的方式比较实用
##### 字符串拼接
- 实现在字符串末尾凭借字符串
- 函数原型
  - string& operator+=(const char* str);    //重载+=操作符
  - string& operator+=(const char str);     //重载+=操作符
  - string& operator+=(const string* str);  //重载+=操作符
  - string& append(const char* s);          //把字符串s连接到当前字符串结尾
  - string& append(const char* s,int n);    //把字符串s的前n个字符连接到当前字符串结尾
  - string& append(const string& s);        //同operator+=(const String& str);
  - string& append(const string& s,int pos,int n);//把字符串s中从pos开始的n个字符连接到字符串结尾
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //string字符串拼接
  void test01()
  {
    string str1 = "我";

    //第一种用法
    str1 += "爱玩游戏";
    cout << "第一种方法 str1 = " << str1 << endl;

    //第二种方法
    str1 += "：";
    cout << "第二种方法 str1 = " << str1 << endl;

    //第三种方法
    string str2 = "LOL DNF";
    str1 += str2;
    cout << "第三种方法 str1 = " << str1 << endl;

    //第四种方法
    string str3 = "I";
    str3.append(" Love ");
    cout << "第四种方法 str1 = " << str3 << endl;

    //第五种方法
    str3.append("game: abcde", 5);
    cout << "第五种方法 str1 = " << str3 << endl;

    //第六种方法
    str3.append(str2);
    cout << "第六种方法 str1 = " << str3 << endl;

    //第七种方法
    string str4 = " CF DATA2";
    str3.append(str4, 0, 4);     //只截取string字符串的元素下标0-4的字符
    cout << "第七种方法 str1 = " << str3 << endl;

  }

  int main()
  {
    //测试
    test01();

    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  第一种方法 str1 = 我爱玩游戏
  第二种方法 str1 = 我爱玩游戏：
  第三种方法 str1 = 我爱玩游戏：LOL DNF
  第四种方法 str1 = I Love
  第五种方法 str1 = I Love game:
  第六种方法 str1 = I Love game:LOL DNF
  第七种方法 str1 = I Love game:LOL DNF CF
  ```
##### string查找和替换
- 功能描述
  - 查找：查找指定字符串是否存在
  - 替换：在指定的位置替换字符串
- 函数原型：
  - int find(const string& str,int pos = 0) const;    //查找str第一次出现位置，从pos开始查找
  - int find(const char* s,int pos = 0) const;        //查找s第一次出现位置，从pos开始查找
  - int find(const char* s,int pos,int n) const;      //从pos位置查找s的前n个字符第一次位置
  - int find(const char c,int pos = 0) const;         //查找字符c第一次出现位置
  - int rfind(const string& str,int pos = npos) const;//查找str最后一次位置，从pos开始查找
  - int rfind(const char* s,int pos = npos) const;    //查找s最后一次出现位置，从pos开始查找
  - int rfind(const char* s,int pos,int n) const;     //从pos查找s的前n个字符最后一次位置
  - int rfind(const char s,int pos = 0) const;        //查找字符c最后一次出现位置
  - string& replace(int pos,int a,const string& str); //替换从pos开始n个字符为字符串str
  - string& replace(int pos,int a,const char* s);     //替换从pos开始的n个字符为字符串s
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //string字符串查找和替换

  //1、查找
  void test01()
  {
    string str1 = "abcdefgde";
    //第一种方法  从头开始查找字符c在当前字符串的位置
    int pos = str1.find("de");

    //通常要判断一下
    if (pos == -1)  //未找到返回值为-1  pos值如果为-1  代表未找到
    {
      cout << "未找到字符串" << endl;
    }
    else
    {
      cout << "第一种方法  pos = " << pos << endl;  //返回第一次出现的下标位置
    }

    //第一种方法find与第五种方法rfind
    //区别：rfind从右往左查找  find从左往右查找
    pos = str1.rfind("de");
    if (pos == -1)
    {
      cout << "未找到字符串" << endl;
    }
    else
    {
      cout << "第五种方法  pos = " << pos << endl;
    }
    //第二种方法  从pos开始查找字符串s在当前串中的位置
    pos = str1.find("f", 0);
    if (pos == -1)
    {
      cout << "未找到字符串" << endl;
    }
    else
    {
      cout << "第二种方法  pos = " << pos << endl;
    }
    
    //第二种方法  从pos开始查找字符串s在当前串中的位置
    pos = str1.find("f", 2);
    if (pos == -1)
    {
      cout << "未找到字符串" << endl;
    }
    else
    {
      cout << "第二种方法  pos = " << pos << endl;
    }

    //第三种方法
    //从str1元素下标0的位置开始查找字符串"fgsk"前2位字符在当前串中的位置
    pos = str1.find("fgsk", 0, 2);
    if (pos == -1)
    {
      cout << "未找到字符串" << endl;
    }
    else
    {
      cout << "第三种方法  pos = " << pos << endl;
    }

    //第四种方法  从pos开始查找字符c在当前串中第一次出现的位置
    pos = str1.find('d');
    if (pos == -1)
    {
      cout << "未找到字符串" << endl;
    }
    else
    {
      cout << "第四种方法  pos = " << pos << endl;
    }

    //第六种方法   元素下标【5】开始从右往左查找最后一次的位置
    pos = str1.rfind("d", 5);
    if (pos == -1)
    {
      cout << "未找到字符串" << endl;
    }
    else
    {
      cout << "第六种方法  pos = " << pos << endl;
    }

    //第六种方法  第二次查找   从右往左查找第一个字符【d】
    pos = str1.rfind("d");
    if (pos == -1)
    {
      cout << "未找到字符串" << endl;
    }
    else
    {
      cout << "第六种方法  pos = " << pos << endl;
    }

    //第七种方法   查找字符串的前两个字符  从最后一次位置开始  str1.size()表示最后一次位置
    pos = str1.rfind("defg", str1.size(), 2);
    if (pos == -1)
    {
      cout << "未找到字符串" << endl;
    }
    else
    {
      cout << "第七种方法  pos = " << pos << endl;
    }

    //第八种方法  从右往左查找字符第一次出现的位置 str1.size()表示最后一个元素下标位置
    pos = str1.rfind('d',str1.size());
    if (pos == -1)
    {
      cout << "未找到字符串" << endl;
    }
    else
    {
      cout << "第八种方法  pos = " << pos << endl;
    }
  }

  //2、替换
  void test02()
  {
    //第九种方法  替换 
    string str1 = "abcdefgde";
    //从元素下标【1】开始，往后3个字符替换为“1234”
    str1.replace(1, 3, "1234");
    if (str1.size()>1)
    {
      cout << "第九种方法  替换  str1 = " << str1 << endl;
    }
    else
    {
      cout << "字符串元素下标小于1，无法完成替换" << endl;
    }

    //第十种方法  替换
    str1.replace(2, 4, "567890");
    if (str1.size() > 1)
    {
      cout << "第九种方法  替换  str1 = " << str1 << endl;
    }
    else
    {
      cout << "字符串元素下标小于1，无法完成替换" << endl;
    }

  }

  int main()
  {
    //测试
    test01();
    test02();

    system("pause");
    return 0;
  }
  ```
  运行结果
  ```cpp
  第一种方法  pos = 3
  第五种方法  pos = 7
  第二种方法  pos = 5
  第二种方法  pos = 5
  第三种方法  pos = 5
  第四种方法  pos = 3
  第六种方法  pos = 3
  第六种方法  pos = 7
  第七种方法  pos = 7
  第八种方法  pos = 7
  第九种方法  替换  str1 = a1234efgde
  第九种方法  替换  str1 = a1567890fgde
  ``` 
- 总结：
  - find查找是从左往右，rfind是从右往左
  - find找到字符串后返回查找的第一个字符位置，找不到返回-1
  - replace在替换时，要指定从哪个位置起，多少个字符，替换成什么样的字符串
##### string字符串比较
- 字符串之间的比较
- 比较方式：
  - 字符串比较是按照字符的ASCII码进行对比
  - = 返回  0
  - \> 返回  1
  - < 返回 -1
- 函数原型：
  - int compare(const string &s) const; //与字符串s比较
  - int compare(const char *s) const;   //与字符串s比较
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //string字符串比较

  void test01()
  {
    string str1 = "hello";
    string str2 = "xello";

    if (str1.compare(str2) == 0)
    {
      cout << "str1 = str2" << endl;
    }
    else if (str1.compare(str2) > 0)
    {
      cout << "strl > str2" << endl;
    }
    else
    {
      cout << "str1 < str2" << endl;
    }

  }

  int main()
  {
    //测试
    test01();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  str1 < str2
  ```
- 总结：字符串对比主要是用于比较两个字符串是否相等，判断谁大谁小的意义并不是很大
##### string字符存取
- string中单个字符存取方式有两种
  - char& operator[](int n);  //通过[]方式获取字符
  - char& at(int n);          //通过at方法获取字符
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //string字符存取

  void test01()
  {
    string str = "hello";

    cout << "str = " << str << endl << endl;

    //1、通过 [] 访问单个字符
    for (int i = 0; i < str.size(); i++)
    {
      cout << str[i] << " ";
    }
    cout << endl << endl;

    //2、通过at方式访问单个字符
    for (int i = 0; i < str.size(); i++)
    {
      cout << str.at(i) << " ";
    }
    cout << endl << endl;

    //修改单个字符
    str[0] = 'x';
    cout << "str = " << str << endl << endl;

    str.at(1) = 'x';
    cout << "str = " << str << endl << endl;
  }

  int main()
  {
    //测试
    test01();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  str = hello

  h e l l o

  h e l l o

  str = xello

  str = xxllo
  ```
- 总结：string字符串中单个字符存取有两种方式，利用[]或者at
##### string插入和删除
- 作用：对string字符串进行插入和删除字符操作
- 函数原型：
  - string& insert(int pos,const char* s);      //插入字符串
  - string& insert(int pos,const string* str);  //插入字符串
  - string& insert(int pos,int n, char c);      //在指定位置插入n个字符c
  - string& erase(int pos,int n = npos);        //删除从pos开始的n个字符
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //string字符串插入和删除

  void test01()
  {
    string str = "hello";

    //插入
    str.insert(1, "222");
    cout << str << endl;

    str.insert(4, 3, '6');
    cout << str << endl;

    //删除
    str.erase(1, 6);
    cout << str << endl;
  }

  int main()
  {
    //测试
    test01();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  h222ello
  h222666ello
  hello
  ```
- 总结：插入和删除的起始下标都是从0开始
##### string子串
- 作用：从字符串中获取想要的子串
- 函数原型：
  - string substr(int pos = 0;int n = npos) const;  //返回由pos开始的n个字符组成的字符串
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>

  //string字符串子串

  void test01()
  {
    string str = "abcdef";

    string subStr = str.substr(1, 3);

    cout << "subStr = " << subStr << endl;
  }

  //实用操作
  void test02()
  {
    string email = "zhangsan@sina.com";

    //从邮件地址中  获取 用户名信息
    //email_name = email从0开始截取到email.rfind('@')-1的字符串   email.rfind('@')是指从右往左查找 @ 字符并返回下标
    string email_name = email.substr(0, email.rfind('@'));

    cout << "email_name = " << email_name << endl;
  }
  int main()
  {
    //测试
    test01();
    test02();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  subStr = bcd
  email_name = zhangsan
  ```
#### vector容器
##### vector基本概念
- 作用：vector数据结构和数组非常相似，也成为单端数组
- vector与普通数组区别：
  - 不同之处在于数组是静态空间，而vector可以动态扩展
- 动态扩展：
  - 并不是在原空间之后续接新空间，而是找更大的内存空间，然后将原数据拷贝新空间，释放原空间
- vector容器的迭代器是支持随机访问的迭代器
##### vector构造函数
- 作用：创建vector容器
- 函数原型：
  - vector<T> v;                //采用模板实现类实现，默认构造函数
  - vector(v.begin(),v.end());  //将v[begin(),end()]区间中的元素拷贝给本身
  - vector(n,elem);             //沟站函数将n个elem拷贝给本身
  - vector(const vector &vec);  //拷贝构造函数
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<vector>

  //vector容器构造

  //打印函数
  void printVevtor(vector<int> &v)
  {
    for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
    {
      cout << *it << " ";
    }
    cout << endl;
  }

  void test01()
  {
    vector<int> v1;//默认构造  无参构造

    for (int i = 0; i < 10; i++)
    {
      v1.push_back(i);
    }

    printVevtor(v1);

    //通过区间方式进行构造
    vector<int>v2(v1.begin(), v1.end());
    printVevtor(v2);

    //n个elem方式构造   创建10个100的初始化操作
    vector<int>v3(10, 100);
    printVevtor(v3);

    //拷贝构造
    vector<int>v4(v3);
    printVevtor(v4);
  }

  int main()
  {
    //测试
    test01();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  0 1 2 3 4 5 6 7 8 9
  0 1 2 3 4 5 6 7 8 9
  100 100 100 100 100 100 100 100 100 100
  100 100 100 100 100 100 100 100 100 100
  ```
##### vector赋值操作
- 作用：给vector容器进行赋值
- 函数模型
  - vector& operator=(const vector&vec);  //重载等号操作符
  - assign(beg,end);                      //将[beg,end]区间中的数据拷贝赋值给本身
  - assign(n,elem);                       //将n个elem拷贝赋值给本身
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<vector>

  //vector赋值操作

  //打印函数
  void printVevtor(vector<int> &v)
  {
    for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
    {
      cout << *it << " ";
    }
    cout << endl;
  }

  void test01()
  {
    vector<int> v1;//默认构造  无参构造

    for (int i = 0; i < 10; i++)
    {
      v1.push_back(i);
    }

    printVevtor(v1);

    //赋值    operator=
    vector <int>v2;
    v2 = v1;
    printVevtor(v2);

    //assing
    vector<int>v3;
    v3.assign(v1.begin(), v1.end());
    printVevtor(v3);

    //n个elem 方式赋值
    vector<int>v4;
    v4.assign(10, 100);
    printVevtor(v4);
    
  }

  int main()
  {
    //测试
    test01();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  0 1 2 3 4 5 6 7 8 9
  0 1 2 3 4 5 6 7 8 9
  0 1 2 3 4 5 6 7 8 9
  100 100 100 100 100 100 100 100 100 100
  ```
- 总结：vector赋值方式比较简单，使用operator=或者assign都可以
##### vector容量和大小
- 作用：对vector容器的容量和大小操作
- 函数原型：
  - empty();              //判断容器是否为空
  - capacity();           //容器的容量
  - size();               //返回容器中元素的个数
  - resize(int num);      //重新指定容器的长度为num，若容器变长，则以默认值填充新位置。
                          //如果容器变短，则末尾超出容器长度的元素被删除
  - resize(int num,elem); //重新指定容器的长度为num，若容器变长，则以elem值填充新位置。
                          //如果容器变短，则末尾超出容器长度的元素被删除
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<vector>

  //vector容器的容量和大小操作

  //打印函数
  void printVevtor(vector<int> &v)
  {
    for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
    {
      cout << *it << " ";
    }
    cout << endl;
  }

  void test01()
  {
    vector<int> v1;//默认构造  无参构造

    for (int i = 0; i < 10; i++)
    {
      v1.push_back(i);
    }

    printVevtor(v1);

    //判断容器是否为空
    if (v1.empty())  //为真， 代表容器为空
    {
      cout << "v1为空" << endl;
    }
    else
    {
      cout << "v1不为空" << endl;
      cout << "v1的容量为：" << v1.capacity() << endl;
      cout << "v1的长度为：" << v1.size() << endl;
    }

    //重新指定大小
    v1.resize(15,20);
    printVevtor(v1);

    //重新指定大小
    v1.resize(5);
    printVevtor(v1);
  }

  int main()
  {
    //测试
    test01();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  0 1 2 3 4 5 6 7 8 9
  v1不为空
  v1的容量为：13
  v1的长度为：10
  0 1 2 3 4 5 6 7 8 9 20 20 20 20 20
  0 1 2 3 4
  ```
- 总结：
  - 判断是否为空 --- empty
  - 返回元素个数 --- size
  - 返回容器容量 --- capacity
  - 重新指定大小 --- resize
##### vector插入和删除
- 作用：对vector容器进行插入、删除操作
- 函数原型：
  - push_back(ele);                                 //尾部插入元素ele
  - pop_back();                                     //删除最后一个元素
  - insert(const_iterator pos,ele);                 //迭代器指向位置pos插入元素ele
  - insert(const_iterator pos,int count,ele);       //迭代器指向位置pos插入count个元素ele
  - erase(const_iterator pos);                      //删除迭代器指向的元素
  - erase(const_iterator start,const_iterator end); //删除迭代器从start到end之间的元素
  - clear();                                        //删除容器中所有元素
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<vector>

  //vector容器的容量和大小操作

  //打印函数
  void printVevtor(vector<int> &v)
  {
    for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
    {
      cout << *it << " ";
    }
    cout << endl;
  }

  void test01()
  {
    vector<int> v1;//默认构造  无参构造

    //尾插法
    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(30);
    v1.push_back(40);
    v1.push_back(50);
    //遍历
    printVevtor(v1);

    //尾删法
    v1.pop_back();
    printVevtor(v1);

    //插入  第一个参数是迭代器  begin()
    v1.insert(v1.begin(), 100);
    printVevtor(v1);

    //插入位置   重载版本
    v1.insert(v1.begin(), 2, 1000);
    printVevtor(v1);

    //删除   第一个参数是迭代器
    v1.erase(v1.begin());
    printVevtor(v1);

    //删除位置  重载版本  清空   ==    v1.clear();
    v1.erase(v1.begin(), v1.end());
    printVevtor(v1);
  }

  int main()
  {
    //测试
    test01();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  10 20 30 40 50
  10 20 30 40
  100 10 20 30 40
  1000 1000 100 10 20 30 40
  1000 100 10 20 30 40
  [endl]  //因为最后一次输出清楚了vector容器中元素，所以只产生了endl换行
  ```
- 总结：
  尾插 --- push_back
  尾删 --- pop_back
  插入 --- insert (位置迭代器)
  删除 --- erase  (位置迭代器)
  清空 --- clear
##### vector数据存取
- 作用：对vector中的数据的存取操作
- 函数原型：
  - at(int idx);  //返回索引|idx所指的数据
  - operator[];   //返回索引|idx所指的数据
  - front();      //返回容器中第一个数据元素
  - back();       //返回容器中最后一个数据元素
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<vector>

  //vector容器  数据存取

  //打印函数
  void printVevtor(vector<int> &v)
  {
    for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
    {
      cout << *it << " ";
    }
    cout << endl;
  }

  void test01()
  {
    vector<int> v1;//默认构造  无参构造

    //插入数据
    for (int i = 0; i < 10; i++)
    {
      v1.push_back(i);
    }

    //利用函数访问数组中元素
    printVevtor(v1);

    //利用[ ]中括号方式访问数组中元素
    for (int i = 0; i < v1.size(); i++)
    {
      cout << v1[i] << " ";
    }
    cout << endl;

    //利用at方式访问元素
    for (int i = 0; i < v1.size(); i++)
    {
      cout << v1.at(i) << " ";
    }
    cout << endl;

    //获取第一个元素
    cout << "第一个元素为：" << v1.front() << endl;

    //获取最后一个元素
    cout << "最后一个元素为：" << v1.back() << endl;
  }

  int main()
  {
    //测试
    test01();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  0 1 2 3 4 5 6 7 8 9
  0 1 2 3 4 5 6 7 8 9
  0 1 2 3 4 5 6 7 8 9
  第一个元素为：0
  最后一个元素为：9
  ```
- 总结：
  - 除了用迭代器获取vector容器中元素，[]中括号和at也可以
  - frony返回容器第一个元素
  - back返回容器最后一个元素
##### vector互换容器
- 作用：
  - 实现两个容器内元素进行互换
- 函数原型
  - swap(vec);  //将vec与本身的元素互换
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<vector>

  //vector容器互换

  //打印函数
  void printVevtor(vector<int> &v)
  {
    for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
    {
      cout << *it << " ";
    }
    cout << endl;
  }

  //基本使用
  void test01()
  {
    vector<int> v1;//默认构造  无参构造

    //插入数据 for循环
    for (int i = 0; i < 10; i++)
    {
      v1.push_back(i);
    }

    printVevtor(v1);

    vector<int>v2;

    //插入数据 for循环
    for (int i = 10; i > 0; i--)
    {
      v2.push_back(i);
    }

    printVevtor(v2);

    cout << "交换后：" << endl;

    //交换数据
    v1.swap(v2);
    printVevtor(v1);
    printVevtor(v2);
  }

  //实际使用
  //巧用swap可以收缩内存空间
  void test02()
  {
    vector<int>v;
    for (int i = 0; i < 100000; i++)
    {
      v.push_back(i);
    }

    cout << endl;
    cout << "v的容量为：" << v.capacity() << endl;
    cout << "v的元素长度为：" << v.size() << endl;
    cout << endl;

    v.resize(3);   //重新指定元素长度
    cout << "v的容量为：" << v.capacity() << endl;
    cout << "v的元素长度为：" << v.size() << endl;
    cout << endl;

    //巧用swap收缩内存
    //vector<int>(v)为匿名对象  创建一个新的容器
    //利用swap做容器交换
    vector<int>(v).swap(v);
    cout << "v的容量为：" << v.capacity() << endl;
    cout << "v的元素长度为：" << v.size() << endl;
    cout << endl;
  }

  int main()
  {
    //测试
    test01();
    test02();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  0 1 2 3 4 5 6 7 8 9
  10 9 8 7 6 5 4 3 2 1
  交换后：
  10 9 8 7 6 5 4 3 2 1
  0 1 2 3 4 5 6 7 8 9

  v的容量为：138255
  v的元素长度为：100000

  v的容量为：138255
  v的元素长度为：3

  v的容量为：3
  v的元素长度为：3
  ```
- 总结：swap可以使两个容器互换，可以达到实用的收缩内存效果
##### vector预留空间
- 作用：减少vector在动态扩展容量时的扩展次数
- 函数原型：
  - reserve(int len); //容器预留len个元素长度，预留位置不初始化，元素不可访问
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<vector>

  //vector容器 预留空间

  void test01()
  {
    vector<int> v1;//默认构造  无参构造

    //利用reserve预留空间
    v1.reserve(100000);

    //统计开辟次数
    int num = 0;
    //指针
    int* p = NULL;

    //插入数据 for循环
    for (int i = 0; i < 100000; i++)
    {
      v1.push_back(i);

      //如果p指向不是v1[0]的地址，则p指向v1[0]的地址，开辟次数+1
      //因为开辟的空间不够时，vector会重新开辟一块更大的空间去存储数据
      if (p != &v1[0])
      {
        //p指向v1[0]的地址 
        p = &v1[0];
        num++;
      }
    }
  cout << "开辟次数 num = " << num << endl;
  }

  int main()
  {
    //测试
    test01();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  开辟次数 num = 1
  ```
- 总结：如果数据量较大，可以一开始利用reserve预留空间
#### deque容器
- 功能：双端数组，可以对头端进行插入删除操作
- deque与vector区别：
  - vector对于头部的插入删除效率低，数据量越大，效率越低
  - deque相对而言，对头部的插入删除速度会比vector快
  - vector访问元素时的速度会比deque快，这和两者内部实现有关
- deque内部工作原理：
  - deque内部有个中控器，维护每段缓冲区中的内容，缓冲区中存放真实数据
  - 中控器维护的是每个缓冲区的地址，使得使用deque时像一片连续的内存空间
- deque容器的迭代器也是支持随机访问的
##### deque构造函数
- 函数原型：
  - deque<T>deqT;             //默认构造形式
  - deque(beg,end);           //构造函数将[beg,end]区间中的元素拷贝给本身
  - deque(n,elem);            //构造函数将n个elem拷贝给自身
  - deque(const deque &deq);  //拷贝构造函数
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<deque>

  //deque 构造函数

  //打印函数
  void printDeque(const deque<int>& d)
  {
    for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
    {
      //容器中的数据不可以修改了
      //*it = 100;     //传参处加const并且 迭代器前也加const  作用只读不可写

      cout << *it << " ";
    }
    cout << endl;
  }

  void test01()
  {
    deque<int>d1;

    //插入数据
    for (int i = 0; i < 10; i++)
    {
      d1.push_back(i);
    }

    //遍历容器
    printDeque(d1); 

    //区间方式赋值
    deque<int>d2(d1.begin(), d1.end());
    printDeque(d2);

    //n个elem方式构造   创建10个100的初始化操作
    deque<int>d3(10, 100);
    printDeque(d3);

    //拷贝构造
    deque<int>d4(d3);
    printDeque(d4);
  }

  int main()
  {
    //测试
    test01();
    
    system("pause");
    return 0;
  }
  ``` 
  运行结果：
  ```cpp
  0 1 2 3 4 5 6 7 8 9
  0 1 2 3 4 5 6 7 8 9
  100 100 100 100 100 100 100 100 100 100
  100 100 100 100 100 100 100 100 100 100
  ```
- 总结：deque容器和vector容器的构造方式几乎一致，灵活使用即可
##### deque赋值操作
- 作用：给deque容器进行赋值
- 函数原型：
  - deque& operator=(const deque &deq); //重载等号操作符
  - assign(beg,end);                    //将[beg,end]区间中的数据拷贝赋值给本身
  - assing(n,elem);   //将n个elem拷贝赋值给本身
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<deque>

  //deque容器赋值操作

  //打印函数
  void printDeque(const deque<int>& d)
  {
    for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
    {
      //容器中的数据不可以修改了
      //*it = 100;     //传参处加const并且 迭代器前也加const  作用只读不可写

      cout << *it << " ";
    }
    cout << endl;
  }

  void test01()
  {
    deque<int>d1;

    //插入数据
    for (int i = 0; i < 10; i++)
    {
      d1.push_back(i);
    }

    // operator= 赋值
    deque<int>d2;
    d2 = d1;
    printDeque(d2);

    //assign 赋值
    deque<int>d3;
    d3.assign(d1.begin(), d1.end());
    printDeque(d3);

    ////将n个elem拷贝赋值给本身
    deque<int>d4;
    d4.assign(10, 100);
    printDeque(d4);
  }

  int main()
  {
    //测试
    test01();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  0 1 2 3 4 5 6 7 8 9
  0 1 2 3 4 5 6 7 8 9
  100 100 100 100 100 100 100 100 100 100
  ```
- deque赋值操作与vector相同
##### deque大小操作
- 作用：对deque容器的大小进行操作
- 函数原型：
  - deque.empty();          //判断容器是否为空
  - deque.size();           //返回容器中元素的个数
  - deque.resize(num);      //重新指定容器的长度为num，若容器变长，则以默认值填充新位置。
                            //如果容器变短，则末尾超出容器长度的元素被删除
  - deque.resize(num,elem); //重新指定容器的长度为num，若容器变长，则以elem值填充新位置。
                             //如果容器变短，则末尾超出容器长度的元素被删除
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<deque>

  //deque容器 大小操作

  //打印函数
  void printDeque(const deque<int>& d)
  {
    for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
    {
      //容器中的数据不可以修改了
      //*it = 100;     //传参处加const并且 迭代器前也加const  作用只读不可写

      cout << *it << " ";
    }
    cout << endl;
  }

  void test01()
  {
    deque<int>d1;

    //插入数据
    for (int i = 0; i < 10; i++)
    {
      d1.push_back(i);
    }

    //判断deque容器是否为空
    if (d1.empty())
    {
      cout << "d1为空" << endl;
    }
    else
    {
      cout << "d1不为空" << endl;
      cout << "d1的大小为：" << d1.size() << endl;
      //deque容器没有容量概念
    }

    //重新指定大小
    //d1.resize(15);
    //重载版本  指定填充数据
    d1.resize(15, 1);
    printDeque(d1);

    d1.resize(5);
    printDeque(d1);	
  }

  int main()
  {
    //测试
    test01();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  d1不为空
  d1的大小为：10
  0 1 2 3 4 5 6 7 8 9 1 1 1 1 1
  0 1 2 3 4
  ```
- 总结：
  - deque没有容量的概念
  - 判断是否为空 --- empty
  - 返回元素个数 --- size
  - 重新指定个数 --- resize
##### deque插入和删除
- 作用：向deque容器中插入和删除数据
- 函数原型：
  两端插入操作：
  - push_back(elem);      //在容器尾部添加一个数据
  - push_front(elem);     //在容器头部插入一个数据
  - pop_back();           //删除容器最后一个数据
  - pop_front();          //删除容器第一个数据
  指定位置操作：
  - insert(pos,elem);     //在pos位置插入一个elem元素的拷贝，返回新数据的位置
  - insert(pos,n,elem);   //在pos位置插入n个elem数据，无返回值
  - insert(poe,beg,end);  //在pos位置插入[beg,end]区间数据，无返回值
  - clear();              //清空容器所有数据
  - erase(beg,end);       //删除[beg,end]区间数据，返回下一个数据的位置
  - erase(pos);           //删除pos位置的数据，返回下一个数据的位置
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<deque>

  //deque容器 大小操作

  //打印函数
  void printDeque(const deque<int>& d)
  {
    for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
    {
      //容器中的数据不可以修改了
      //*it = 100;     //传参处加const并且 迭代器前也加const  作用只读不可写

      cout << *it << " ";
    }
    cout << endl;
  }

  void test01()
  {
    deque<int>d1;

    //尾部插入数据
    for (int i = 0; i < 5; i++)
    {
      d1.push_back(i);
    }

    printDeque(d1);

    //头部插入数据
    for (int i = 0; i < 5; i++)
    {
      d1.push_front(i+10);
    }
    
    printDeque(d1);

    //尾删
    d1.pop_back();
    printDeque(d1);

    //头删
    d1.pop_front();
    printDeque(d1);

    cout << endl;
  }

  void test02()
  {
    deque<int>d1;
    d1.push_back(10);
    d1.push_back(20);
    d1.push_front(100);
    d1.push_front(200);

    printDeque(d1);

    //insert插入
    d1.insert(d1.begin(), 1000);	//头部插入一个1000
    printDeque(d1);
    //insert重载
    d1.insert(d1.begin(), 2, 100);	//头部插入两个100
    printDeque(d1);

    //按照区间方式插入
    deque<int>d2;
    d2.push_back(1);
    d2.push_back(2);
    d2.push_back(3);

    //1 2 3 100 100 1000 200 100 10 20
    d1.insert(d1.begin(), d2.begin(), d2.end());
    printDeque(d1);
    cout << endl;
  }

  void test03()
  {
    deque<int>d1;
    d1.push_back(10);
    d1.push_back(20);
    d1.push_front(100);
    d1.push_front(200);

    //删除
    deque<int>::iterator it = d1.begin();
    it++;
    //头部向右偏移删除
    d1.erase(it);
    printDeque(d1);

    //按照区间方式删除
    //clear与区间头尾删除方式一样  都是清空数据。
    //数据清空  最后打印出来一个换行
    d1.clear();
    d1.erase(d1.begin(), d1.end());
    printDeque(d1);
  }

  int main()
  {
    //测试
    test01();
    test02();
    test03();
    
    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  0 1 2 3 4
  14 13 12 11 10 0 1 2 3 4
  14 13 12 11 10 0 1 2 3
  13 12 11 10 0 1 2 3

  200 100 10 20
  1000 200 100 10 20
  100 100 1000 200 100 10 20
  1 2 3 100 100 1000 200 100 10 20

  200 10 20
  //最后因为清空了数据  只打印出来一个换行
  ```
- 总结：
  - 插入和删除提供的位置是迭代器！
  - 尾插 --- push_back
  - 尾删 --- pop_back
  - 头插 --- push_front
  - 头删 --- pop_front
##### deque数据存取
- 作用：对deque中的数据的存储操作
- 函数原型：
  - at(int idx);  //返回索引|idx所指的数据
  - operator[];   //返回索引|idx所指的数据
  - front();      //返回容器中第一个数据元素
  - back();       //返回容器中最后一个数据元素
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<deque>

  //deque容器 大小操作

  //打印函数
  void printDeque(const deque<int>& d)
  {
    for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
    {
      //容器中的数据不可以修改了
      //*it = 100;     //传参处加const并且 迭代器前也加const  作用只读不可写

      cout << *it << " ";
    }
    cout << endl;
  }

  void test01()
  {
    deque<int>d1;

    //尾部插入数据
    for (int i = 0; i < 5; i++)
    {
      d1.push_back(i);
    }

    printDeque(d1);

    //通过[]中括号方式访问元素
    for (int i = 0; i < d1.size(); i++)
    {
      cout << d1[i] << " ";
    }
    cout << endl;
    //通过at方式访问元素
    for (int i = 0; i < d1.size(); i++)
    {
      cout << d1.at(i) << " ";
    }
    cout << endl;

    //访问头尾元素
    cout << "第一个元素为；" << d1.front() << endl;
    cout << "最后一个元素：" << d1.back() << endl;
  }

  int main()
  {
    //测试
    test01();

    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  0 1 2 3 4
  0 1 2 3 4
  0 1 2 3 4
  第一个元素为；0
  最后一个元素：4
  ```
- 总结：
  - 除了用迭代器获取deque容器中元素，[]和at也可以
  - front返回容器第一个元素
  - back返回容器最后一个元素
##### deque排序
- 作用：利用算法实现对deque容器进行排序
- 算法：
  - sort(iterator beg,iterator end) //对beg和end区间内元素进行排序
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<deque>
  #include<algorithm>  //标准算法头文件

  //deque容器 大小操作

  //打印函数
  void printDeque(const deque<int>& d)
  {
    for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
    {
      //容器中的数据不可以修改了
      //*it = 100;     //传参处加const并且 迭代器前也加const  作用只读不可写

      cout << *it << " ";
    }
    cout << endl;
  }

  void test01()
  {
    deque<int>d1;

    //尾部插入数据
    for (int i = 0; i < 5; i++)
    {
      d1.push_back(i);
    }

    printDeque(d1);

    //头部插入数据
    for (int i = 0; i < 5; i++)
    {
      d1.push_front(i);
    }

    printDeque(d1);

    //排序  默认排序规则  从小到达  升序
    //对于支持随机访问的迭代器的容器，都可以利用 sort 算法直接对其进行排序
    //vector容器也可以利用 sort 进行排序
    sort(d1.begin(), d1.end());
    cout << "排序后：" << endl;
    printDeque(d1);
  }

  int main()
  {
    //测试
    test01();

    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  0 1 2 3 4
  4 3 2 1 0 0 1 2 3 4
  排序后：
  0 0 1 1 2 2 3 3 4 4
  ```
- 总结：sort算法非常实用，使用时包含头文件 algorithm 即可
#### 案例-评委打分
- 案例描述：
  - 有5名选手：选手ABCDE，10个评委分别对每一个选手打分，去除最高分，去除最低分，取平均分
- 实现步骤：
  - 创建五名选手，放到vector中
  - 遍历vector容器，取出来每一个选手，执行for循环，可以把10个评分打分存到deque容器中
  - sort算法对deque容器中分数排序，去除最高喝最低分
  - deque容器遍历一遍，累加总分
  - 获取平均分
- 示例：
  ```cpp
  #include<iostream>
  using namespace std;
  #include<string>
  #include<deque>
  #include<algorithm>  //标准算法头文件
  #include<vector>
  #include<ctime>

  //案例 评委打分
  //选手类
  class Person
  {
  public:

    Person(string name, int score)
    {
      this->m_Name = name;
      this->m_Score = score;
    }

    string m_Name;	//姓名
    int m_Score;	//平均分
  };

  void createPerson(vector<Person>&v)
  {
    for (int i = 0; i < 5; i++)
    {
      string nameSeed = "ABCDE";
      string name = "选手";
      name += nameSeed[i];
      int  score = 0;
      Person p(name, score);
      //将创建的Person对象  放入到容器中
      v.push_back(p);
    }
  }

  //打分
  void setScore(vector<Person>& v)
  {
    for (vector<Person>::iterator it = v.begin(); it != v.end(); it++)
    {
      //将评委的分数 放入到deque容器中
      deque<int>d;
      for (int i = 0; i < 10; i++)
      {
        int score = rand() % 41 + 60;
        d.push_back(score);
      }

      //排序
      sort(d.begin(),d.end());

      //去除最高和最低分
      d.pop_back(); 
      d.pop_front();

      //取平均分
      int sum = 0;
      for (deque<int>::iterator it = d.begin(); it != d.end(); it++)
      {
        sum += *it;  //累加每个评委的分数
      }

      //求平均分
      int avg = sum / d.size();

      //将平均分 赋值给选手身上
      it->m_Score = avg;
    }
  }

  //遍历显示
  void showScore(vector<Person>&v)
  {
    for (vector<Person>::iterator it = v.begin(); it != v.end(); it++)
    {
      cout << "选手：" << it->m_Name << "平均分：" << it->m_Score << endl;
    }
  }

  int main()
  {
    //随机数种子
    srand((unsigned int)time(NULL));
    
    //1、创建5名选手
    //存放选手的容器
    vector<Person>v;
    createPerson(v);

    //2、给5名选手打分
    setScore(v);
    
    //3、显示最后得分
    showScore(v);

    system("pause");
    return 0;
  }
  ```
  运行结果：
  ```cpp
  //因为加入了随机数  所以分数随机  每次都不一样
  选手：选手A平均分：81
  选手：选手B平均分：85
  选手：选手C平均分：72
  选手：选手D平均分：82
  选手：选手E平均分：88
  ```
#### stack容器
#### queue容器
#### list容器
#### set/multiset容器
#### map/multimap容器
### STL-函数对象
### STL-常用算法

```cpp
#include <libssh2.h>

int main()
{
    // 初始化libssh2库
    if (libssh2_init(0) != 0)
    {
        fprintf(stderr, "Failed to initialize libssh2\n");
        return -1;
    }

    // 创建ssh会话
    LIBSSH2_SESSION *session = libssh2_session_init();
    if (!session)
    {
        fprintf(stderr, "Failed to create ssh session\n");
        return -1;
    }

    // 连接到服务器
    if (libssh2_session_handshake(session, sockfd))
    {
        fprintf(stderr, "Failed to connect to ssh server\n");
        return -1;
    }

    // 验证服务器
    if (libssh2_userauth_password(session, username, password))
    {
        fprintf(stderr, "Failed to authenticate ssh server\n");
        return -1;
    }

    // 执行ssh命令
    LIBSSH2_CHANNEL *channel = libssh2_channel_open_session(session);
    if (!channel)
    {
        fprintf(stderr, "Failed to open ssh channel\n");
        return -1;
    }
    if (libssh2_channel_exec(channel, "ls -l") != 0)
    {
        fprintf(stderr, "Failed to execute ssh command\n");
        return -1;
    }

    // 读取ssh命令的输出
    char buffer[1024];
    int bytes_read;
    while ((bytes_read = libssh2_channel_read(channel, buffer, sizeof(buffer))) > 0)
    {
        fprintf(stdout, "%s", buffer);
    }

    // 关闭ssh连接
    libssh2_channel_close(channel);
    libssh2_session_free(session);
    libssh2_exit();
    return 0;
}
```