# DOM
1. DOM為Document Object Model縮寫，用來表示HTML與XML文件內容的應用程式API。  
2. 將HTML文件解析為結構化樹狀表示，並定義讓程式可存取並修改文件架構、樣式和內容的方法。  
3. HTML文件內的所有資料皆可透過DOM來存取、修改、新增甚至刪除。  
4. W3C歷年透過DOM進行標準化，目前已推進至DPM Level4
動態標準請參考: https://dom.spec.whatwg.org/ 

# 樹狀結構
以下資料參考來源: https://www.w3schools.com/xml/dom_nodetype.asp  
由上而下分為文件節點、元素節點(標籤)與文字節點(內容):  
![Image](https://github.com/EnasVen/JavaScript/blob/main/DOM01.png)  

樹狀化結構可透過parent-child節點方式來存取資料。  
![Image](https://github.com/EnasVen/JavaScript/blob/main/DOM02.png)  

使用document物件來使用節點物件的屬性和方法:
1. 節點相對關係(attr):
  - documentElement: 回傳HTMLTag
  - firstChild,lastChild,parentNode,childNodes,previousSibling,nextSibling ... etc
  ```
  <body>
    <h1>Hello DOM</h1>
    <p>I am a JavaScript</p>
	  <ul>
      <li>aaaaa</li>
      <li>bbbbb</li>
      <li>ccccc</li>
      <li>ddddd</li>
      <li>eeeee</li>
      <li>fffff</li>
    </ul>

    <script >
        //*****************************************
        //nodeName 讀取元素節點內容，得到是元素名稱
        //nodeValue 讀取文字節點內容，得到的是文字內容
        //nodeType 讀取節點類型
        //*****************************************
      
        let root =document.documentElement;
        // console.log(root.nodeName);
        let thehead=root.firstElementChild;  //HEAD
        let thebody=root.lastElementChild;  //BODY
        let theUl=thebody.firstElementChild.nextElementSibling.nextElementSibling;  //UL
        let theUlchilds=theUl.childElementCount;        
        // console.log(theUl.childNodes);
        // console.log(theUl.childNodes[1].firstChild.nodeValue);
        console.log(theUl.childNodes); // 有換行
        console.log(theUl.children);  //6
        console.log(theUl.children[0].innerHTML);
        // console.log(theUl.firstElementChild);

        let childEl = theUl.firstElementChild;
        while ( childEl ) {
            console.log(childEl);   // 印出物件
            console.log(childEl.innerHTML) // 印出textContent
            childEl = childEl.nextElementSibling;                    
        }
    </script>
  </body>
  ```
2. 節點屬性
  - nodeType: 節點類型(回傳以NodeType回傳，例如:1,2,3...12，對應代碼參考: https://www.w3schools.com/xml/dom_nodetype.asp)
  - nodeName: 大寫標籤名稱或#document or #text (非標籤的node回傳值)
  - nodeValue: Text或備註comment的文字內容(可能為null)
  ```
  <script >
        //*****************************************
        //nodeName 讀取元素節點內容，得到是元素名稱
        //nodeValue 讀取文字節點內容，得到的是文字內容
        //nodeType 讀取節點類型
        //*****************************************

        alert(document.nodeType);  //9
        alert(document.nodeName);  //#document
        alert(document.nodeValue);  //null

        //取得根元素 documentElement
        let root = document.documentElement;  //HTML
        alert(root.nodeType); // 1 
        alert(root.nodeName);  // HTML
        alert(root.nodeValue); // null

        let thebody = root.childNodes[1];  //BODY
        alert(thebody.nodeType); // 1 
        alert(thebody.nodeName);   // BODY
        alert(thebody.nodeValue); //null


        let theNode = root.childNodes[1].childNodes[3].childNodes[3];  //LI
        //alert(root.childNodes[1].childNodes[3].nodeName);
        //alert(theNode.nodeName);
        //alert(theNode.firstChild.nodeValue);  //bbbbb
        //alert(theNode.previousSibling.previousSibling.firstChild.nodeValue);  //aaaaa
        //alert(theNode.nextSibling.nextSibling.firstChild.nodeValue);  //ccccc

        //alert(theNode.parentNode.nodeName);  //UL
        //alert(theNode.parentNode.lastChild.previousSibling.firstChild.nodeValue);  //fffff


        let lis = document.getElementsByTagName("li");
        console.log(lis);
        for (let i = 0; i < lis.length; i++) {
            // alert(lis.item(i).firstChild.nodeValue);
            alert(lis[i].firstChild.nodeValue);

        }
  </script>
  ```
  
# 元素的新增與移除
新增元素包含以下4步驟:
1. 建立元素名稱
2. 建立文字內容
3. 使用appendChild將文字內容新增在元素之後
4. 使用appendChild將新元素新增在特定元素之後

移除元素包含以下2步驟:
1. 找到刪除元素(透過索引)
2. 使用node.parentNode.removeChild(node)的方式來刪除節點 或者 使用 node.remove()刪除節點

範例: 
```
<body>
    <div id="iddiv">div</div>
    <input type="button" id="CEle" value="CreateElement">
    <input type="button" id="REle" value="RemoveElement">
    <script>
        document.querySelector("#CEle").addEventListener("click", CreateElement)
        document.querySelector("#REle").addEventListener("click", RemoveElement)

        function CreateElement() {
            let theDIV = document.querySelector("#iddiv");  //取得div物件

            let eleP = document.createElement("p");
            let txtP = document.createTextNode("Hello World");
            eleP.appendChild(txtP);

            theDIV.appendChild(eleP);

            let eleImg = document.createElement("img");
            eleImg.setAttribute("src", "DOM/DOMImage/rabbit-hat.gif");
            eleImg.setAttribute("id" , "idImg");
            theDIV.appendChild(eleImg);
        }

        function RemoveElement() {
            let theNode = document.getElementById("idImg");
            theNode.parentNode.removeChild(theNode);
            // theNode.remove();
        }
    </script>
</body>
```

