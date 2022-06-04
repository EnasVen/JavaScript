# 動態樣式
JS內可透過兩種方法變更CSS:
1. Object.style.css屬性 = css值 or Object.style = "屬性1:值1;屬性2:值2..."
2. 預先定義class或id的CSS(寫在stylesheet內，以selector方式)，並利用object.className = "名稱"的方式來改變class屬性值，進而套用CSS

```
document.getElementById("idName").style.backgroundColor = "LightCoral";
document.getElementById(i).className = "n"; //提前定義Class = "n"的樣式，修改後即套用
object.style = "color:red;";
```

# 修改顯示內容
讀取/改變HTML標籤內的文字內容(成對標籤):
1. textContent : 讀取元素內容或將取代的內容視為純文字
2. innerHTML : 讀取元素內容或將取代的內容視為HTML標籤解譯

![Image](https://github.com/EnasVen/JavaScript/blob/main/inner_outer.png)

自訂文字加入的位置:
1. insertAdjacentHTML(where,text)
2. insertAdjacentText(where,text)

where 的取值可使用: afterbegin,beforebegin,beforeend,afterend  
上面的定位以HTML 第1與第2 tag的位置做闡述!  

