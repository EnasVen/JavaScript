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

字串常用的**屬性**如下:
> length : 回傳字串長度

字串常使用的**方法**如下:
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
須注意字串的比大小預設使用ASCII作為比大小的依據!  
字串的獲取可透過DOM抓取網頁元素內的value屬性:
```
var elementObj = document.getElementById(elementId);
var strValue = elementObj.value // 例如: <h1  id="ID" value = "abc"> xxx </h1>
```

JS內常用的字元編碼:
1. ASCII (American Standard Code for Information Interchange): 
  - 基於拉丁字母的一套電腦編碼系統
  - 主要用於英語系的文字編碼 
2. Unicode (萬國碼/統一碼)
  - 公認的編碼標準
  - 對世界上大部分的文字進行整理和編碼，使電腦能夠以簡單的方式來顯示語言文字
3. UTF-8 
  - 針對Unicode的可變長度字元編碼
  - 多使用於繁體或簡體中文
  - 根據不同語言可使用不同的byte，例如漢字用3byte、英文字元只用1byte、阿拉伯文使用2byte...等等

# Array物件
陣列為放置在連續記憶體的變數集合。  
語法:
```
arrayObj = new Array([size])
arrayObj = [element0 [,element1 , ...]]
```
和Python相同，陣列索引由0開始，且為iterable物件，可用for迴圈來getitem!  

陣列常用的**屬性**如下:
> length : 回傳陣列長度

陣列常使用的**方法**如下:
> concat(array) : 和input陣列串接形成新的陣列，回傳新陣列，原陣列不改變  
> join([seperator]) : 將所有元素以分隔符號串接，回傳新陣列，原陣列不改變  
> sort : 排序陣列，回傳排序後的陣列，原陣列將被改變  
> push(item1 , item2 , ...) : 陣列尾端加入多個元素值，回傳陣列長度，原陣列將被改變  
> pop() : 取出尾端元素，回傳取出的元素，原陣列將被改變  
> unshift(item1,item2,...) :陣列前端加入多個元素值，回傳陣列長度，原陣列將被改變  
> shift() : 從陣列前端取出一個元素值，回傳取出的元素，原陣列將被改變  

```
const numbers = [4, 2, 5, 1, 3];
numbers.sort();
console.log(numbers); // [1, 2, 3, 4, 5]

const numAry = [35, 6, 78, 12, 54, 9];
// numAry.sort();
// console.log(numAry);

// 自定義排序 (Custom Sort)
// sort() 可以傳入函數參數 compareFunction，可以用來自訂排序的邏輯，陣列會根據 compareFunction 函數的回傳值來做排序依據。 
// compareFunction(a, b) 函數接受兩個參數，分別表示兩個元素值做比較，然後傳回一個數字，可能是正數、0 或負數：
// 例如 : function(50,100)
// compareFunction(a, b) 回傳值如果小於 0 (負數)，表示 a 排序在 b 前面
// compareFunction(a, b) 回傳值如果等於 0，表示 a 和 b 排序一樣位置不動
// compareFunction(a, b) 回傳值如果大於 0 (正數)，表示 b 排序在 a 前面
//ECMAscript 標準沒規範當 0 相等的時候，哪個元素排先哪個元素排後，每個瀏覽器的實做可能會不一樣。

numAry.sort(function (a, b) {
    console.log(`a=${a} and b=${b}`);
    return a - b;
});
console.log(numAry);

console.log(numAry.unshift(0));
```

# Date物件
語法: 
```
dateObj = new Date();
dateObj = new Date(dateString);
dateObj = new Date(year,month,day [,hour[minute [, second [ , millisecond ]]]]);
```

日期常使用的**方法**如下:
> getFullYear() : 回傳西元年分  
> getMonth() : 回傳月份值  
> getDate() : 回傳日數(1 to 31)  
> getDay() : 回傳星期數(0 to 6)  
> getHours() : 回傳小時數(0 to 23)  
> getMinutes() : 回傳分鐘數(0 to 59)  
> getSeconds() : 回傳秒數(0 to 59)  
> getTime() : 回傳自 1970/1/1 00:00:00起的秒數  

```
//建立日期物件語法 1
let d = new Date();
console.log(d);

//建立日期物件語法 2
d = new Date("2022-05-11");  //未指定細節時間則預設08:00:00
console.log(d);
d = new Date("2022-05-11T09:11:30"); 
console.log(d);
d = new Date("2022-5-11T09:11:30");  // invalid date
console.log(d);
d = new Date("2022-5-11T9:11:30");  // invalid date
console.log(d);

d = new Date("2022/05/11");  // 斜線也ok  只是default會變成00:00:00
console.log(d);
d = new Date("2022/05/11 9:13:30 pm");  // 後面細部時間使用空白分隔
console.log(d);
d = new Date("2022/05/11 7:17:37");  // 後面細部時間使用空白分隔
console.log(d);

//建立日期物件語法 3
d = new Date(2022,7,19,15,20,20);  // 注意月份是從0~11，因此7代表8月
console.log(d);

// 超出規格的日期結果
d = new Date("2022-04-31");  // 沒有31就自動位移天數
console.log(d);
d = new Date("2022-02-31");  // 沒有31就自動位移天數
console.log(d);
d = new Date("2022-04-32");  // 超過31就會invalid
console.log(d);

d = new Date(2022,1,35);  // 直接輸入數字則不會內建驗證，會直接往後位移
console.log(d);


d = new Date();  
console.log(d.getDay());
let theYear = d.getFullYear() - 1911;
let theMonth = d.getMonth() + 1;
let theDate = d.getDate();
// console.log(d);
console.log(`民國${theYear}年${theMonth}月${theDate}日`);
```


# Object物件
語法:
```
obj = new Object()
obj = {property1 : value1 , ...} // property可使用單或雙引號，也可以不包起來
```

物件存取**屬性**: 
```
obj.property
obj."property"
```
物件存取**方法**: 
```
obj.method()
```
```
<div id="myDiv"></div>
<script>
let cars = {
    brand: "A",
    "max spd":999,
    color: "red",
    do:function(){
        return `${this.brand}+${this["max spd"]}+${this.color}`
    }
};
console.log(cars);
console.log(cars.do());

//for..in
for(t in cars){
    console.log(cars[t]);
    console.log(typeof t);
    document.getElementById("myDiv").innerHTML += `<li>cars[${t}]:${cars[t]} </li>`
}
</script>  
```


在JS內，物件也可以透過this代名詞來指向呼叫函數的物件!  

# JSON物件
