# 運算子
運算子包含算術運算子、邏輯運算子、關係運算子、賦值運算子與條件運算子:  
1. 算數運算子
  - 基本加減乘除(+-/*)、餘數(%)...等等，就不做介紹了
  - 遞增++與遞減--
    > prefix
    ```
    a=1;
    let b=++a*10
    console.log(`For ++a : a=${a},b=${b}`);  //回傳a=2 , b=20
    ```
    > postfix
    ```
    a=1;
    let b=a++*10
    console.log(`For ++a : a=${a},b=${b}`);  //回傳a=2 , b=10
    ```
2. 邏輯運算子
  - 結果不一定為布林值，0、NaN、null、""、undefined轉為false，其餘皆為true
  - 包含 && (and) 與 || (or)
    > 2 || 8 => 回傳2，因為第一項已經為true
  - !NOT運算子 (即取相反)
    > !5 => 回傳false
3. 關係運算子
  -  一般的比較(>,<,=,==,>=,<=)就不介紹了，與Python相同
  -  === , !=== (嚴格比較值與資料型別是否相同) 
4. 賦值運算子
  - = 賦予變數值或者定義function...etc
5. 條件運算子
  - 語法: (判斷式) ? (if true) : (if false)
  - 例如: x>0 ? x:-99

# 流程控制
選擇敘述分成以下:
1. if單一敘述
  - 語法:
  ```
  if(condition){
     statements
  }
  ```
  - 只具備單一敘述時，condition可不加小括號
2. if ... else
  - 語法:
  ```
  if(condition){
    statements
  }else{
    statements
  }
  ```
3. if ... else if ... else
  - 語法: 
  ```
  if(condition){
    statements
  }else if(){
    statements
  }else{
    statements
  }
  ```
4. 多重敘述選擇
  - 語法: 
  ```
  switch(expr){
    case condition:
      statements
      break;
    case condition:
      statements
      break;
    deafult:
      statements
  }
  ```
  
  # 迴圈
  常用的for,while,do...while這邊就不介紹了，與Python相同
