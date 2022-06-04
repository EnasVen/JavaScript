# 函數的功能
函數為一獨立完整的程式碼，可以避免重複的動作以及讓html文件更容易閱讀。  

# 函數宣告
語法: 
```
function 函數名稱 (arg1 , arg2 , ...){
  statements
  return 回傳值
}
```
須注意如果沒有設定return value，default的回傳值為undefined! (Python內則為None)  

# 匿名函數
不使用函數名稱來建立function，需要賦值給指定變數。  
語法: 
```
let variable = function(arg){
  statements
}
```

如果在函數加上小括號，則代表立即執行(優先級別最高!)  
語法:
```
(function(arg1,arg2){
  statements
})(a,b)
```

# 箭頭函數
箭頭函式(Arrow Functions)是ES6標準中，最受歡迎的一種新語法，其優點如下:
1. 語法簡單。少打很多字元。
2. 可以讓程式碼的可閱讀性提高。
3. 某些情況下可以綁定this值。

以下內容擷取自MDN(https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
語法1:
```
([param] [, param]) => {
   statements
}

param => expression
```
例如:
```
const func = (x) => x + 1
```
這個寫法相當於
```
const func = function (x) { return x + 1 }
```
下面是一個容易搞混的例子:
```
const funcA = x => x + 1
const funcB = x => { x + 1 }

funcA(1) //2
funcB(1) //undefined
```
沒有{}時，代表會自動加return，也只能在一行的語句的時候使用;而使用{}則是可以加入多行的語句，不過return不會自動加!  
根據先前定義，沒設定return的函數將會回傳null，而無賦值的變數就會是undefined!  

不可使用箭頭函數的情境:
1. 使用字面文字定義物件時，其中的方法
2. 物件的prototype屬性中定義方法時
3. DOM addEventListener

# 變數範圍
變數的有效範圍分成三種:(和Python不同，Python只有區域和全域)
1. local
  - 使用var在函數內宣告 
2. global 
  - 在函數外宣告
  - 在函數內宣告，但不使用var
3. block(ES6新增)
  - 在{...} block內用let宣告

