# JS Literal
代表各類資料類型中實際儲存值的表示法，永遠不變
1. Numeric
  - normal : 123.45 , -8 , 15e6
  - binary : 0b1010
  - octal : 0o12
  - 0x4e00 : 0x4f01
2. String
  - "text"
  - 'text'
3. Boolean
  - true , false (注意均為小寫)
4. Function
  - function(){...}
5. Object
  - {...}
6. Array
  - [...]
7. REGEXP
  - /.../

# 變數宣告
使用3種方法宣告變數:
1. var
  - 使用var宣告變數 : var identifier [= value];  (可不先給值)
  - 直接指定變數值 : x = value (不寫var直接給值視同var方式呼叫變數)
  - 變數的資料型別在指定值之後才判定(call by balue)
2. let
  - 使用let宣告變數 : let identifier [= value]; (可不先給值)
  - 透過let宣告的變數名，只能被宣告一次，不可重複宣告
  - 區塊性{...} : 在區塊範圍內宣告的let變數只能用於區塊內
```
if(true){
let p = 30;
}
console.log(p);  // 程式碼會回傳錯誤，因為p在global找不到定義 
```
3. const 
  - 使用const宣告變數 : const identifier = value; (一定要給值)
  - 不可重複宣告
  - 不可變更
```
const c = 100;
c = 105;  // 程式碼會回傳錯誤，因為常數變數不可再更改 
```

# 變數命名規則
1. 不可使用保留字 https://www.w3schools.com/js/js_reserved.asp
2. 第1個字元應為大小寫英文字母、下底線或者$，不可為數字 https://www.w3schools.com/js/js_variables.asp
3. 大小寫視為不同變數
4. 第2個字元以後可為大小寫英文字母、下底線、數字或者$

# Template Literal
ES6新增的語法，類似Python的f-string，以成對反引號取代string literal，內部可透過${variableName}來讀取變數值!  
```
//字串轉換為數值
console.log(`parseInt("123.45")=${parseInt("123.45")}`);
//如果沒有初始值，JavaScript會自動將變數的值初始化為undefined(預設值 default value)        
let u;
console.log(`u=${u},type of u = ${typeof u}`);
//字串轉換為數值
console.log(`Number("123.45")=${Number("123.45")}`);
//數值轉換為字串
let price=125;
console.log(`price=${price}`); // ES6
console.log( typeof(`price=${price}`));
```

# 跳脫字元
字串中表示特定字元，或者該字元具備特殊意義時使用
1. \t : TAB (\0009)
2. \n : 換行 (\u000A)
3. \" : 雙引號 (\u0022)
4. \' : 單引號 (\u0027)
5. \\ : 反斜線 (\u005C)
6. \xXX: 兩位數的16進位 (ASCII)
7. \uXXXX : 以16進位數指定 Uncode字元輸出

# 資料型別
JS五大基本資料型別:
1. Number
  - double or float，共64bit
2. String
  - 雙引號 or 單引號呈現
3. Boolean
  - true , false
  - true為1，false為0 (和Python非0即為真相同)
  - 真假判斷式內，任何值都可以被轉成布林值，**而0,NaN,"",null,undefined則轉為false，其餘皆為true!!**
4. null(Object)
  - 無值或者null物件 
```
//null
let n = null;
console.log(`n=${n},type of n = ${typeof n}`);
```
5. undefined
  - 宣告變數時未指定值或不存在的物件

物件資料型別則包含以下:
1. Object
2. Array
3. Function
4. String
5. Number
6. Boolean
7. Date

# 資料型別的獲取與轉換
使用typeof運算子  
字串轉為數值: 
  - parseInt()方法 : 將字串轉成整數
  - parseFloat()方法 : 將字串轉成浮點數
  - Number(string)物件 : 將字串轉為數值  
數值轉為字串:
  - number + "" : 運算子左右只要任一邊為字串，回傳結果就是字串!
  - number.toString()方法 : 數值轉為字串
