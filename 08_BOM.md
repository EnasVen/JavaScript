# BOM架構
BOM為Browser Object Model的簡寫，其包含4類主物件:
1. window物件
  - window物件是BOM內的最高階層，代表目前使用的視窗
  - 語法:
  ```
  window.方法()
  window.屬性
  ```
  - 在JS內，函數不論定義在何處都會被提升(elevated)到script頂端，但匿名函數只會提升變數宣告的部分到頂端(也就是只有變數但無函數內容的賦值)
  - 計時器(timer)可以建立動態網頁內容
  ```
  let timeoutID = setTimeout(func. , milliseconds)  //時間到之後只執行1次
  clearTimeout(timeoutID) //停止setTimeout啟動的timer物件
  let intervalID = setInterval(func. , milliseconds) //每隔一定時間執行一次
  clearIntervval(intervalID) //停止setInterval方法啟動的timer物件
  ```
2. location物件
  - 儲存載入網頁URL的相關資訊
  - 屬性: 
    > href: 轉向連結到其他網址  
    > protocol , host , hostname , port , pathname , hash ...etc  
    ```
    console.log("location information:");
    console.log("location protocol=" + location.protocol); //網路協定是哪一種(e.g. http , https)
    console.log("location hostname=" + location.hostname); //主機ip
    console.log("location port=" + location.port); //連接阜 
    console.log("location host=" + location.host); //websocket
    console.log("location pathname=" + location.pathname); //檔案相對位置
    console.log("location hash=" + location.hash);   // bookmark    
    ```
  - 方法:
    > reload: 重新載入目前網頁  
    > replace(url): 使用新網頁取代現有網頁  
3. event物件
  - 用來取得事件發生的位置與類型
  - 屬性:
    > type: 事件類型  
    > button: 回傳滑鼠按下的按鈕  
    > which: 回傳按鍵鍵盤的Unicode編碼  
    > altKey,ctrlKey,shiftKey: 回傳true/false  
    > target: 回傳事件發生的元素物件  
    > currentTaret: 回傳bubbling正在處理的物件  
  - 方法:
    > stopPropagation(): 取消事件氣泡  
    > preventDefault(): 取消或停止預設的動作  
4. document物件
  - 屬性:
    > URL: 回傳文件上的網址  
    > forms: 文件上所有\<form\>元素的集合  
    > images: 文件上所有\<img\>元素的集合  
    > links: 文件上含有href屬性(空字串也算)的所有\<a\>以及\<area\>元素集合  
    > title: 網頁標頭名稱  
  - 方法:
    > getElementById(): 回傳指定id物件  
    > getElementsByName(): 回傳指定name的元素，為類陣列的NodeList  
    > getElementsByTagName(): 回傳指定標籤名稱的元素，為類陣列的HTML Collection  
    > getElementsByClassName(): 回傳css類別名稱的元素，為類陣列的HTML Collection  
    > querySelector(): 回傳符合CSS selector的第一個物件  
    > querySelectorAll(): 回傳符合CSS selector的所有元素，為類陣列的NodeList
  
  NodeList和HTMLCollection兩者均具備length屬性與item(index)方法，但HTMLCollection多了一個namedItem(name)方法!!  
  
  getElementBy...範例:  
  ```
  <body>
    <form>
        <label>name:</label><input type="text" name="txtName" value="abc" /><span id="idsp"></span><br />
        <input type="checkbox" class="ch" name="hobby" checked="checked" value="reading" />
        <label>reading</label>
        <input type="checkbox" class="ch" name="hobby" value="movie" />
        <label>movie</label>
        <input type="checkbox" name="hobby" value="game" />
        <label>game</label>
        <input type="checkbox" name="hobby" value="sleep" />
        <label>sleep</label>
        <br />
        <input id="idcheck" type="button" value="check" />
    </form>

    <script>
        //***********************************************************
        //NodeList 與 HTMLCollection : 這些物件是唯讀的類陣列物件(array-like objects)
        //1.NodeList物件 : 有length 屬性和item(index)方法
        //2.HTMLCollection物件 : 有length 屬性和item(index)方法，namedItem(name)
        //https://developer.mozilla.org/en-US/docs/Web/API
        //***********************************************************

        document.getElementById("idcheck").onclick=check;
        
        function check() {
            
            //NodeList
            let theHobbys = document.getElementsByName("hobby");
            console.log(theHobbys);  //4            
            let theHobbysLen = theHobbys.length; //4
            for (let i = 0; i < theHobbysLen; i++) {
                //console.log(theHobbys.item(i).value);
                console.log(theHobbys[i].value);
            }
            let theSelectors = document.querySelectorAll("input");
            console.log(theSelectors); //6
            


            
            //HTMLCollection
            let theClass = document.getElementsByClassName("ch");
            console.log(theClass);  //2
            
            let theInputs = document.getElementsByTagName("input");
            console.log(theInputs);  //6            
            let theInputsLen = theInputs.length;

            for (let i = 0; i < theInputsLen; i++) {
                //console.log(theInputs.item(i).value);
                console.log(theInputs[i].value);
            }
            console.log(theInputs.namedItem("txtName").value);  //abc
            console.log(theInputs.namedItem("hobby").value);  //reading 傳回第一個
            console.log(theInputs["hobby"].value);
            
        }
      </script>   
  </body>
  ```
  
  querySelector範例:
  ```
 <body>
    <table>
        <tr>
            <td id="td1">A1</td>
            <td class="myclass">B2</td>
            <td>C3</td>
        </tr>
        <tr>
            <td>D4</td>
            <td class="myclass">E5</td>
            <td>F6</td>
        </tr>
    </table>
    <hr>
    <div id="myDiv"></div>

    <script>
        //使用document.querySelector()
        let qs1 = document.querySelector("td");
        console.log(qs1);
        let qs2 = document.querySelector(".myclass");
        console.log(qs2);
        let qs3 = document.querySelector("#td1");
        console.log(qs3);


        //使用document.querySelectorAll()
        let qsA1 = document.querySelectorAll("td");
        console.log(qs1);
        let qsA2 = document.querySelectorAll(".myclass");
        console.log(qs2);
        let qsA3 = document.querySelectorAll("#td1");
        console.log(qsA3[0]);
        console.log(qsA3[0].textContent);

    </script>
</body>
  ```
