# Web Flow
客戶端與server端透過HTTP協定進行交流，所謂HTTP即Hyper Text Transfer Protocol，為網路設備之間溝通的語言。  
![Image](https://github.com/EnasVen/JavaScript/blob/main/Web_App_Flow.png)  

# 開發人員工具
F12可查看網頁各項數據，常用如下:  
1. Element : 查看網頁架構，即HTML組成
2. Console : 呈現錯誤訊息或JavaScript除錯用(回傳console.log) 
3. Network : 查看網頁的HTTP request和response狀態，通常用於爬蟲(獲取headers以及json,html response位置)
4. Applications : 查看網頁暫存資料，例如: cookies

# JavasCript
JS為一種以物件和事件驅動的基礎程式語言，必須要嵌入HTML文件內才可執行，無法單獨發揮效用。  
一般而言包括三大部分:
1. ECMA Script
  - 規範JS的標準, https://www.ecma-international.org/
  - 目前為ES6.0
2. BOM
  - Browser Object Model，意即以瀏覽器為框架往下延伸的架構
3. DOM
  - Document Object Model，意即以Document網頁主體往下延伸的架構
  - 以樹狀結構來表示HTML文件的模型，同時定義JS指令可存取並改變文件架構、樣式或內容的方

關於BOM與DOM的解析可透過下圖一目了然(來源:csdn)  
![Image](https://github.com/EnasVen/JavaScript/blob/main/BOM_DOM.png)  

# 物件導向
HTML內的標籤元素(tags)，在JS內視為一個物件。  
JS物件由屬性(property)和方法(method)組成。  
屬性和方法呼叫原則如下:
```
object.property
object.mehtod()
```
事件為預先定義好的特定動作，通常由使用者或系統觸發。  

# JS優點
1. 跨瀏覽器皆可使用
2. 具備與網頁互動功能
3. 提供表單前端驗證(Browser端)
4. 動態更新網頁內容

# 使用方式與位置
兩種嵌入HTML的位置，以及兩種嵌入方式(直接寫/外掛樣式):
1. inside body
```diff
<body>
  <某個tag></某個tag>
+  <script>
+      ...js codes...
+  </script>
</body>
```
2. inside head
```diff
<head>
  <meta>
  <title> xxx </title>
  <link rel="stylesheet" href="./.css">
+  <script src="./xxx.js"></script>
</head>
<body>
  ...
</body>
```
