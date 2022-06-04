# 物件的種類
JS內的物件分成3種類型:
1. 內建
  - 由ECMAScript規格所定義之物件，例如: Date,Array,RegExp,function...等等
2. 主機
  - JS用於執行環境所定義的物件，例如: BOM
  - 客戶端用瑜表示網頁結構的HTML元素，例如: DOM
3. 自訂
  - 使用JS自行定義物件導向的內容，包含內容如: constructor、method...etc

# 物件的屬性與方法
語法:
```
物件.屬性 [=設定值]
物件.方法([參數])
```

詳細物件說明可參考W3School https://www.w3schools.com/jsref/default.asp  
以下挑選部分物件做說明:  

# String物件
字串變數與字串物件所運用的方法和屬性都相同。  
語法: 
```
stringObj = new String(["stringLiteral"])
```

字串常使用的方法如下:
> charAt(char) : 回傳指定索引的字元位置(從0開始算)  
> charCodeAt(index) : 回傳指定索引的Unicode字元  
> indexOf(subString) : 回傳指定字串第一次出現的索引位置，找不到就return -1  
> lastIndexOf(subString) : 回傳指定字串最後出現的索引位置，找不到就return -1  
> substr(start [,length]) : 回傳開始索引後特定長度的字串，如果沒指定length則預設為取到字串最後一個字元  
> substring(start , end) :回傳開始到結束索引的字串，不包含最後(i.e. [a,b) )  
> slice(start , end) : 與substring相同，輸入-1則從後面開始索引，和Python相同  
> split([seperator] , [limit]) : 用符號分割字串，回傳分割後的字串array  
> toUpperCase() , toLowerCase() : 轉換大小寫  


```
//字串物件
let strObj = new String("Hello! Java!");    
console.log(typeof strObj);
console.log("strObj.charAt(3)="+strObj.charAt(3));
console.log("strObj.charCodeAt(3)="+strObj.charCodeAt(3));
console.log("strObj.indexOf('a')="+strObj.indexOf('a'));
console.log("strObj.lastIndexOf('a')="+strObj.lastIndexOf('a'));
console.log("strObj.lastIndexOf('@')="+strObj.lastIndexOf('@'));
console.log("strObj.substr(5,3)="+strObj.substr(5,3));
console.log("strObj.substr(5)=")+strObj.substr(5);
console.log("strObj.substring(5,8)="+strObj.substring(5,8));
console.log("strObj.split(' ')="+strObj.split(" "));

let strArray = strObj.split(" ");
console.log("Array String is :");
console.log(strArray);
console.log(`Type of this object is : ${typeof strArray}`);
console.log("strObj.toUpperCase()="+strObj.toUpperCase());
```
# Array物件

# Date物件

# Object物件

# JSON物件
