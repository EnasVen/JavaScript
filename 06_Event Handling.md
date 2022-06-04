# 事件
事件定義為使用者對瀏覽器或網頁內容所做的動作，例如: 滑鼠點擊、鍵盤輸入...等等，並且產生一個event物件。  

# 事件處理程序
定義事件觸發時的動作

# 事件處理方式
JS內提供3種事件處理方式:  
1. HTML屬性事件處理程序
  - 以HTML內屬性的方式定義事件處理的方式
  ```
  <input type="button onclick=check() value="">
  <script>
    function check(){...}
  </script>
  ```
2. JavaScript屬性事件處理程序
  - 利用呼叫屬性的方式來定義事件處理方式
  ```
  <input type="button id="myBtn" value="">
  <script>
    document.getElementById("myBtn).onclick = check;
    function check(){...}
  </script>
  ```
3. W3C DOM處理程序
  - 以addEventListener的方法來定義事件處理方式
  ```
  <input type="button id="myBtn" value="">
  <script>
    document.getElementById("myBtn).addEventListener("click" , check , false);  //預設為false，這個arg關係到bubbling
    function check(){...}
  </script>
  ```

# Event Bubbling (事件氣泡)
以DOM階層式架構規範事件處理階段:  capture(if true) => handling => bubbling(if false)  
整理以true優先作動，由上往下，再由下往上  
![Image](https://github.com/EnasVen/JavaScript/blob/main/eventflow.png)

下面的例子作為簡易說明:  
1. 當點擊div1時，get true的事件，由上而下只有document，而true部分做完後，便開始false階段，由下而上便會彈出div01 => document的alert訊息  
2. 當點擊div2時，get true的事件，由上而下分別為document => div2，而true部分做完後，便開始false階段，由下而上便會彈出div02 => div01 => document的alert訊息  

```
<body>
    <div id="iddiv1">
		div1
		<div id="iddiv2">div2</div>
    </div>
    <script>
        //==============================================================
        //階層式標籤，事件流程分三階段，
        //事件捕獲(capture)階段==>處理目標階段==>事件氣泡(bubbling)階段
        //==============================================================
        document.addEventListener("click", clickDoc, true);  //事件繫結
        document.getElementById("iddiv1").addEventListener("click", clickDiv1, false);
        document.getElementById("iddiv2").addEventListener("click", clickDiv2, true);

        document.addEventListener("click", clickDoc, false);  //事件繫結
        document.getElementById("iddiv1").addEventListener("click", clickDiv1, false);
        document.getElementById("iddiv2").addEventListener("click", clickDiv2, false);

        function clickDoc() {
            alert("document");
        }

        function clickDiv1() {
            alert("div1");
        }

        function clickDiv2() {
            alert("div2");
        }
    </script>
</body>
```
  
# 常用事件
1. 滑鼠事件處理 
> click , dblclick : 單擊 , 雙擊  
> mousedown , mouseup : 按下滑鼠左鍵 , 放開滑鼠左鍵  
> mouseover , mouseout : 滑鼠移入元素 , 滑鼠移出元素  
> mousemove : 滑鼠在元素上移動  
2. 鍵盤事件處理
> keydown , keyup : 鍵盤按下 , 鍵盤放開(一律回傳大寫，可偵測特殊鍵)  
> keypress : 檢盤按下+放開(有區分大小寫，無法偵測特殊鍵)  
3. 其他事件處理
> load : 視窗載入所有資源(文件、圖檔、樣式)後觸發  
> DOMcontentLoaded : DOM架構載入後即可觸發  
> focus : 選取游標  
> blur : 游標離開選取元素  
> change : 改變文字方塊內容且離開 或者 選取下拉式選單  
