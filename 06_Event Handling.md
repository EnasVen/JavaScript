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
