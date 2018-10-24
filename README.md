<h1 align="center">
<br>
  <a href="https://github.com/doggy8088/36-js-concepts"><img src="36_js_concepts.png" alt="每位 JavaScript 開發者應理解的 33 個概念" width=200"></a>
  <br>
    <br>
  每位 JavaScript 開發者應理解的 36 個概念
  <br>
</h1>

## 簡介

這個專案是為了幫助開發者掌握 JavaScript 概念而建立的。它不是必備，但在未來學習 JavaScript 的過程中，可以作為一篇指南。

本篇文章是基於 [Stephen Curtis](https://twitter.com/stephenthecurt) 的文章寫成，你可以從[這裡](https://medium.com/@stephenthecurt/33-fundamentals-every-javascript-developer-should-know-13dd720a90d1)閱讀。

本篇文章也另外參考了 [這裡](https://github.com/leonardomso/33-js-concepts) 與 [這裡](https://github.com/stephentian/33-js-concepts) 所整理的連結。

---

## 目錄

1. [呼叫堆疊 (Call Stack)](#1-呼叫堆疊-call-stack)
2. [原始型別 (Primitive Types)](#2-原始型別-primitive-types)
3. [實值型別和參考型別](#3-實值型別和參考型別)
4. [隱式、顯式、名義、結構和鴨子類型](#4-隱式顯式名義結構和鴨子類型)
5. [== vs ===、typeof vs instanceof](#5--vs-typeof-vs-instanceof)
6. [函數作用域(Function Scope)、區塊作用域(Block Scope)和詞法作用域(Lexical Scope)](#6-函數作用域function-scope區塊作用域block-scope和詞法作用域lexical-scope)
7. [表達式和陳述式](#7-表達式和陳述式)
8. [立即執行函數、模組化、命名空間](#8-立即執行函數模組化命名空間)
9. [訊息佇列和事件循環](#9-訊息佇列和事件循環)
10. [setTimeout, setInterval 和 requestAnimationFrame](#10-settimeout-setinterval-和-requestanimationframe)
11. [JavaScript 引擎](#11-javascript-引擎)
12. [Bitwise operators、型別陣列(Type Arrays) 和 Array Buffers](#12-bitwise-operators型別陣列type-arrays-和-array-buffers)
13. [DOM 樹和渲染過程](#13-dom-樹和渲染過程)
14. [工廠函數和類別](#14-工廠函數和類別)
15. [this、call、apply 和 bind](#15-thiscallapply-和-bind)
16. [new、建構式、instanceof 與 Instances](#16-new建構式instanceof-與-instances)
17. [原型繼承與原型鏈](#17-原型繼承與原型鏈)
18. [Object.create 和 Object.assign](#18-objectcreate-和-objectassign)
19. [map、reduce、filter 等高階函數](#19-mapreducefilter-等高階函數)
20. [純函數, 函數副作用和狀態變化](#20-純函數-函數副作用和狀態變化)
21. [閉包](#21-閉包)
22. [High Order Functions](#22-high-order-functions)
23. [遞迴](#23-遞迴)
24. [集合 (Collections)](#24-集合-collections)
25. [Promise](#25-promise)
26. [async/await](#26-asyncawait)
27. [資料結構](#27-資料結構)
28. [耗性能操作 (Expensive Operation) 和 時間複雜度 (Big O Notation)](#28-耗性能操作-expensive-operation-和-時間複雜度-big-o-notation)
29. [演算法](#29-演算法)
30. [繼承, 多型和代碼複用](#30-繼承-多型和代碼複用)
31. [設計模式](#31-設計模式)
32. [偏函數 (Partial Applications)、柯理化 (Currying)、Compose 與 Pipe](#32-偏函數-partial-applications柯理化-curryingcompose-與-pipe)
33. [代碼整潔之道](#33-代碼整潔之道)
34. [變量提升 (Hoisting)](#34-變量提升-hoisting)
35. [Memoization](#35-memoization)
36. [二進制, 十六進制, 十進制, 科學記數法](#36-二進制-十六進制-十進制-科學記數法)

---

## 1. 呼叫堆疊 (Call Stack)

### 相關文章

- 📜 [Understanding Javascript Call Stack, Event Loops — Gaurav Pandvia](https://medium.com/@gaurav.pandvia/understanding-javascript-function-executions-tasks-event-loop-call-stack-more-part-1-5683dea1f5ec)
- 📜 [Understanding the JavaScript Call Stack — Charles Freeborn](https://medium.freecodecamp.org/understanding-the-javascript-call-stack-861e41ae61d4)
- 📜 [Javascript: What Is The Execution Context? What Is The Call Stack? — Valentino Gagliardi](https://www.valentinog.com/blog/js-execution-context-call-stack/)
- 📜 [What is the JS Event Loop and Call Stack? — Jess Telford](https://gist.github.com/jesstelford/9a35d20a2aa044df8bf241e00d7bc2d0)
- 📜 [Call Stack — MDN](https://developer.mozilla.org/en-US/docs/Glossary/Call_stack)
- 📜 [Understanding Execution Context and Execution Stack in Javascript — Sukhjinder Arora](https://blog.bitsrc.io/understanding-execution-context-and-execution-stack-in-javascript-1c9ea8642dd0)
- 📜 [How JavaScript Works: An Overview of the Engine, the Runtime, and the Call Stack — Alexander Zlatkov](https://blog.sessionstack.com/how-does-javascript-actually-work-part-1-b0bacc073cf)
- 📜 [The Ultimate Guide to Execution Contexts, Hoisting, Scopes, and Closures in JavaScript — Tyler McGinnis](https://tylermcginnis.com/ultimate-guide-to-execution-contexts-hoisting-scopes-and-closures-in-javascript/)

- 📜 [呼叫堆疊 — MDN](https://developer.mozilla.org/en-US/docs/Glossary/Call_stack)
- 📜 [[譯] JavaScript 如何工作：對引擎、運行時、呼叫堆棧的概述 —— 掘金](https://juejin.im/post/5a05b4576fb9a04519690d42#comment)
- 📜 [[譯] 理解 JavaScript 中的執行上下文和執行棧 —— 掘金](https://juejin.im/post/5ba32171f265da0ab719a6d7)
- 📜 [這一次，徹底弄懂 JavaScript 執行機制 —— 掘金](https://juejin.im/post/59e85eebf265da430d571f89)
- 📜 [解讀 JavaScript 之引擎、運行時和堆棧呼叫 —— 開源中國](https://www.oschina.net/translate/how-does-javascript-actually-work-part-1)
- 📜 [Tasks, microtasks, queues and schedules —— Jake Archibald](https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/)

### 相關影片

- 🎥 [Javascript: the Call Stack explained — Coding Blocks India](https://www.youtube.com/watch?v=w6QGEiQceOM)
- 🎥 [The JS Call Stack Explained In 9 Minutes — Colt Steele](https://www.youtube.com/watch?v=W8AeMrVtFLY)
- 🎥 [JavaScript Execution Stack — Codecademy](https://www.youtube.com/watch?v=jT0USJeNFEA)
- 🎥 [What is the Call Stack? — Eric Traub](https://www.youtube.com/watch?v=w7QWQlkLY_s)
- 🎥 [The Call Stack — Kevin Drumm](https://www.youtube.com/watch?v=Q2sFmqvpBe0)
- 🎥 [Understanding JavaScript Execution — Codesmith](https://www.youtube.com/watch?v=Z6a1cLyq7Ac&list=PLWrQZnG8l0E4kd1T_nyuVoxQUaYEWFgcD)
- 🎥 [Call Stack & Event Loop — movies com](https://www.youtube.com/watch?v=mk0lu9MKBto)
- 🎥 [The Ultimate Guide to Execution Contexts, Hoisting, Scopes, and Closures in JavaScript — Tyler McGinnis](https://www.youtube.com/watch?v=Nt-qa_LlUH0)

- 🎥 [What is the event loop anyway? —— 騰訊視頻(英文字幕)](https://v.qq.com/x/page/h0372bld8re.html?ptag=qqbrowser)
- 🎥 [Understanding The JavaScript Call Stack, Event Queue, Event Table, & Event Loop —— Bilibili](https://www.bilibili.com/video/av33824933/)
- 🎥 [JS 中的變量提升、堆棧內存及閉包詳解 —— Acfun](http://www.acfun.cn/v/ac4495641)
- 🎥 [事件循環模型 —— PHP 中文網](http://www.php.cn/code/21194.html)

**[⬆ 返回目錄](#目錄)**

---

## 2. 原始型別 (Primitive Types)

### 相關文章

- 📜 [How numbers are encoded in JavaScript — Dr. Axel Rauschmayer](http://2ality.com/2012/04/number-encoding.html)
- 📜 [What You Need to Know About JavaScript Number Type — Max Wizard K](https://medium.com/dailyjs/javascripts-number-type-8d59199db1b6)
- 📜 [What Every JavaScript Developer Should Know About Floating Point Numbers — Chewxy](https://blog.chewxy.com/2014/02/24/what-every-javascript-developer-should-know-about-floating-point-numbers/)
- 📜 [The Secret Life of JavaScript Primitives — Angus Croll](https://javascriptweblog.wordpress.com/2010/09/27/the-secret-life-of-javascript-primitives/)
- 📜 [Primitive Types — Flow](https://flow.org/en/docs/types/primitives/)
- 📜 [(Not) Everything in JavaScript is an Object - Daniel Li](http://blog.brew.com.hk/not-everything-in-javascript-is-an-object/)
- 📜 [JavaScript data types and data structures - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#Primitive_values)

- 📜 [原始數據 —— MDN](https://developer.mozilla.org/zh-TW/docs/Glossary/Primitive)
- 📜 [ECMAScript 原始類型 —— W3school](http://www.w3school.com.cn/js/pro_js_primitivetypes.asp)
- 📜 [How numbers are encoded in JavaScript —— Dr. Axe](http://2ality.com/2012/04/number-encoding.html)
- 📜 [每一個 JavaScript 開發者應該瞭解的浮點知識 —— 顏海鏡](https://yanhaijing.com/javascript/2014/03/14/what-every-javascript-developer-should-know-about-floating-points/)
- 📜 [JavaScript 標準參考教程(基本語法之數值) —— 阮一峰](https://wangdoc.com/javascript/types/number.html)
- 📜 [The Secret Life of JavaScript Primitives —— Angus Croll](https://javascriptweblog.wordpress.com/2010/09/27/the-secret-life-of-javascript-primitives/)

### 相關影片

- 🎥 [JavaScript Reference vs Primitive Types — Academind](https://www.youtube.com/watch?v=9ooYYRLdg_g)
- 🎥 [JavaScript Primitive Types — Simon Sez IT](https://www.youtube.com/watch?v=HsbWQsSCE5Y)
- 🎥 [Javascript Primitive and Reference Types — Baljeet Singh](https://www.youtube.com/watch?v=F7YbhKbpFic)
- 🎥 [Value Types and Reference Types in JavaScript — Programming with Mosh](https://www.youtube.com/watch?v=e-_mDyqm2oU)
- 🎥 [JavaScript Primitive Data Types — Avelx](https://www.youtube.com/watch?v=qw3j0A3DIzQ)
- 🎥 [Everything you never wanted to know about JavaScript numbers — Bartek Szopka](https://www.youtube.com/watch?v=MqHDDtVYJRI)

- 🎥 [javascript 六種數據類型 —— 慕課網](https://www.imooc.com/video/5674)
- 🎥 [javascript 視頻教程(數據類型) —— PHP 中文網](http://www.php.cn/code/5808.html)

**[⬆ 返回目錄](#目錄)**

---

## 3. 實值型別和參考型別

### 相關文章

- 📜 [Explaining Value vs. Reference in Javascript — Arnav Aggarwal](https://codeburst.io/explaining-value-vs-reference-in-javascript-647a975e12a0)
- 📜 [Understand Value and Reference Types in JavaScript — Zsolt Nagy](https://www.zsoltnagy.eu/understand-value-and-reference-types-in-javascript/)
- 📜 [Primitive Types & Reference Types in JavaScript — Bran van der Meer](https://gist.github.com/branneman/7fb06d8a74d7e6d4cbcf75c50fec599c)
- 📜 [Value Types, Reference Types and Scope in JavaScript — Ben Aston](https://medium.com/@benastontweet/lesson-1b-javascript-fundamentals-380f601ba851)
- 📜 [Back to roots: JavaScript Value vs Reference — Miro Koczka](https://medium.com/dailyjs/back-to-roots-javascript-value-vs-reference-8fb69d587a18)
- 📜 [Grasp “By Value” and “By Reference” in JavaScript — Léna Faure](https://hackernoon.com/grasp-by-value-and-by-reference-in-javascript-7ed75efa1293)
- 📜 [JavaScript Reference and Copy Variables — Vítor Capretz](https://hackernoon.com/javascript-reference-and-copy-variables-b0103074fdf0)
- 📜 [JavaScript Primitive vs Reference Values](http://www.javascripttutorial.net/javascript-primitive-vs-reference-values/)

- 📜 [ECMAScript 引用類型 —— W3school](http://www.w3school.com.cn/js/pro_js_referencetypes.asp)
- 📜 [js 中的實值型別和參考型別的區別 —— 博客園](https://www.cnblogs.com/leiting/p/8081413.html)
- 📜 [JavaScript 的值傳遞和引用傳遞 —— FunDebug](https://blog.fundebug.com/2017/08/09/explain_value_reference_in_js/)
- 📜 [Primitive Types & Reference Types in JavaScript —— Bran van der Meer](https://docstore.mik.ua/orelly/webprog/jscript/ch04_04.htm)
- 📜 [JavaScript: Passing by Value or by Reference —— CSDN](https://blog.csdn.net/xiaojia_boke/article/details/54906509)
- 📜 [js 值引用和值複製 —— SegmentFault](https://segmentfault.com/a/1190000015411195)
- 📜 [js- 引用和複製(傳值和傳址) —— CSDN](https://blog.csdn.net/zzzaquarius/article/details/4902235)

### 相關影片

- 🎥 [Javascript Pass by Value vs Pass by Reference — techsith](https://www.youtube.com/watch?v=E-dAnFdq8k8)
- 🎥 [JavaScript Value vs Reference Types — Programming with Mosh](https://www.youtube.com/watch?v=fD0t_DKREbE)

**[⬆ 返回目錄](#目錄)**

---

## 4. 隱式、顯式、名義、結構和鴨子類型

### 相關文章

- 📜 [What you need to know about Javascript's Implicit Coercion — Promise Tochi](https://dev.to/promhize/what-you-need-to-know-about-javascripts-implicit-coercion-e23)
- 📜 [JavaScript Type Coercion Explained — Alexey Samoshkin](https://medium.freecodecamp.org/js-type-coercion-explained-27ba3d9a2839)
- 📜 [Javascript Coercion Explained — Ben Garrison](https://hackernoon.com/javascript-coercion-explained-545c895213d3)
- 📜 [What exactly is Type Coercion in Javascript? - Stack Overflow](https://stackoverflow.com/questions/19915688/what-exactly-is-type-coercion-in-javascript)
- 📜 [You Don't Know JS: Types & Grammar [Book] — Kyle Simpson](https://www.oreilly.com/library/view/you-dont-know/9781491905159/ch04.html)
- 📜 [(Not) Everything in JavaScript is an Object - Daniel Li](http://blog.brew.com.hk/not-everything-in-javascript-is-an-object/)

- 📜 [ECMAScript 類型轉換 —— W3school](http://www.w3school.com.cn/js/pro_js_typeconversion.asp)
- 📜 [JavaScript 的怪癖 1：隱式類型轉換 —— justjavac](http://justjavac.com/javascript/2013/04/08/javascript-quirk-1-implicit-conversion-of-values.html)
- 📜 [JavaScript 運算子規則與隱式類型轉換詳解 —— 掘金](https://juejin.im/post/59ad2585f265da246a20e026)
- 📜 [聊一聊 JS 中的隱式類型轉換 —— SegmentFault](https://segmentfault.com/a/1190000004482388)
- 📜 [有趣的 JavaScript 隱式類型轉換 —— 博客園](https://www.cnblogs.com/yugege/p/5277883.html)
- 📜 [JavaScript 顯式類型轉換與隱式類型轉換 —— CSDN](https://blog.csdn.net/yangjvn/article/details/48284163)
- 📜 [你不知道的 JavaScript（中卷）強制類型轉換 —— 簡書](https://www.jianshu.com/p/777a89b4ed9a)
- 📜 [你懂 JavaScript 嗎？#8 強制轉型 —— cythilya](https://ithelp.ithome.com.tw/articles/10201512)
- 📜 [動態類型語言和鴨子類型 —— 曾探](http://book.51cto.com/art/201505/475153.htm)
- 📜 [Nominal & Structural Typing —— flow](https://flow.org/en/docs/lang/nominal-structural/)
- 📜 [What exactly is Type Coercion in Javascript? —— stackoverflow](https://stackoverflow.com/questions/19915688/what-exactly-is-type-coercion-in-javascript)
- 📜 [You Don't Know JS: Types & Grammar —— github](https://github.com/getify/You-Dont-Know-JS/blob/master/types%20&%20grammar/ch4.md)

### 相關影片

- 🎥 [== ? === ??? ...#@^% - Shirmung Bielefeld](https://www.youtube.com/watch?v=qGyqzN0bjhc&t)
- 🎥 [Coercion in Javascript - Hitesh Choudhary](https://www.youtube.com/watch?v=b04Q_vyqEG8)
- 🎥 [JavaScript Questions: What is Coercion? - Steven Hancock](https://www.youtube.com/watch?v=z4-8wMSPJyI)

- 🎥 [javascript 隱式轉換 —— 慕課網](https://www.imooc.com/video/5675)
- 🎥 [Javascript 基礎加強-類型轉換 —— 黑馬程序員](http://www.le.com/ptv/vplay/27767009.html)

**[⬆ 返回目錄](#目錄)**

---

<div id="5--vs--typeof-vs-instanceof"></div>

## 5. == vs ===、typeof vs instanceof

### 相關文章

- 📜 [JavaScript Double Equals vs. Triple Equals — Brandon Morelli](https://codeburst.io/javascript-double-equals-vs-triple-equals-61d4ce5a121a)
- 📜 [What is the difference between =, ==, and === in JS? — Codecademy](https://www.codecademy.com/en/forum_questions/558ea4f5e39efed371000508)
- 📜 [Should I use === or == equality comparison operator in JavaScript? — Panu Pitkamaki](https://bytearcher.com/articles/equality-comparison-operator-javascript/)
- 📜 [== vs === JavaScript: Double Equals and Coercion — AJ Meyghani](https://www.codementor.io/javascript/tutorial/double-equals-and-coercion-in-javascript)
- 📜 [Why Use the Triple-Equals Operator in JavaScript? — Louis Lazaris](https://www.impressivewebs.com/why-use-triple-equals-javascipt/)
- 📜 [What is the difference between == and === in JavaScript? — Craig Buckler](https://www.oreilly.com/learning/what-is-the-difference-between-and-in-javascript)
- 📜 [Why javascript's typeof always return "object"? — Stack Overflow](https://stackoverflow.com/questions/3787901/why-javascripts-typeof-always-return-object)
- 📜 [Checking Types in Javascript — Toby Ho](http://tobyho.com/2011/01/28/checking-types-in-javascript/)
- 📜 [How to better check data types in JavaScript — Webbjocke](https://webbjocke.com/javascript-check-data-types/)
- 📜 [Checking for the Absence of a Value in JavaScript — Tomer Aberbach](https://tomeraberba.ch/html/post/checking-for-the-absence-of-a-value-in-javascript.html)

- 📜 [JavaScript 中的相等性判斷 —— MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Equality_comparisons_and_sameness)
- 📜 [js 中 == 和 === 的區別 —— 掘金](https://juejin.im/entry/584918612f301e005716add6)
- 📜 [== vs === in Javascript —— CSDN](https://blog.csdn.net/w97531/article/details/82255225)
- 📜 [深入理解 javascript 之 typeof 和 instanceof —— CSDN](https://blog.csdn.net/mevicky/article/details/50353881)
- 📜 [JavaScript 的 typeof 的用途 —— justjavac](http://justjavac.com/javascript/2012/12/23/what-is-javascripts-typeof-operator-used-for.html)
- 📜 [一張圖看懂 Function 和 Object 的關係及簡述 instanceof 運算子 —— 掘金](https://juejin.im/post/58358606570c35005e4142bd)
- 📜 [淺談 instanceof 和 typeof 的實現原理 —— 掘金](https://juejin.im/post/5b0b9b9051882515773ae714)
- 📜 [js 中 typeof 與 instanceof 用法 —— 博客園](https://www.cnblogs.com/double405/p/5326311.html)

### 相關影片

- 🎥 [JavaScript - The typeof operator — Java Brains](https://www.youtube.com/watch?v=ol_su88I3kw)
- 🎥 [Javascript typeof operator — DevDelight](https://www.youtube.com/watch?v=qPYhTPt_SbQ)

**[⬆ 返回目錄](#目錄)**

---

## 6. 函數作用域(Function Scope)、區塊作用域(Block Scope)和詞法作用域(Lexical Scope)

### 相關文章

- 📜 [You Don't Know JS: Scope & Closures [Book] — Kyle Simpson](https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20%26%20closures/ch3.md)
- 📜 [The battle between Function Scope and Block Scope — Marius Herring](http://www.deadcoderising.com/2017-04-11-es6-var-let-and-const-the-battle-between-function-scope-and-block-scope/)
- 📜 [Emulating Block Scope in JavaScript — Josh Clanton](http://adripofjavascript.com/blog/drips/emulating-block-scope-in-javascript.html)
- 📜 [The Difference Between Function and Block Scope in JavaScript — Joseph Cardillo](https://medium.com/@josephcardillo/the-difference-between-function-and-block-scope-in-javascript-4296b2322abe)
- 📜 [Function Scopes and Block Scopes in JavaScript — Samer Buna](https://edgecoders.com/function-scopes-and-block-scopes-in-javascript-25bbd7f293d7)
- 📜 [Understanding Scope and Context in JavaScript | Ryan Morr](http://ryanmorr.com/understanding-scope-and-context-in-javascript/)
- 📜 [JavaScript Scope and Closures — Zell Liew](https://css-tricks.com/javascript-scope-closures/)
- 📜 [Understanding Scope in JavaScript — Wissam Abirached](https://developer.telerik.com/topics/web-development/understanding-scope-in-javascript/)
- 📜 [Speaking JavaScript - Variables: Scopes, Environments, and Closures — Dr. Axel Rauschmayer](http://speakingjs.com/es5/ch16.html)
- 📜 [Understanding Scope in JavaScript ― Hammad Ahmed](https://scotch.io/tutorials/understanding-scope-in-javascript)

- 📜 [變量作用域與解構賦值 —— 廖雪峰](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/0014344993159773a464f34e1724700a6d5dd9e235ceb7c000)
- 📜 [學習 Javascript 閉包（Closure） —— 阮一峰](http://www.ruanyifeng.com/blog/2009/08/learning_javascript_closures.html)
- 📜 [JavaScript 中詞法作用域、閉包與跳出閉包 —— SegmentFault](https://segmentfault.com/a/1190000006671020)
- 📜 [JavaScript 深入之詞法作用域和動態作用域 —— 掘金](https://juejin.im/entry/58e70077b123db15eb88dc7e)
- 📜 [深入理解閉包之前置知識 → 作用域與詞法作用域 —— 掘金](https://juejin.im/post/5afb0ae56fb9a07aa2138425)
- 📜 [What is lexical scope? —— stackoverflow](https://stackoverflow.com/questions/1047454/what-is-lexical-scope)
- 📜 [You Don't Know JS: Scope & Closures —— Kyle Simpson](https://github.com/fishenal/You-Dont-Know-JS/blob/master/scope%20&%20closures/ch2.md)

### 相關影片

- 🎥 [What Makes Javascript Weird ... and Awesome pt. 4 — LearnCode.academy](https://www.youtube.com/watch?v=SBwoFkRjZvE)
- 🎥 [Variable Scope in JavaScript — Kirupa Chinnathambi](https://www.youtube.com/watch?v=dhp57T3p760)
- 🎥 [JavaScript Block Scope and Function Scope — mmtuts](https://www.youtube.com/watch?v=aK_nuUAdr8E)
- 🎥 [What the Heck is Lexical Scope? — NWCalvank](https://www.youtube.com/watch?v=GhNA0r10MmA)

**[⬆ 返回目錄](#目錄)**

---

## 7. 表達式和陳述式

### 相關文章

- 📜 [All you need to know about Javascript's Expressions, Statements and Expression Statements — Promise Tochi](https://dev.to/promhize/javascript-in-depth-all-you-need-to-know-about-expressions-statements-and-expression-statements-5k2)
- 📜 [Function Expressions vs Function Declarations — Paul Wilkins](https://www.sitepoint.com/function-expressions-vs-declarations/)
- 📜 [JavaScript Function — Declaration vs Expression — Ravi Roshan](https://medium.com/@raviroshan.talk/javascript-function-declaration-vs-expression-f5873b8c7b38)
- 📜 [Function Declarations vs. Function Expressions — Mandeep Singh](https://medium.com/@mandeep1012/function-declarations-vs-function-expressions-b43646042052)
- 📜 [Function Declarations vs. Function Expressions — Anguls Croll](https://javascriptweblog.wordpress.com/2010/07/06/function-declarations-vs-function-expressions/)

- 📜 [js 表達式與陳述式 —— 博客園](https://www.cnblogs.com/xianshenglu/p/8386918.html)
- 📜 [JS 表達式和陳述式的區別 —— SegmentFault](https://segmentfault.com/q/1010000004102804)
- 📜 [JavaScript 中的表達式（expression）和陳述式/聲明（statement） —— CSDN](https://blog.csdn.net/mett_smith/article/details/78761247)
- 📜 [重讀 Axel 的 Javascript 中的 Expression vs Statement 一文 —— SegmentFault](https://segmentfault.com/a/1190000004565693)
- 📜 [Expressions versus statements in JavaScript —— Dr. Axel](http://2ality.com/2012/09/expressions-vs-statements.html)

### 相關影片

- 🎥 [Expressions vs. Statements in JavaScript — Hexlet](https://www.youtube.com/watch?v=WVyCrI1cHi8)
- 🎥 [JavaScript - Expression vs. Statement — WebTunings](https://www.youtube.com/watch?v=3jDpNGJkupA)

**[⬆ 返回目錄](#目錄)**

---

## 8. 立即執行函數、模組化、命名空間

### 相關文章

- 📜 [Mastering Immediately-Invoked Function Expressions ― Chandra Gundamaraju](https://medium.com/@vvkchandra/essential-javascript-mastering-immediately-invoked-function-expressions-67791338ddc6)
- 📜 [Do ES6 Modules make the case of IIFEs obsolete?](https://hashnode.com/post/do-es6-modules-make-the-case-of-iifes-obsolete-civ96wet80scqgc538un20es0)
- 📜 [A 10 minute primer to JavaScript modules, module formats, module loaders and module bundlers ― Jurgen Van de Moere](https://www.jvandemo.com/a-10-minute-primer-to-javascript-modules-module-formats-module-loaders-and-module-bundlers/)
- 📜 [Modules ― Exploring JS](http://exploringjs.com/es6/ch_modules.html)
- 📜 [ES modules: A cartoon deep-dive — Lin Clark](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/)
- 📜 [Understanding ES6 Modules — Craig Buckler](https://www.sitepoint.com/understanding-es6-modules/)
- 📜 [An overview of ES6 Modules in JavaScript — Brent Graham](https://blog.cloud66.com/an-overview-of-es6-modules-in-javascript/)
- 📜 [ES6 Modules in Depth — Nicolás Bevacqua](https://ponyfoo.com/articles/es6-modules-in-depth)
- 📜 [ES6 modules, Node.js and the Michael Jackson Solution — Alberto Gimeno](https://medium.com/dailyjs/es6-modules-node-js-and-the-michael-jackson-solution-828dc244b8b)

- 📜 [Javascript 模組化編程（一）：模塊的寫法 —— 阮一峰](http://www.ruanyifeng.com/blog/2012/10/javascript_module.html)
- 📜 [javascript 模組化編程-詳解立即執行函數表達式 —— 簡書](https://www.jianshu.com/p/4dbf4a4c8ebb)
- 📜 [Javascript 的匿名函數與自執行 —— 掘金](https://juejin.im/entry/57fee360a22b9d005b1d9ae3)
- 📜 [前端模組化——技術選型 —— SegmentFault](https://segmentfault.com/a/1190000006966358)
- 📜 [談談 Js 前端模組化規範 —— SegmentFault](https://segmentfault.com/a/1190000015991869#articleHeader8)

### 相關影片

- 🎥 [Immediately Invoked Function Expression - Beau teaches JavaScript — freeCodeCamp](https://www.youtube.com/watch?v=3cbiZV4H22c)
- 🎥 [Understanding JavaScript IIFE](https://www.youtube.com/watch?v=I5EntfMeIIQ)
- 🎥 [JavaScript Modules: ES6 Import and Export — Kyle Robinson](https://www.youtube.com/watch?v=_3oSWwapPKQ)
- 🎥 [ES6 - Modules — Ryan Christiani](https://www.youtube.com/watch?v=aQr2bV1BPyE)
- 🎥 [ES6 Modules in the Real World — Sam Thorogood](https://www.youtube.com/watch?v=fIP4pjAqCtQ)
- 🎥 [ES6 Modules — TempleCoding](https://www.youtube.com/watch?v=5P04OK6KlXA)

**[⬆ 返回目錄](#目錄)**

---

## 9. 訊息佇列和事件循環

### 相關文章

- 📜 [JavaScript Event Loop Explained — Anoop Raveendran](https://medium.com/front-end-hacking/javascript-event-loop-explained-4cd26af121d4)
- 📜 [The JavaScript Event Loop: Explained — Erin Sweson-Healey](https://blog.carbonfive.com/2013/10/27/the-javascript-event-loop-explained/)
- 📜 [What is the Event Loop in Javascript — WP Tutor.io](https://www.wptutor.io/web/js/javascript-event-loop)
- 📜 [Understanding JS: The Event Loop — Alexander Kondov](https://hackernoon.com/understanding-js-the-event-loop-959beae3ac40)
- 📜 [Understanding the JavaScript Event Loop — Ashish Gupta](https://www.zeolearn.com/magazine/understanding-the-javascript-event-loop)
- 📜 [Event Loop in Javascript — Manjula Dube](https://code.likeagirl.io/what-the-heck-is-event-loop-1e414fccef49)
- 📜 [The JavaScript Event Loop — Flavio Copes](https://flaviocopes.com/javascript-event-loop/)
- 📜 [How JavaScript works: Event loop — Alexander Zlatkov](https://blog.sessionstack.com/how-javascript-works-event-loop-and-the-rise-of-async-programming-5-ways-to-better-coding-with-2f077c4438b5)

- 📜 [並發模型與事件循環 —— MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/EventLoop)
- 📜 [JavaScript 運行機制詳解：再談 Event Loop —— 阮一峰](http://www.ruanyifeng.com/blog/2014/10/event-loop.html)
- 📜 [深入理解 JavaScript 事件循環 —— 博客園](https://www.cnblogs.com/dong-xu/p/7000163.html)
- 📜 [深入淺出 Javascript 事件循環機制 —— 知乎](https://zhuanlan.zhihu.com/p/26229293)
- 📜 [JS 事件循環機制（event loop）之宏任務、微任務 —— SegmentFault](https://segmentfault.com/a/1190000014940904#articleHeader7)
- 📜 [JavaScript：徹底理解同步、異步和事件循環 —— SegmentFault](https://segmentfault.com/a/1190000004322358)

### 相關影片

- 🎥 [What the heck is the event loop anyway? | JSConf EU — Philip Roberts](https://www.youtube.com/watch?v=8aGhZQkoFbQ)
- 🎥 [JavaScript Event Loop — ComScience Simplified](https://www.youtube.com/watch?v=XzXIMZMN9k4)
- 🎥 [I'm stuck in an Event Loop — Philip Roberts](https://www.youtube.com/watch?v=6MXRNXXgP_0)

**[⬆ 返回目錄](#目錄)**

---

## 10. setTimeout, setInterval 和 requestAnimationFrame

### 相關文章

- 📜 [setTimeout and setInterval — JavaScript.Info](https://javascript.info/settimeout-setinterval)
- 📜 [Why not to use setInterval — Akanksha Sharma](https://dev.to/akanksha_9560/why-not-to-use-setinterval--2na9)
- 📜 [setTimeout VS setInterval — Develoger](https://develoger.com/settimeout-vs-setinterval-cff85142555b)
- 📜 [Using requestAnimationFrame — Chris Coyier](https://css-tricks.com/using-requestanimationframe/)
- 📜 [Understanding JavaScript's requestAnimationFrame() — JavaScript Kit](http://www.javascriptkit.com/javatutors/requestanimationframe.shtml)
- 📜 [Handling time intervals in JavaScript - Amit Merchant](https://www.amitmerchant.com/Handling-Time-Intervals-In-Javascript/)

- 📜 [Window setTimeout() 方法 —— 菜鳥教程](http://www.runoob.com/jsref/met-win-settimeout.html)
- 📜 [Window setInterval() 方法 —— 菜鳥教程](http://www.runoob.com/jsref/met-win-setinterval.html)
- 📜 [關於 setTimeout —— 掘金](https://juejin.im/post/5aa4c47af265da239866e236)
- 📜 [你不知道的 Javascript：有趣的 setTimeout —— 掘金](https://juejin.im/post/5a77f8ce5188257a6d635d76)
- 📜 [原來你是這樣的 setTimeout —— 掘金](https://juejin.im/entry/5861ebf01b69e6006ce61d38)
- 📜 [setTimeout() 和 setInterval() 本質區別在哪裡？ —— SegmentFault](https://segmentfault.com/q/1010000005989491)
- 📜 [window.requestAnimationFrame —— MDN](https://developer.mozilla.org/zh-TW/docs/Web/API/Window/requestAnimationFrame)

- 📜 [requestAnimationFrame 知多少？ —— 博客園](http://www.cnblogs.com/onepixel/p/7078617.html)
- 📜 [CSS3 動畫那麼強，requestAnimationFrame 還有毛線用？ —— 張鑫旭](https://www.zhangxinxu.com/wordpress/2013/09/css3-animation-requestanimationframe-tween-%e5%8a%a8%e7%94%bb%e7%ae%97%e6%b3%95/)
- 📜 [「JavaScript 定時器」setInterval、setTimeout 和 requestAnimationFrame 淺析 —— SegmentFault](https://segmentfault.com/a/1190000014661035)
- 📜 [翻譯：setInterval 與 requestAnimationFrame 的時間間隔測試 —— SegmentFault](https://segmentfault.com/a/1190000000386368)
- 📜 [阿里前端面試題：requestAnimationFrame 實現類似 setInterval 的計時器 —— SegmentFault](https://segmentfault.com/q/1010000013909430)

### 相關影片

- 🎥 [Javascript: How setTimeout and setInterval works — Coding Blocks India](https://www.youtube.com/watch?v=6bPKyl8WYWI)
- 🎥 [setTimeout and setInterval in JavaScript — techsith](https://www.youtube.com/watch?v=TbCgGWe8LN8)
- 🎥 [JavaScript Timers — Steve Griffith](https://www.youtube.com/watch?v=0VVJSvlUgtg)
- 🎥 [JavaScript setTimeout, setInterval & clearInterval — DoingITeasyChannel](https://www.youtube.com/watch?v=BVALvvy5bZY)
- 🎥 [JavaScript setTimeOut and setInterval Explained — Theodore Anderson](https://www.youtube.com/watch?v=mVKfrWCOB60)

- 🎥 [setTimeout 和 setInterval —— 優酷](http://v.youku.com/v_show/id_XNTA4OTQ0NzA0.html)

**[⬆ 返回目錄](#目錄)**

---

## 11. JavaScript 引擎

### 相關文章

- 📜 [JavaScript Engines — Jen Looper](http://www.softwaremag.com/javascript-engines/)
- 📜 [Understanding How the Chrome V8 Engine Translates JavaScript into Machine Code — DroidHead](https://medium.freecodecamp.org/understanding-the-core-of-nodejs-the-powerful-chrome-v8-engine-79e7eb8af964)
- 📜 [Understanding V8’s Bytecode — Franziska Hinkelmann](https://medium.com/dailyjs/understanding-v8s-bytecode-317d46c94775)
- 📜 [How the V8 engine works? — Thibault Laurens](http://thibaultlaurens.github.io/javascript/2013/04/29/how-the-v8-engine-works/)
- 📜 [A Brief History of Google’s V8 Javascript Engine — Clair Smith](https://www.mediacurrent.com/blog/brief-history-googles-v8-javascript-engine/)

- 📜 [javascript 引擎 —— 百度百科](https://baike.baidu.com/item/javascript引擎/5356108)
- 📜 [V8(JavaScript 引擎) —— 百度百科](https://baike.baidu.com/item/V8/6178125)
- 📜 [圖解搞懂 JavaScript 引擎 Event Loop —— 掘金](https://juejin.im/post/5a6309f76fb9a01cab2858b1)3
- 📜 [V8 JavaScript 引擎：高性能的 ES2015+ —— justjavac](https://segmentfault.com/a/1190000010819020)
- 📜 [10 分鐘理解 JS 引擎的執行機制 —— SegmentFaut](https://segmentfault.com/a/1190000012806637)
- 📜 [V8 javascript 引擎 —— 博客園](https://www.cnblogs.com/weirdoQi/p/6609811.html)

### 相關影片

- 🎥 [JavaScript Engines: The Good Parts™ — Mathias Bynens & Benedikt Meurer](https://www.youtube.com/watch?v=5nmpokoRaZI)

**[⬆ 返回目錄](#目錄)**

---

## 12. Bitwise operators、型別陣列(Type Arrays) 和 Array Buffers

### 相關文章

- 📜 [Programming with JS: Bitwise Operations — Alexander Kondov](https://hackernoon.com/programming-with-js-bitwise-operations-393eb0745dc4)
- 📜 [Using JavaScript’s Bitwise Operators in Real Life — ian m](https://codeburst.io/using-javascript-bitwise-operators-in-real-life-f551a731ff5)
- 📜 [JavaScript Bitwise Operators — w3resource](https://www.w3resource.com/javascript/operators/bitwise-operator.php)
- 📜 [Bitwise Operators in Javascript — Joe Cha](https://medium.com/bother7-blog/bitwise-operators-in-javascript-65c4c69be0d3)
- 📜 [A Comprehensive Primer on Binary Computation and Bitwise Operators in Javascript — Paul Brown](https://medium.com/techtrument/a-comprehensive-primer-on-binary-computation-and-bitwise-operators-in-javascript-81acf8341f04)

- 📜 [Bitwise operators —— MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators)
- 📜 [型別陣列 —— MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Typed_arrays)
- 📜 [ArrayBuffer —— MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer)
- 📜 [JavaScript ArrayBuffer 淺析 —— 博客園](https://www.cnblogs.com/gradolabs/p/4762134.html)

### 相關影片

- 🎥 [JavaScript Bitwise Operators — Programming with Mosh](https://www.youtube.com/watch?v=mesu75PTDC8)

**[⬆ 返回目錄](#目錄)**

---

## 13. DOM 樹和渲染過程

### 相關文章

- 📜 [How To Understand and Modify the DOM in JavaScript — Tania Rascia](https://www.digitalocean.com/community/tutorials/introduction-to-the-dom)
- 📜 [JavaScript DOM Tutorial with Example — Guru99](https://www.guru99.com/how-to-use-dom-and-events-in-javascript.html)
- 📜 [What is the DOM? — Chris Coyier](https://css-tricks.com/dom/)
- 📜 [Traversing the DOM with JavaScript — Zell Liew](https://zellwk.com/blog/dom-traversals/)
- 📜 [Eloquent JavaScript [Book] — The Document Object Model](https://eloquentjavascript.net/14_dom.html)
- 📜 [DOM Tree](https://javascript.info/dom-nodes)
- 📜 [Render Tree Construction — Ilya Grigorik](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-tree-construction)

- 📜 [如何創建一個 DOM 樹 —— MDN](https://developer.mozilla.org/zh-TW/docs/Web/API/Document_Object_Model/How_to_create_a_DOM_tree)
- 📜 [HTML DOM 節點 —— W3school](http://www.w3school.com.cn/htmldom/dom_nodes.asp)
- 📜 [DOM 概述 —— 阮一峰](http://javascript.ruanyifeng.com/dom/node.html)
- 📜 [《JavaScript 闖關記》之 DOM（上）—— 掘金](https://juejin.im/post/583cbbfa61ff4b006ccc41fe)
- 📜 [《JavaScript 闖關記》之 DOM（下）—— 掘金](https://juejin.im/post/583cbc4961ff4b006ccc44fb)
- 📜 [掌握 DOM 操作 —— 掘金](https://juejin.im/entry/58314efd8ac2470061bb30fd)
- 📜 [操作 DOM —— 廖雪峰](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/001434500494451273e6b3dec9d411d9ba841dee8caec45000)
- 📜 [原來 CSS 與 JS 是這樣阻塞 DOM 解析和渲染的 —— 掘金](https://juejin.im/post/59c60691518825396f4f71a1)

### 相關影片

- 🎥 [JavaScript DOM — The Net Ninja](https://www.youtube.com/watch?v=FIORjGvT0kk)
- 🎥 [JavaScript DOM Crash Course — Traversy Media](https://www.youtube.com/watch?v=0ik6X4DJKCc)

- 🎥 [DOM 探索之基礎詳解篇 —— 慕課網](https://www.imooc.com/learn/488)
- 🎥 [DOM 事件探秘 —— 慕課網](https://www.imooc.com/learn/138)
- 🎥 [jQuery 基礎(二)DOM 篇 —— 慕課網](https://www.imooc.com/learn/530)
- 🎥 [JS 操作 DO 陣列物件屬性和方法 —— 愛奇藝](http://www.iqiyi.com/w_19rr19s08l.html)

**[⬆ 返回目錄](#目錄)**

---

## 14. 工廠函數和類別

### 相關文章

- 📜 [How To Use Classes in JavaScript — Tania Rascia](https://www.digitalocean.com/community/tutorials/understanding-classes-in-javascript)
- 📜 [Javascript Classes — Under The Hood — Majid](https://medium.com/tech-tajawal/javascript-classes-under-the-hood-6b26d2667677)
- 📜 [ES6 Classes — Nathaniel Foster](https://www.javascriptjanuary.com/blog/es6-classes)
- 📜 [Better JavaScript with ES6, Pt. II: A Deep Dive into Classes ― Peleke Sengstacke](https://scotch.io/tutorials/better-javascript-with-es6-pt-ii-a-deep-dive-into-classes)
- 📜 [Understand the Factory Design Pattern in Plain JavaScript — Aditya Agarwal](https://medium.com/front-end-hacking/understand-the-factory-design-pattern-in-plain-javascript-20b348c832bd)
- 📜 [JavaScript Factory Functions vs Constructor Functions vs Classes — Eric Elliott](https://medium.com/javascript-scene/javascript-factory-functions-vs-constructor-functions-vs-classes-2f22ceddf33e)
- 📜 [JavaScript Factory Functions with ES6+ — Eric Elliott](https://medium.com/javascript-scene/javascript-factory-functions-with-es6-4d224591a8b1)
- 📜 [Factory Functions in JavaScript — Josh Miller](https://atendesigngroup.com/blog/factory-functions-javascript)
- 📜 [The Factory Pattern in JS ES6 — SnstsDev](https://medium.com/@SntsDev/the-factory-pattern-in-js-es6-78f0afad17e9)
- 📜 [Class vs Factory function: exploring the way forward — Cristi Salcescu](https://medium.freecodecamp.org/class-vs-factory-function-exploring-the-way-forward-73258b6a8d15)

- 📜 [Class —— MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Classes)
- 📜 [類和 Instances —— 廖雪峰](https://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/00138682004077376d2d7f8cc8a4e2c9982f92788588322000)
- 📜 [Javascript 定義類別的三種方法 —— 阮一峰](http://www.ruanyifeng.com/blog/2012/07/three_ways_to_define_a_javascript_class.html)
- 📜 [【譯】ES6 的工廠函數 —— 掘金](https://juejin.im/post/59c8c8756fb9a00a681ae5bd)
- 📜 [JavaScript 陣列物件之單例、工廠、建構式模式 —— 掘金](https://juejin.im/entry/587992c961ff4b0065edf1ff)

### 相關影片

- 🎥 [JavaScript Factory Functions — Programming with Mosh](https://www.youtube.com/watch?v=jpegXpQpb3o)
- 🎥 [Factory Functions in JavaScript — Fun Fun Function](https://www.youtube.com/watch?v=ImwrezYhw4w)
- 🎥 [Javascript Tutorial Function Factories — Crypto Chan](https://www.youtube.com/watch?v=R7-IwpH80UE)

**[⬆ 返回目錄](#目錄)**

---

## 15. this、call、apply 和 bind

### 相關文章

- 📜 [How-to: call() , apply() and bind() in JavaScript — Niladri Sekhar Dutta](https://www.codementor.io/niladrisekhardutta/how-to-call-apply-and-bind-in-javascript-8i1jca6jp)
- 📜 [JavaScript’s Apply, Call, and Bind Methods are Essential for JavaScript Professionals — Richard Bovell](http://javascriptissexy.com/javascript-apply-call-and-bind-methods-are-essential-for-javascript-professionals/)
- 📜 [WTF is this - Understanding the this keyword, call, apply, and bind in JavaScript — Tyler McGinnis](https://tylermcginnis.com/this-keyword-call-apply-bind-javascript/)
- 📜 [Javascript: call(), apply() and bind() — Omer Goldberg](https://medium.com/@omergoldberg/javascript-call-apply-and-bind-e5c27301f7bb)
- 📜 [The difference between call / apply / bind — Ivan Sifrim](https://medium.com/@ivansifrim/the-differences-between-call-apply-bind-276724bb825b)
- 📜 [call(), apply() and bind() methods in JavaScript](https://tech.io/playgrounds/9799/learn-solve-call-apply-and-bind-methods-in-javascript)
- 📜 [Mastering 'this' in JavaScript: Callbacks and bind(), apply(), call() — Michelle Gienow](https://thenewstack.io/mastering-javascript-callbacks-bind-apply-call/)
- 📜 [JavaScript’s apply, call, and bind explained by hosting a cookout — Kevin Kononenko](https://dev.to/kbk0125/javascripts-apply-call-and-bind-explained-by-hosting-a-cookout-32jo)
- 📜 [How AND When to use bind, call, and apply in Javascript — Eigen X](https://www.eigenx.com/blog/https/mediumcom/eigen-x/how-and-when-to-use-bind-call-and-apply-in-javascript-77b6f42898fb)
- 📜 [JavaScript .bind() vs .apply() and .call() — Hack Sparrow](https://www.hacksparrow.com/javascript-bind-vs-apply-and-call.html)
- 📜 [call() — MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call)
- 📜 [bind() — MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind)
- 📜 [apply() — MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)
- 📜 [What is 'this' in JavaScript? — Daniel Li](http://blog.brew.com.hk/what-is-this-in-javascript/)
- 📜 [Let me explain to you what is `this`. (Javascript) — Jason Yu](https://dev.to/ycmjason/let-me-explain-to-you-what-is-this-javascript-44ja)

- 📜 [Javascript 的 this 用法 —— 阮一峰](http://www.ruanyifeng.com/blog/2010/04/using_this_keyword_in_javascript.html)
- 📜 [學會 JS 的 this 這一篇就夠了，根本不用記 —— 簡書](https://www.jianshu.com/p/6b4333e78bf5)
- 📜 [[譯] this（他喵的）到底是什麼 — 理解 JavaScript 中的 this、call、apply 和 bind —— 掘金](https://juejin.im/post/5b9f176b6fb9a05d3827d03f)
- 📜 [this、apply、call、bind —— 掘金](https://juejin.im/post/59bfe84351882531b730bac2)
- 📜 [使用 call、apply 和 bind 解決 js 中煩人的 this，事件綁定時的 this 和傳參問題 —— 博客園](https://www.cnblogs.com/tingyu-blog/p/6212392.html)
- 📜 [call、apply 和 bind 的原生實現 —— github](https://github.com/Abiel1024/blog/issues/16)
- 📜 [詳解 JS 中的 this、apply、call、bind(經典面試題) —— 腳本之家](https://www.jb51.net/article/124024.htm)

### 相關影片

- 🎥 [JavaScript call, apply and bind — techsith](https://www.youtube.com/watch?v=c0mLRpw-9rI)
- 🎥 [JavaScript Practical Applications of Call, Apply and Bind functions— techsith](https://www.youtube.com/watch?v=AYVYxezrMWA)
- 🎥 [JavaScript (call, bind, apply) — curious aatma](https://www.youtube.com/watch?v=Uy0NOXLBraE)
- 🎥 [Understanding Functions and 'this' In The World of ES2017 — Bryan Hughes](https://www.youtube.com/watch?v=AOSYY1_np_4)

- 🎥 [JavaScript 關於 this 關鍵字解釋 —— 愛奇藝](https://www.iqiyi.com/w_19rr1augsd.html)
- 🎥 [JS 關於作用域閉包和 this 的綜合面試題 —— 百度視頻](http://baidu.iqiyi.com/watch/845335533383874688.html?page=videoMultiNeed)
- 🎥 [js 陣列物件閉包陣列 12.函數中的 this —— 樂視視頻](http://www.le.com/ptv/vplay/27478413.html?ch=baidu_s)
- 🎥 [1.3.10-this 指向及 this 應用 —— 樂視視頻](http://www.le.com/ptv/vplay/24835911.html?ch=baidu_s)
- 🎥 [珠峰培訓 JavaScript 開發課程：關於 this 關鍵字、閉包作用域 —— 網易雲課堂](https://study.163.com/course/introduction/590005.htm)

**[⬆ 返回目錄](#目錄)**

---

## 16. new、建構式、instanceof 與 Instances

### 相關文章

- 📜 [建構式與 new 命令 —— 阮一峰](http://javascript.ruanyifeng.com/oop/basic.html)
- 📜 [Javascript 陣列物件編程（二）：建構式的繼承 —— 阮一峰](http://www.ruanyifeng.com/blog/2010/05/object-oriented_javascript_inheritance.html)
- 📜 [完整原型鏈詳細圖解(建構式、原型、實陣列物件) —— CSDN](https://blog.csdn.net/SpicyBoiledFish/article/details/71123162)
- 📜 [JavaScript 中建構式與 new 運算子的 Instances 詳解 —— PHP 中文網](http://www.php.cn/js-tutorial-376246.html)
- 📜 [建構式、Instances、原型、原型鏈之間的關係 —— CSDN](https://blog.csdn.net/yin_991/article/details/80954453)
- 📜 [深入理解 JS—instanceof 和原型鏈 —— CSDN](https://blog.csdn.net/cecilia620/article/details/71158048)
- 📜 [前端基礎進階（九）：詳解陣列物件、建構式、原型與原型鏈 —— 簡書](https://www.jianshu.com/p/15ac7393bc1f)
- 📜 [js 用 new 實體化物件與直接呼叫的 this 的區別 —— 簡書](https://www.jianshu.com/p/60ffc4831bff)
- 📜 [JavaScript 並非所有的東西陣列物件 —— justjavac](http://justjavac.com/javascript/2012/12/22/javascript-values-not-everything-is-an-object.html)
- 📜 [JavaScript instanceof 運算子深入剖析 —— IBM](https://www.ibm.com/developerworks/cn/web/1306_jiangjj_jsinstanceof/)

### 相關影片

- 🎥 [改良版的建構式 —— 樂視](http://www.le.com/ptv/vplay/27766889.html)

**[⬆ 返回目錄](#目錄)**

---

## 17. 原型繼承與原型鏈

### 相關文章

- 📜 [Javascript : Prototype vs Class — Valentin PARSY](https://medium.com/@parsyval/javascript-prototype-vs-class-a7015d5473b)
- 📜 [JavaScript engine fundamentals: optimizing prototypes — Mathias Bynens](https://mathiasbynens.be/notes/prototypes)
- 📜 [JavaScript Prototype — NC Patro](https://codeburst.io/javascript-prototype-cb29d82b8809)
- 📜 [Prototype in Javascript — Sandeep Ranjan](https://www.codementor.io/sandeepranjan2007/prototype-in-javascipt-knbve0lqo)
- 📜 [Prototypes in JavaScript — Rupesh Mishra](https://hackernoon.com/prototypes-in-javascript-5bba2990e04b)
- 📜 [Prototype in JavaScript: it’s quirky, but here’s how it works — Pranav Jindal](https://medium.freecodecamp.org/prototype-in-js-busted-5547ec68872)
- 📜 [Inheritance and the prototype chain — MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- 📜 [Master the JavaScript Interview: What’s the Difference Between Class & Prototypal Inheritance? — Eric Elliott](https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9)
- 📜 [Understanding JavaScript: Prototype and Inheritance — Alexander Kondov](https://hackernoon.com/understanding-javascript-prototype-and-inheritance-d55a9a23bde2)
- 📜 [Prototypal Inheritance — JavaScript.Info](https://javascript.info/prototype-inheritance)
- 📜 [How To Work with Prototypes and Inheritance in JavaScript — Tania Rascia](https://www.digitalocean.com/community/tutorials/understanding-prototypes-and-inheritance-in-javascript)
- 📜 [Master JavaScript Prototypes & Inheritance — Arnav Aggarwal](https://codeburst.io/master-javascript-prototypes-inheritance-d0a9a5a75c4e)
- 📜 [You Don't Know JS [Book] Chapter 5: Prototypes — Kyle Simpson](https://github.com/getify/You-Dont-Know-JS/blob/master/this%20%26%20object%20prototypes/ch5.md)
- 📜 [JavaScript’s Prototypal Inheritance Explained Using CSS — Nash Vail](https://medium.freecodecamp.org/understanding-prototypal-inheritance-in-javascript-with-css-93b2fcda75e4)
- 📜 [Prototypal Inheritance in JavaScript — Jannis Redmann](https://gist.github.com/derhuerst/a585c4916b1c361cc6f0)
- 📜 [Classical and Prototypical Inheritance in JavaScript — Danny Cornelisse](http://www.competa.com/blog/classical-prototypical-inheritance-javascript/)
- 📜 [Demystifying ES6 Classes And Prototypal Inheritance ― Neo Ighodaro](https://scotch.io/tutorials/demystifying-es6-classes-and-prototypal-inheritance)
- 📜 [Intro To Prototypal Inheritance — Dharani Jayakanthan](https://dev.to/danny/intro-to-prototypal-inheritance---js-9di)
- 📜 [Classes in JavaScript - Explained — Daniel Li](http://blog.brew.com.hk/classes-in-javascript-explained/)

- 📜 [繼承與原型鏈 —— MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- 📜 [建構式、原型與原型鏈 —— github](https://github.com/bigdots/blog/issues/1)
- 📜 [原型及原型鏈 —— github(1269 Star)](https://github.com/stone0090/javascript-lessons/tree/master/2.5-Prototype)
- 📜 [理清 javascript 中的陣列物件(一) 原型繼承 —— SegmentFault](https://segmentfault.com/a/1190000004282206)
- 📜 [JavaScript：繼承和原型鏈(譯) —— justjavac](http://justjavac.com/2015/12/09/inheritance-and-the-prototype-chain.html)
- 📜 [三張圖搞懂 JavaScript 的原型對象與原型鏈 —— 博客園](http://www.cnblogs.com/shuiyi/p/5305435.html)
- 📜 [一張圖讓你搞懂 JavaScript 的繼承與原型鏈 —— CSDN](https://blog.csdn.net/the__apollo/article/details/76774698)
- 📜 [JS 高級--原型鏈(一看就懂，但 18 歲以下請繞道) —— CSDN](https://blog.csdn.net/xiaotao_css/article/details/72782416)
- 📜 [原型繼承 —— 廖雪峰](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/0014344997013405abfb7f0e1904a04ba6898a384b1e925000)
- 📜 [JS 原型鏈與繼承別再被問倒了 —— 掘金](https://juejin.im/post/58f94c9bb123db411953691b)
- 📜 [征服 JavaScript 面試系列：類繼承和原型繼承的區別 —— 掘金](https://juejin.im/entry/5885db221b69e600592253e7)

### 相關影片

- 🎥 [Javascript Prototype Inheritance — Avelx](https://www.youtube.com/watch?v=sOrtAjyk4lQ)
- 🎥 [JavaScript Prototype Inheritance Explained pt. I — techsith](https://www.youtube.com/watch?v=7oNWNlMrkpc)
- 🎥 [JavaScript Prototype Inheritance Explained pt. II — techsith](https://www.youtube.com/watch?v=uIlj6_z_wL8)
- 🎥 [JavaScript Prototype Inheritance Explained — Kyle Robinson](https://www.youtube.com/watch?v=qMO-LTOrJaE)
- 🎥 [Advanced Javascript - Prototypal Inheritance In 1 Minute](https://www.youtube.com/watch?v=G6l5CHl67HQ)
- 🎥 [An Overview Of Classical Javascript Classes and Prototypal Inheritance — Pentacode](https://www.youtube.com/watch?v=phwzuiJJPpQ)
- 🎥 [Object Oriented JavaScript - Prototype — The Net Ninja](https://www.youtube.com/watch?v=4jb4AYEyhRc)
- 🎥 [Prototype in JavaScript — kudvenkat](https://www.youtube.com/watch?v=2rkEbcptR64)
- 🎥 [JavaScript Using Prototypes — O'Reilly](https://www.youtube.com/watch?v=oCwCcNvaXAQ)
- 🎥 [A Beginner's Guide to Javascript's Prototype — Tyler Mcginnis](https://www.youtube.com/watch?v=XskMWBXNbp0)

- 🎥 [JS 高級-07-原型鏈繼承 —— 樂視](http://www.le.com/ptv/vplay/27552753.html)
- 🎥 [JS 陣列物件和原型鏈簡介 —— 騰訊視頻](https://v.qq.com/x/page/b0511nwa7d3.html)

**[⬆ 返回目錄](#目錄)**

---

## 18. Object.create 和 Object.assign

### 相關文章

- 📜 [Object.create() — MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create)
- 📜 [Object.create in JavaScript — Rupesh Mishra](https://hackernoon.com/object-create-in-javascript-fa8674df6ed2)
- 📜 [Object.create(): the New Way to Create Objects in JavaScript — Rob Gravelle](https://www.htmlgoodies.com/beyond/javascript/object.create-the-new-way-to-create-objects-in-javascript.html)
- 📜 [Basic Inheritance with Object.create — Joshua Clanton](http://adripofjavascript.com/blog/drips/basic-inheritance-with-object-create.html)
- 📜 [Object.create() In JavaScript — GeeksforGeeks](https://www.geeksforgeeks.org/object-create-javascript/)
- 📜 [Understanding the difference between Object.create() and the new operator — Jonathan Voxland](https://medium.com/@jonathanvox01/understanding-the-difference-between-object-create-and-the-new-operator-b2a2f4749358)
- 📜 [JavaScript Object Creation: Patterns and Best Practices — Jeff Mott](https://www.sitepoint.com/javascript-object-creation-patterns-best-practises/)
- 📜 [Dealing With Objects in JavaScript With Object.assign, Object.keys and hasOwnProperty](https://alligator.io/js/dealing-with-objects/)
- 📜 [Copying Objects in JavaScript ― Orinami Olatunji](https://scotch.io/bar-talk/copying-objects-in-javascript)
- 📜 [Object.assign() — MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)
- 📜 [JavaScript: Object.assign() — Thiago S. Adriano](https://codeburst.io/javascript-object-assign-bc9696dcbb6e)

- 📜 [Object.create —— MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)
- 📜 [Object.assign —— MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)
- 📜 [Object.create vs Object.assign —— 慕課網手記](https://www.imooc.com/article/17591)
- 📜 [JS 中的 Object.assign()、Object.create()、Object.defineProperty() —— CSDN](https://blog.csdn.net/DeepLies/article/details/52915143)
- 📜 [es6 中 object.create()和 object.assign() —— 風信子博客](http://www.onlyfordream.cn/2018/03/19/es6%E4%B8%ADobject-create%E5%92%8Cobject-assign/)
- 📜 [Object-Assign-Deep —— github](https://github.com/saikojosh/Object-Assign-Deep)

### 相關影片

- 🎥 [Object.assign() explained — Aaron Writes Code](https://www.youtube.com/watch?v=aw7NfYhR5rc)
- 🎥 [Object.assign() Method — techsith](https://www.youtube.com/watch?v=9Ky4X6inpi4)

**[⬆ 返回目錄](#目錄)**

---

## 19. map、reduce、filter 等高階函數

### 相關文章

- 📜 [JavaScript Functional Programming — map, filter and reduce — Bojan Gvozderac](https://medium.com/jsguru/javascript-functional-programming-map-filter-and-reduce-846ff9ba492d)
- 📜 [Learn map, filter and reduce in Javascript — João Miguel Cunha](https://medium.com/@joomiguelcunha/learn-map-filter-and-reduce-in-javascript-ea59009593c4)
- 📜 [JavaScript’s Map, Reduce, and Filter — Dan Martensen](https://danmartensen.svbtle.com/javascripts-map-reduce-and-filter)
- 📜 [How to Use Map, Filter, & Reduce in JavaScript — Peleke Sengstacke](https://code.tutsplus.com/tutorials/how-to-use-map-filter-reduce-in-javascript--cms-26209)
- 📜 [JavaScript — Learn to Chain Map, Filter, and Reduce — Brandon Morelli](https://codeburst.io/javascript-learn-to-chain-map-filter-and-reduce-acd2d0562cd4)
- 📜 [Javascript data structure with map, reduce, filter and ES6 — Deepak Gupta](https://codeburst.io/write-beautiful-javascript-with-%CE%BB-fp-es6-350cd64ab5bf)
- 📜 [Understanding map, filter and reduce in Javascript — Luuk Gruijs](https://hackernoon.com/understanding-map-filter-and-reduce-in-javascript-5df1c7eee464)
- 📜 [Functional Programming in JS: map, filter, reduce (Pt. 5) — Omer Goldberg](https://hackernoon.com/functional-programming-in-js-map-filter-reduce-pt-5-308a205fdd5f)
- 📜 [JavaScript: Map, Filter, Reduce — William S. Vincent](https://wsvincent.com/functional-javascript-map-filter-reduce/)
- 📜 [Arrow Functions: Fat and Concise Syntax in JavaScript — Kyle Pennell](https://www.sitepoint.com/es6-arrow-functions-new-fat-concise-syntax-javascript/)
- 📜 [JavaScript: Arrow Functions for Beginners — Brandon Morelli](https://codeburst.io/javascript-arrow-functions-for-beginners-926947fc0cdc)
- 📜 [When (and why) you should use ES6 arrow functions — and when you shouldn’t — Cynthia Lee](https://medium.freecodecamp.org/when-and-why-you-should-use-es6-arrow-functions-and-when-you-shouldnt-3d851d7f0b26)
- 📜 [JavaScript — Learn & Understand Arrow Functions — Brandon Morelli](https://codeburst.io/javascript-learn-understand-arrow-functions-fe2083533946)
- 📜 [(JavaScript )=> Arrow functions — sigu](https://medium.com/podiihq/javascript-arrow-functions-27d4c3334b83)
- 📜 [A possibility to use Async/Await for filter(), find(), forEach(), map() and reduce() methods in Array - Ruwan Geeganage](https://www.linkedin.com/pulse/possibility-use-asyncawait-filter-find-foreach-map-reduce-geeganage/)

- 📜 [高階函數 —— 廖雪峰](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/001434499355829ead974e550644e2ebd9fd8bb1b0dd721000)
- 📜 [ES5 中新增的 Array 方法詳細說明 —— 張鑫旭](https://www.zhangxinxu.com/wordpress/2013/04/es5%e6%96%b0%e5%a2%9e%e6%95%b0%e7%bb%84%e6%96%b9%e6%b3%95/)
- 📜 [一張圖看懂 JavaScript 中陣列的迭代方法：forEach、map、filter、reduce、every、some —— 掘金](https://juejin.im/post/5835808067f3560065ed4ab2)
- 📜 [Transducing（上）－《JavaScript 輕量級函數式編程》 —— SegmentFault](https://segmentfault.com/a/1190000012127329)

### 相關影片

- 🎥 [Map, Filter and Reduce — Lydia Hallie](https://www.youtube.com/watch?v=UXiYii0Y7Nw)
- 🎥 [Functional JavaScript: Map, forEach, Reduce, Filter — Theodore Anderson](https://www.youtube.com/watch?v=vytzLlY_wmU)
- 🎥 [JavaScript Array superpowers: Map, Filter, Reduce (part I) — Michael Rosata](https://www.youtube.com/watch?v=qTeeVd8hOFY)
- 🎥 [JavaScript Array superpowers: Map, Filter, Reduce (part 2) — Michael Rosata](https://www.youtube.com/watch?v=gIm9xLYudL0)
- 🎥 [JavaScript Higher Order Functions - Filter, Map, Sort & Reduce — Epicop](https://www.youtube.com/watch?v=zYBeEPxNSbw)
- 🎥 [[Array Methods 2/3] .filter + .map + .reduce — CodeWithNick](https://www.youtube.com/watch?v=4qWlqD0yYTU)
- 🎥 [Arrow functions in JavaScript - What, Why and How — Fun Fun Function](https://www.youtube.com/watch?v=6sQDTgOqh-I)

**[⬆ 返回目錄](#目錄)**

---

## 20. 純函數, 函數副作用和狀態變化

### 相關文章

- 📜 [Javascript and Functional Programming — Pure Functions — Omer Goldberg](https://hackernoon.com/javascript-and-functional-programming-pt-3-pure-functions-d572bb52e21c)
- 📜 [Master the JavaScript Interview: What is a Pure Function? — Eric Elliott](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976)
- 📜 [JavaScript: What Are Pure Functions And Why Use Them? — James Jeffery](https://medium.com/@jamesjefferyuk/javascript-what-are-pure-functions-4d4d5392d49c)
- 📜 [Pure functions in JavaScript — @nicoespeon](http://www.nicoespeon.com/en/2015/01/pure-functions-javascript/)
- 📜 [Functional Programming: Pure Functions — Arne Brasseur](https://www.sitepoint.com/functional-programming-pure-functions/)
- 📜 [Pure Functions In Javascript — Krunal](https://appdividend.com/2017/04/10/pure-functions-in-javascript/)
- 📜 [Making your JavaScript Pure — Jack Franklin](https://alistapart.com/article/making-your-javascript-pure)
- 📜 [To mutate, or not to mutate, in JavaScript](https://slemgrim.com/mutate-or-not-to-mutate/)
- 📜 [Arrays, Objects and Mutations — Federico Knüssel](https://medium.com/@fknussel/arrays-objects-and-mutations-6b23348b54aa)
- 📜 [The State of Immutability — Maciej Sikora](https://medium.com/dailyjs/the-state-of-immutability-169d2cd11310)
- 📜 [How to deal with dirty side effects in your pure functional JavaScript — James Sinclair](https://jrsinclair.com/articles/2018/how-to-deal-with-dirty-side-effects-in-your-pure-functional-javascript/)
- 📜 [Preventing Side Effects in JavaScript — David Walsh](https://davidwalsh.name/preventing-sideeffects-javascript)

- 📜 [純函數(Pure Function) —— React.js 小書](http://huziketang.mangojuice.top/books/react/lesson32)
- 📜 [JavaScript Functional Programming：純函數 —— 寧皓網](https://ninghao.net/blog/4634)
- 📜 [js 函數的副作用分析 —— 腳本之家](https://www.jb51.net/article/28079.htm)
- 📜 [如何使用純函數式 JavaScript 處理髒副作用 —— 掘金](https://juejin.im/post/5b82bdb351882542e241ed32?utm_medium=hao.caibaojian.com&utm_source=hao.caibaojian.com)
- 📜 [原生 JavaScript 實現 state 狀態管理系統 —— 博客園](http://www.cnblogs.com/zhangycun/p/9403335.html)

### 相關影片

- 🎥 [Pure Functions — Hexlet](https://www.youtube.com/watch?v=dZ41D6LDSBg)
- 🎥 [Pure Functions - Functional Programming in JavaScript — Paul McBride](https://www.youtube.com/watch?v=Jh_Uzqzz_wM)
- 🎥 [JavaScript Pure Functions — Seth Alexander](https://www.youtube.com/watch?v=frT3H-eBmPc)

**[⬆ 返回目錄](#目錄)**

---

## 21. 閉包

### 相關文章

- 📜 [Closures — MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
- 📜 [I never understood JavaScript closures — Olivier De Meulder](https://medium.com/dailyjs/i-never-understood-javascript-closures-9663703368e8)
- 📜 [Closure — JavaScript.Info](https://javascript.info/closure)
- 📜 [Understand JavaScript Closures With Ease — Richard Bovell](http://javascriptissexy.com/understand-javascript-closures-with-ease/)
- 📜 [Understanding JavaScript Closures — Codesmith](https://codeburst.io/understanding-javascript-closures-da6aab330302)
- 📜 [Understand Closures in JavaScript — Brandon Morelli](https://codeburst.io/understand-closures-in-javascript-d07852fa51e7)
- 📜 [A simple guide to help you understand closures in JavaScript — Prashant Ram](https://medium.freecodecamp.org/javascript-closures-simplified-d0d23fa06ba4)
- 📜 [Understanding JavaScript Closures: A Practical Approach — Paul Upendo](https://scotch.io/tutorials/understanding-javascript-closures-a-practical-approach)
- 📜 [Understanding JavaScript: Closures — Alexander Kondov](https://hackernoon.com/understanding-javascript-closures-4188edf5ea1b)
- 📜 [How to use JavaScript closures with confidence — Léna Faure](https://hackernoon.com/how-to-use-javascript-closures-with-confidence-85cd1f841a6b)
- 📜 [JavaScript closures by example — tyler](https://howchoo.com/g/mge2mji2mtq/javascript-closures-by-example)

- 📜 [閉包 —— MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Closures)
- 📜 [ECMAScript 閉包（closure）—— w3school](http://www.w3school.com.cn/js/pro_js_functions_closures.asp)
- 📜 [學習 Javascript 閉包（Closure） —— 阮一峰](http://www.ruanyifeng.com/blog/2009/08/learning_javascript_closures.html)
- 📜 [閉包 —— 廖雪峰](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/00143449934543461c9d5dfeeb848f5b72bd012e1113d15000)
- 📜 [一次性搞懂 JavaScript 閉包 —— 簡書](https://www.jianshu.com/p/796e903754f1)
- 📜 [JavaScript 閉包 —— SegmentFault](https://segmentfault.com/a/1190000006875662)
- 📜 [js 匿名自執行函數中閉包的高級使用 —— 掘金](https://juejin.im/entry/5800eb7da22b9d005b36156e)
- 📜 [高效使用 JavaScript 閉包 —— 掘金](https://juejin.im/entry/59df405251882551bf7e58c6#comment)

### 相關影片

- 🎥 [Javascript Closure — techsith](https://www.youtube.com/watch?v=71AtaJpJHw0)
- 🎥 [Closures — Fun Fun Function](https://www.youtube.com/watch?v=CQqwU2Ixu-U)
- 🎥 [Closures in JavaScript — techsith](https://www.youtube.com/watch?v=-xqJo5VRP4A)
- 🎥 [JavaScript Closures 101: What is a closure? — JavaScript Tutorials](https://www.youtube.com/watch?v=yiEeiMN2Khs)
- 🎥 [Closures — freeCodeCamp](https://www.youtube.com/watch?v=1JsJx1x35c0)
- 🎥 [JavaScript Closures — CodeWorkr](https://www.youtube.com/watch?v=-rLrGAXK8WE)

- 🎥 [JavaScript 閉包和閉包面試題 —— 愛奇藝](http://www.iqiyi.com/w_19rr1amael.html)
- 🎥 [js 陣列物件閉包陣列 11.閉包 —— 樂視](http://www.le.com/ptv/vplay/27478410.html)
- 🎥 [白賀翔\_函數(閉包) —— 樂視](http://www.le.com/ptv/vplay/30505852.html)

**[⬆ 返回目錄](#目錄)**

---

## 22. High Order Functions

### 相關文章

- 📜 [Higher-Order Functions — Eloquent JavaScript [Book]](https://eloquentjavascript.net/05_higher_order.html)
- 📜 [Higher-Order Functions in JavaScript — M. David Green](https://www.sitepoint.com/higher-order-functions-javascript/)
- 📜 [Higher Order Functions: Using Filter, Map and Reduce for More Maintainable Code — Guido Schmitz](https://medium.freecodecamp.org/higher-order-functions-in-javascript-d9101f9cf528)
- 📜 [First-class and Higher Order Functions: Effective Functional JavaScript — Hugo Di Francesco](https://hackernoon.com/effective-functional-javascript-first-class-and-higher-order-functions-713fde8df50a)
- 📜 [Higher Order Functions in JavaScript — John Hannah](https://www.lullabot.com/articles/higher-order-functions-in-javascript)
- 📜 [Higher-order Functions — Richard Bovell](http://javascriptissexy.com/tag/higher-order-functions/)
- 📜 [Higher Order Functions in JavaScript — Zsolt Nagy](http://www.zsoltnagy.eu/higher-order-functions-in-javascript/)
- 📜 [Fun With Higher Order Functions In JavaScript — Derick](https://derickbailey.com/2015/10/21/fun-with-higher-order-functions-in-javascript/)
- 📜 [Just a reminder on how to use high order functions — Pedro Filho](https://github.com/pedroapfilho/high-order-functions)
- 📜 [How to use JavaScript closures with confidence — Léna Faure](https://hackernoon.com/how-to-use-javascript-closures-with-confidence-85cd1f841a6b)
- 📜 [JavaScript closures by example — tyler](https://howchoo.com/g/mge2mji2mtq/javascript-closures-by-example)

### 相關影片

- 🎥 [JavaScript Higher Order Functions & Arrays — Traversy Media](https://www.youtube.com/watch?v=rRgD1yVwIvE)
- 🎥 [Higher Order Functions — Fun Fun Function](https://www.youtube.com/watch?v=BMUiFMZr7vk)
- 🎥 [Higher Order Functions in Javascript — Raja Yogan](https://www.youtube.com/watch?v=dTlpYnmBW9I)
- 🎥 [Higher Order Iterators in JavaScript — Fun Fun Function](https://www.youtube.com/watch?v=GYRMNp1SKXA)
- 🎥 [Higher Order Functions in JavaScript — The Coding Train](https://www.youtube.com/watch?v=H4awPsyugS0)

**[⬆ Back to Top](#table-of-contents)**

---

## 23. 遞迴

### 相關文章

- 📜 [Recursion in JavaScript — Kevin Ennis](https://medium.freecodecamp.org/recursion-in-javascript-1608032c7a1f)
- 📜 [Understanding Recursion in JavaScript — Zak Frisch](https://medium.com/@zfrisch/understanding-recursion-in-javascript-992e96449e03)
- 📜 [Learn and Understand Recursion in JavaScript — Brandon Morelli](https://codeburst.io/learn-and-understand-recursion-in-javascript-b588218e87ea)
- 📜 [Recursion in Functional JavaScript — M. David Green](https://www.sitepoint.com/recursion-functional-javascript/)
- 📜 [Programming with JS: Recursion — Alexander Kondov](https://hackernoon.com/programming-with-js-recursion-31371e2bf808)
- 📜 [Anonymous Recursion in JavaScript — simo](https://dev.to/simov/anonymous-recursion-in-javascript)
- 📜 [Recursion, iteration and tail calls in JS — loverajoel](http://www.jstips.co/en/javascript/recursion-iteration-and-tail-calls-in-js/)
- 📜 [Understanding Recursion in JavaScript with Confidence — Jay](https://www.thecodingdelight.com/understanding-recursion-javascript/)

- 📜 [求解釋 js 遞迴 —— SegmentFault](https://segmentfault.com/q/1010000003942347)
- 📜 [JavaScript 中的遞迴 —— 掘金](https://juejin.im/post/5948c0d8fe88c2006a939e2a)
- 📜 [遞迴（上）－《JavaScript 輕量級函數式編程》 —— 掘金](https://juejin.im/post/59c1d91d6fb9a00a53275f79)
- 📜 [遞迴（下）－《JavaScript 輕量級函數式編程》 —— 掘金](https://juejin.im/post/59c87fb46fb9a00a437b1a2e)
- 📜 [尾呼叫和尾遞迴 —— 掘金](https://juejin.im/post/5acdd7486fb9a028ca53547c)
- 📜 [幾個經典遞迴問題用 js 實現 —— CSDN](https://blog.csdn.net/qianqianstd/article/details/75807462)
- 📜 [遞迴函數的幾個例子 —— CSDN](https://blog.csdn.net/x_i_xw/article/details/72026868)

### 相關影片

- 🎥 [Recursion In JavaScript — techsith](https://www.youtube.com/watch?v=VtG0WAUvq2w)
- 🎥 [Recursion — Fun Fun Function](https://www.youtube.com/watch?v=k7-N8R0-KY4)
- 🎥 [Recursion and Recursive Functions — Hexlet](https://www.youtube.com/watch?v=vLhHyGTkjCs)
- 🎥 [Recursion: Recursion() - JS Monthly — Lucas da Costa](https://www.youtube.com/watch?v=kGXVsd8pBLw)
- 🎥 [Recursive Function in JavaScript — kudvenkat](https://www.youtube.com/watch?v=uyjsR9eNTIw)

**[⬆ 返回目錄](#目錄)**

---

## 24. 集合 (Collections)

### 相關文章

- 📜 [ES6 In Depth: Collections — Jason Orendorff](https://hacks.mozilla.org/2015/06/es6-in-depth-collections/)
- 📜 [ES6 Collections: Using Map, Set, WeakMap, WeakSet — Kyle Pennell](https://www.sitepoint.com/es6-collections-map-set-weakmap-weakset/)
- 📜 [ES6 WeakMaps, Sets, and WeakSets in Depth — Nicolás Bevacqua](https://ponyfoo.com/articles/es6-weakmaps-sets-and-weaksets-in-depth)
- 📜 [Introduction to Sets in JavaScript — Alligator.io](https://alligator.io/js/sets-introduction/)
- 📜 [Introduction to Maps in JavaScript — Alligator.io](https://alligator.io/js/maps-introduction/)
- 📜 [Map, Set, WeakMap and WeakSet — JavaScript.Info](https://javascript.info/map-set-weakmap-weakset)
- 📜 [Maps in ES6 - A Quick Guide — Ben Mildren](https://dev.to/mildrenben/maps-in-es6---a-quick-guide-35pk)
- 📜 [ES6 — Set vs Array — What and when? — Maya Shavin](https://medium.com/front-end-hacking/es6-set-vs-array-what-and-when-efc055655e1a)
- 📜 [ES6 — Map vs Object — What and when? — Maya Shavin](https://medium.com/front-end-hacking/es6-map-vs-object-what-and-when-b80621932373)
- 📜 [ES6: Working with Sets in JavaScript — Dead Code Rising](http://www.deadcoderising.com/es6-working-with-sets-in-javascript/)
- 📜 [Array vs Set vs Map vs Object — Real-time use cases in Javascript (ES6/ES7) — Rajesh Babu](https://codeburst.io/array-vs-set-vs-map-vs-object-real-time-use-cases-in-javascript-es6-47ee3295329b)
- 📜 [How to create an array of unique values in JavaScript using Sets — Claire Parker-Jones](https://dev.to/claireparker/how-to-create-an-array-of-unique-values-in-javascript-using-sets-5dg6)
- 📜 [What You Should Know About ES6 Maps — Just Chris](https://hackernoon.com/what-you-should-know-about-es6-maps-dc66af6b9a1e)
- 📜 [ES6 Maps in Depth — Nicolás Bevacqua](https://ponyfoo.com/articles/es6-maps-in-depth)

### 相關影片

- 🎥 [JavaScript ES6 / ES2015 Set, Map, WeakSet and WeakMap — Traversy Media](https://www.youtube.com/watch?v=ycohYSx5h9w)
- 🎥 [The Differences between ES6 Maps and Sets — Steve Griffith](https://www.youtube.com/watch?v=m4abICrldQI)

**[⬆ Back to Top](#table-of-contents)**

---

## 25. Promise

### 相關文章

- 📜 [Promise — MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- 📜 [JavaScript Promises for Dummies ― Jecelyn Yeen](https://scotch.io/tutorials/javascript-promises-for-dummies)
- 📜 [Understanding promises in JavaScript — Gokul N K](https://hackernoon.com/understanding-promises-in-javascript-13d99df067c1)
- 📜 [Master the JavaScript Interview: What is a Promise? — Eric Elliott](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261)
- 📜 [An Overview of JavaScript Promises — Sandeep Panda](https://www.sitepoint.com/overview-javascript-promises/)
- 📜 [How to use Promises in JavaScript — Prashant Ram](https://medium.freecodecamp.org/promises-in-javascript-explained-277b98850de)
- 📜 [Implementing Promises In JavaScript — Maciej Cieslar](https://medium.freecodecamp.org/how-to-implement-promises-in-javascript-1ce2680a7f51)
- 📜 [JavaScript: Promises explained with simple real life analogies — Shruti Kapoor](https://codeburst.io/javascript-promises-explained-with-simple-real-life-analogies-dd6908092138)
- 📜 [Promises for Asynchronous Programming — Exploring JS](http://exploringjs.com/es6/ch_promises.html)
- 📜 [JavaScript Promises Explained By Gambling At A Casino — Kevin Kononenko](https://blog.codeanalogies.com/2018/08/26/javascript-promises-explained-by-gambling-at-a-casino/)
- 📜 [ES6 Promises: Patterns and Anti-Patterns — Bobby Brennan](https://medium.com/datafire-io/es6-promises-patterns-and-anti-patterns-bbb21a5d0918)
- 📜 [A Simple Guide to ES6 Promises — Brandon Morelli](https://codeburst.io/a-simple-guide-to-es6-promises-d71bacd2e13a)
- 📜 [The ES6 Promises — Manoj Singh Negi](https://codeburst.io/the-es6-promises-87a979ab27e4)
- 📜 [ES6 Promises in Depth — Nicolás Bevacqua](https://ponyfoo.com/articles/es6-promises-in-depth)

- 📜 [使用 promises —— MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Using_promises)
- 📜 [Promise —— MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- 📜 [Promie — 廖雪峰](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/0014345008539155e93fc16046d4bb7854943814c4f9dc2000)
- 📜 [JavaScript Promise：去而復返 —— 司徒正美](https://www.cnblogs.com/rubylouvre/p/3495286.html)
- 📜 [(上面的原文)JavaScript Promise：簡介 —— Web Fundamentals](https://developers.google.com/web/fundamentals/primers/promises#_1)
- 📜 [1 分鐘讀完《10 分鐘學會 JavaScript 的 Async/Await》 —— justjavac](https://segmentfault.com/a/1190000011813934)
- 📜 [JavaScript Promise 迷你書（中文版）](https://juejin.im/entry/56499ae160b2d1404c4f8834)
- 📜 [JavaScript 進階之路——認識和使用 Promise，重構你的 Js 代碼 —— 博客園](https://www.cnblogs.com/yunfeifei/p/4453690.html)

### 相關影片

- 🎥 [Let's Learn ES6 - Promises — Ryan Christiani](https://www.youtube.com/watch?v=vQ3MoXnKfuQ)
- 🎥 [JavaScript ES6 / ES2015 Promises — Traversy Media](https://www.youtube.com/watch?v=XJEHuBZQ5dU)
- 🎥 [Promises — Fun Fun Function](https://www.youtube.com/watch?v=2d7s3spWAzo)
- 🎥 [Error Handling Promises in JavaScript — Fun Fun Function](https://www.youtube.com/watch?v=f8IgdnYIwOU)

- 🎥 [Promise 入門 —— 慕課網](https://www.imooc.com/learn/949)

**[⬆ 返回目錄](#目錄)**

---

## 26. async/await

### 相關文章

- 📜 [async/await — JavaScript.Info](https://javascript.info/async-await)
- 📜 [Understanding async/await in Javascript — Gokul N K](https://hackernoon.com/understanding-async-await-in-javascript-1d81bb079b2c)
- 📜 [Asynchronous Programming — Eloquent JavaScript](https://eloquentjavascript.net/11_async.html)
- 📜 [Exploring Async/Await Functions in JavaScript — Alligator.io](https://alligator.io/js/async-functions/)
- 📜 [Asynchronous Javascript using async/await — Joy Warugu](https://scotch.io/tutorials/asynchronous-javascript-using-async-await)
- 📜 [Modern Asynchronous JavaScript with async/await — Flavio Copes](https://flaviocopes.com/javascript-async-await/)
- 📜 [Asynchronous JavaScript: From Callback Hell to Async and Await — Demir Selmanovic](https://www.toptal.com/javascript/asynchronous-javascript-async-await-tutorial)
- 📜 [Javascript — ES8 Introducing async/await Functions — Ben Garrison](https://medium.com/@_bengarrison/javascript-es8-introducing-async-await-functions-7a471ec7de8a)
- 📜 [How to escape async/await hell — Aditya Agarwal](https://medium.freecodecamp.org/avoiding-the-async-await-hell-c77a0fb71c4c)
- 📜 [Understanding JavaScript’s async await — Nicolás Bevacqua](https://ponyfoo.com/articles/understanding-javascript-async-await)
- 📜 [JavaScript Async/Await: Serial, Parallel and Complex Flow — TechBrij](https://techbrij.com/javascript-async-await-parallel-sequence)
- 📜 [Asynchronous Programming — Exploring JS](http://exploringjs.com/es6/ch_async.html)
- 📜 [From JavaScript Promises to Async/Await: why bother? — Chris Nwamba](https://blog.pusher.com/promises-async-await/)
- 📜 [Flow Control in Modern JS: Callbacks to Promises to Async/Await — Craig Buckler](https://www.sitepoint.com/flow-control-callbacks-promises-async-await/)
- 📜 [JavaScript: Promises and Why Async/Await Wins the Battle — Nick Parsons](https://dzone.com/articles/javascript-promises-and-why-asyncawait-wins-the-ba)

### 相關影片

- 🎥 [Async + Await — Wes Bos](https://www.youtube.com/watch?v=9YkUCxvaLEk)
- 🎥 [Asynchrony: Under the Hood — Shelley Vohr](https://www.youtube.com/watch?v=SrNQS8J67zc)
- 🎥 [async/await in JavaScript - What, Why and How — Fun Fun Function](https://www.youtube.com/watch?v=568g8hxJJp4&index=3&list=PL0zVEGEvSaeHJppaRLrqjeTPnCH6)

**[⬆ Back to Top](#table-of-contents)**

---

## 27. 資料結構

### 相關文章

- 📜 [Data Structures in JavaScript — Thon Ly](https://medium.com/siliconwat/data-structures-in-javascript-1b9aed0ea17c)
- 📜 [Algorithms and Data Structures in JavaScript — Oleksii Trekhleb](https://itnext.io/algorithms-and-data-structures-in-javascript-a71548f902cb)
- 📜 [Data Structures: Objects and Arrays ― Chris Nwamba](https://scotch.io/courses/10-need-to-know-javascript-concepts/data-structures-objects-and-arrays)
- 📜 [Data structures in JavaScript — Benoit Vallon](http://blog.benoitvallon.com/data-structures-in-javascript/data-structures-in-javascript/)
- 📜 [Playing with Data Structures in Javascript — Anish K.](https://blog.cloudboost.io/playing-with-data-structures-in-javascript-stack-a55ebe50f29d)
- 📜 [The Little Guide of Queue in JavaScript — Germán Cutraro](https://hackernoon.com/the-little-guide-of-queue-in-javascript-4f67e79260d9)
- 📜 [All algorithms writing with JavaScript in the book 'Algorithms Fourth Edition'](https://github.com/barretlee/algorithms)
- 📜 [Collection of classic computer science paradigms in JavaScript](https://github.com/nzakas/computer-science-in-javascript)
- 📜 [All the things you didn't know you wanted to know about data structures](https://github.com/jamiebuilds/itsy-bitsy-data-structures)

- 📜 [來我們淺談一下 js 的資料結構 —— 簡書](https://www.jianshu.com/p/5e0e8d183102)
- 📜 [JavaScript 中的演算法與資料結構 —— 簡書](https://www.jianshu.com/nb/16835496)
- 📜 [學 JS 必看-JavaScript 資料結構深度剖析 —— 大道至簡的博客](http://blog.sina.com.cn/s/blog_7b9c5e4101017mjt.html)
- 📜 [js 中基礎資料結構陣列去重問題 —— 掘金](https://juejin.im/entry/586effe0da2f600053d85a9a)

### 相關影片

- 🎥 [Algorithms in JavaScript — Seth Koch](https://www.youtube.com/watch?v=PylQlISSH8U&list=PLujX4CIdBGCa-65N3uN8CDbUMrYsHBrz-)
- 🎥 [Algorithms In Javascript | Ace Your Interview — Eduonix Learning Solutions](https://www.youtube.com/watch?v=H_EBPZgiAas&list=PLDmvslp_VR0zYUSth_8O69p4_cmvZEgLa)
- 🎥 [Data Structures and Algorithms in JavaScript — freeCodeCamp](https://www.youtube.com/watch?v=Gj5qBheGOEo&list=PLWKjhJtqVAbkso-IbgiiP48n-O-JQA9PJ)

- 🎥 [JavaScript 資料結構-運算子 —— 樂視](http://www.le.com/ptv/vplay/27606964.html)

**[⬆ 返回目錄](#目錄)**

---

## 28. 耗性能操作 (Expensive Operation) 和 時間複雜度 (Big O Notation)

### 相關文章

- 📜 [Big O Notation in Javascript — César Antón Dorantes](https://medium.com/cesars-tech-insights/big-o-notation-javascript-25c79f50b19b)
- 📜 [Time Complexity/Big O Notation — Tim Roberts](https://medium.com/javascript-scene/time-complexity-big-o-notation-1a4310c3ee4b)
- 📜 [Big O in JavaScript — Gabriela Medina](https://medium.com/@gmedina229/big-o-in-javascript-36ff67766051)
- 📜 [Big O Search Algorithms in JavaScript — Bradley Braithwaite](http://www.bradoncode.com/blog/2012/04/big-o-algorithm-examples-in-javascript.html)
- 📜 [Time Complexity Analysis in JavaScript — Jennifer Bland](https://www.jenniferbland.com/time-complexity-analysis-in-javascript/)
- 📜 [Algorithms in plain English: time complexity and Big-O Notation — Michael Olorunnisola](https://medium.freecodecamp.org/time-is-complex-but-priceless-f0abd015063c)

- 📜 [時間複雜度 O(log n) 意味著什麼？ —— 掘金](https://juejin.im/entry/593f56528d6d810058a355f4)
- 📜 [演算法的時間複雜度和空間複雜度 —— 掘金](https://juejin.im/entry/5a49f7d36fb9a0450a67b269)
- 📜 [演算法（一）時間複雜度 —— 掘金](https://juejin.im/post/58d15f1044d90400691834d4)
- 📜 [Big O Search Algorithms in JavaScript —— Bradley Braithwaite](http://www.bradoncode.com/blog/2012/04/big-o-algorithm-examples-in-javascript.html)
- 📜 [Time Complexity Analysis in JavaScript — Jennifer Bland](https://www.jenniferbland.com/time-complexity-analysis-in-javascript/)

### 相關影片

- 🎥 [JavaScript: Intro to Big O Notation and Function Runtime — Eric Traub](https://www.youtube.com/watch?v=HgA5VOFan5E)
- 🎥 [Essential Big O for JavaScript Developers — Dave Smith](https://www.youtube.com/watch?v=KatlvCFHPRo)
- 🎥 [Big O Notation - Time Complexity Analysis — WebTunings](https://www.youtube.com/watch?v=ALl86xJiTD8)

**[⬆ 返回目錄](#目錄)**

---

## 29. 演算法

### 相關文章

- 📜 [Data Structures and Algorithms using ES6](https://github.com/Crizstian/data-structure-and-algorithms-with-ES6)
- 📜 [Algorithms and data structures implemented in JavaScript with explanations and links to further readings](https://github.com/trekhleb/javascript-algorithms)
- 📜 [JS: Interview Algorithm](http://www.thatjsdude.com/interview/js1.html)
- 📜 [Algorithms in JavaScript — Thon Ly](https://medium.com/siliconwat/algorithms-in-javascript-b0bed68f4038)
- 📜 [JavaScript Objects, Square Brackets and Algorithms — Dmitri Grabov](https://medium.freecodecamp.org/javascript-objects-square-brackets-and-algorithms-e9a2916dc158)
- 📜 [Atwood's Law applied to CS101 - Classic algorithms and data structures implemented in JavaScript](https://github.com/felipernb/algorithms.js)
- 📜 [Data Structures and Algorithms library in JavaScript](https://github.com/yangshun/lago)
- 📜 [Collection of computer science algorithms and data structures written in JavaScript](https://github.com/idosela/algorithms-in-javascript)

- 📜 [十大經典排序演算法總結（JavaScript 描述） —— 掘金](https://juejin.im/post/57dcd394a22b9d00610c5ec8)
- 📜 [在 JavaScript 中學習資料結構與演算法 —— 掘金](https://juejin.im/post/594dfe795188250d725a220a#comment)
- 📜 [JS 中可能用得到的全部的排序演算法 —— 掘金](https://juejin.im/post/58c9d5fb1b69e6006b686bce)
- 📜 [JS 家的排序演算法 —— 簡書](https://www.jianshu.com/p/1b4068ccd505)
- 📜 [前端常見演算法的 JS 實現 —— SegmentFault](https://segmentfault.com/a/1190000008593715)
- 📜 [前端面試中的常見的演算法問題 ——蒲小花的博客](https://www.jackpu.com/qian-duan-mian-shi-zhong-de-chang-jian-de-suan-fa-wen-ti/)

### 相關影片

- 🎥 [Javascript 實現二叉樹演算法 —— 慕課網](https://www.imooc.com/learn/888)

**[⬆ 返回目錄](#目錄)**

---

## 30. 繼承, 多型和代碼複用

### 相關文章

- 📜 [Class inheritance, super — JavaScript.Info](https://javascript.info/class-inheritance)
- 📜 [Inheritance in JavaScript — MDN](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Inheritance)
- 📜 [Inheritance in JavaScript — Rupesh Mishra](https://hackernoon.com/inheritance-in-javascript-21d2b82ffa6f)
- 📜 [Simple Inheritance with JavaScript — David Catuhe](https://www.sitepoint.com/simple-inheritance-javascript/)
- 📜 [JavaScript — Inheritance, delegation patterns and Object linking — NC Patro](https://codeburst.io/javascript-inheritance-25fe61ab9f85)
- 📜 [Object Oriented JavaScript: Polymorphism with examples — Knoldus Blogs](https://blog.knoldus.com/object-oriented-javascript-polymorphism-with-examples/)
- 📜 [Program Like Proteus — A beginner’s guide to polymorphism in Javascript — Sam Galson](https://medium.com/yld-engineering-blog/program-like-proteus-a-beginners-guide-to-polymorphism-in-javascript-867bea7c8be2)
- 📜 [Object-oriented JavaScript: A Deep Dive into ES6 Classes — Jeff Mott](https://www.sitepoint.com/object-oriented-javascript-deep-dive-es6-classes/)

- 📜 [JS 陣列物件編程之：封裝、繼承、多型 —— 博客園](https://www.cnblogs.com/Leo_wl/p/5734794.html)
- 📜 [Javascript 的繼承與多型 —— 簡書](https://www.jianshu.com/p/5cb692658704)
- 📜 [js:陣列物件編程，帶你認識封裝、繼承和多型 —— 掘金](https://juejin.im/post/59396c96fe88c2006afc2707)
- 📜 [JavaScript 中的「多繼承」 —— 掘金](https://zhuanlan.zhihu.com/p/34693209)
- 📜 [代碼複用模式 —— github](https://github.com/TooBug/javascript.patterns/blob/master/chapter6.markdown)
- 📜 [深入理解 JavaScript：代碼複用模式(推薦篇) —— 湯姆大叔](http://www.cnblogs.com/TomXu/archive/2012/04/24/2438050.html)
- 📜 [深入理解 JavaScript：代碼複用模式(避免篇) —— 湯姆大叔](https://www.cnblogs.com/TomXu/archive/2012/04/23/2438005.html)

### 相關影片

- 🎥 [Inheritance in JavaScript — kudvenkat](https://www.youtube.com/watch?v=yXlFR81tDBM)
- 🎥 [JavaScript ES6 Classes and Inheritance — Traversy Media](https://www.youtube.com/watch?v=RBLIm5LMrmc)
- 🎥 [Polymorphism in JavaScript — kudvenkat](https://www.youtube.com/watch?v=zdovG9cuEBA)

**[⬆ 返回目錄](#目錄)**

---

## 31. 設計模式

### 相關文章

- 📜 [4 JavaScript Design Patterns You Should Know — Devan Patel](https://scotch.io/bar-talk/4-javascript-design-patterns-you-should-know)
- 📜 [JavaScript Design Patterns – Beginner's Guide to Mobile Web Development — Soumyajit Pathak](https://medium.com/beginners-guide-to-mobile-web-development/javascript-design-patterns-25f0faaaa15)
- 📜 [JavaScript Design Patterns — Akash Pal](https://medium.com/front-end-hacking/javascript-design-patterns-ed9d4c144c81)
- 📜 [Javascript Design Patterns: What They Are & How To Use Them — Patrick Simpson](https://seesparkbox.com/foundry/javascript_design_patterns)
- 📜 [All the 23 (GoF) design patterns implemented in Javascript — Felipe Beline](https://github.com/fbeline/Design-Patterns-JS)
- 📜 [Learning JavaScript Design Patterns — Addy Osmani](https://addyosmani.com/resources/essentialjsdesignpatterns/book/)

- 📜 [設計模式 —— 阮一峰](http://javascript.ruanyifeng.com/library/designpattern.html)
- 📜 [JavaScript 設計模式 —— 掘金](https://juejin.im/post/59df4f74f265da430f311909)
- 📜 [學用 JavaScript 設計模式 —— 極客學院](http://wiki.jikexueyuan.com/project/javascript-design-patterns/)
- 📜 [[面試專題]JS 設計模式 —— SegmentFault](https://segmentfault.com/a/1190000010914032)
- 📜 [JavaScript Patterns 中譯本 —— github](https://github.com/lxj/javascript.patterns)

### 相關影片

- 🎥 [JavaScript Design Patterns — Udacity](https://www.udacity.com/course/javascript-design-patterns--ud989)

- 🎥 [HTML5 課程大綱 2-11JS 設計模式](https://tv.sohu.com/v/dXMvMjQwNzYwNzQ4Lzg5NzM2MDA3LnNodG1s.html)

**[⬆ 返回目錄](#目錄)**

---

## 32. 偏函數 (Partial Applications)、柯理化 (Currying)、Compose 與 Pipe

### 相關文章

- 📜 [Use function composition in JavaScript — Rémi](https://www.codementor.io/michelre/use-function-composition-in-javascript-gkmxos5mj)
- 📜 [Currying in JavaScript ES6 — Adam Bene](https://blog.benestudio.co/currying-in-javascript-es6-540d2ad09400)
- 📜 [Composition and Currying Elegance in JavaScript — Pragyan Das](https://medium.com/@pragyan88/writing-middleware-composition-and-currying-elegance-in-javascript-8b15c98a541b)
- 📜 [Functional JavaScript: Function Composition For Every Day Use — Joel Thoms](https://hackernoon.com/javascript-functional-composition-for-every-day-use-22421ef65a10)
- 📜 [Functional Composition: compose() and pipe() — Anton Paras](https://medium.com/@acparas/what-i-learned-today-july-2-2017-ab9a46dbf85f)
- 📜 [Why The Hipsters Compose Everything: Functional Composing In JavaScript — A. Sharif](http://busypeoples.github.io/post/functional-composing-javascript/)
- 📜 [A Gentle Introduction to Functional JavaScript pt III: Functions for making functions — James Sinclair](https://jrsinclair.com/articles/2016/gentle-introduction-to-functional-javascript-functions/)
- 📜 [Curry And Compose (why you should be using something like ramda in your code) — jsanchesleao](https://jsleao.wordpress.com/2015/02/22/curry-and-compose-why-you-should-be-using-something-like-ramda-in-your-code/)
- 📜 [Function Composition in JavaScript with Pipe — Andy Van Slaars](https://vanslaars.io/post/create-pipe-function/)
- 📜 [Practical Functional JavaScript with Ramda — Andrew D'Amelio, Yuri Takhteyev](https://developer.telerik.com/featured/practical-functional-javascript-ramda/)
- 📜 [The beauty in Partial Application, Currying, and Function Composition — Joel Thoms](https://hackernoon.com/the-beauty-in-partial-application-currying-and-function-composition-d885bdf0d574)
- 📜 [Curry or Partial Application? — Eric Elliott](https://medium.com/javascript-scene/curry-or-partial-application-8150044c78b8)
- 📜 [Partial Application in JavaScript — Ben Alman](http://benalman.com/news/2012/09/partial-application-in-javascript/)
- 📜 [Partial Application of Functions — Functional Reactive Ninja](https://hackernoon.com/partial-application-of-functions-dbe7d9b80760)
- 📜 [Currying vs Partial Application — Deepak Gupta](https://codeburst.io/javascript-currying-vs-partial-application-4db5b2442be8)
- 📜 [Partial Application in ECMAScript 2015 — Ragan Wald](http://raganwald.com/2015/04/01/partial-application.html)
- 📜 [Functional Composition in Javascript — Joe Cortopassi](https://joecortopassi.com/articles/functional-composition-in-javascript/)
- 📜 [So You Want to be a Functional Programmer pt. I — Charles Scalfani](https://medium.com/@cscalfani/so-you-want-to-be-a-functional-programmer-part-1-1f15e387e536)
- 📜 [So You Want to be a Functional Programmer pt. II — Charles Scalfani](https://medium.com/@cscalfani/so-you-want-to-be-a-functional-programmer-part-2-7005682cec4a)
- 📜 [So You Want to be a Functional Programmer pt. III — Charles Scalfani](https://medium.com/@cscalfani/so-you-want-to-be-a-functional-programmer-part-3-1b0fd14eb1a7)
- 📜 [So You Want to be a Functional Programmer pt. IV — Charles Scalfani](https://medium.com/@cscalfani/so-you-want-to-be-a-functional-programmer-part-4-18fbe3ea9e49)
- 📜 [So You Want to be a Functional Programmer pt. V — Charles Scalfani](https://medium.com/@cscalfani/so-you-want-to-be-a-functional-programmer-part-5-c70adc9cf56a)
- 📜 [Functional-Light JavaScript Chapter 3: Managing Function Inputs — Kyle Simpson](https://github.com/getify/Functional-Light-JS/blob/master/manuscript/ch3.md)

- 📜 [Javascript 函數式編程之偏函數 —— CSDN](https://blog.csdn.net/qq_42129063/article/details/81874314)
- 📜 [JavaScript 專題之偏函數 —— SegmentFault](https://segmentfault.com/a/1190000010686144)
- 📜 [柯理化和偏函數有什麼區別？ —— SegmentFault](https://segmentfault.com/q/1010000008626058)
- 📜 [Javascript 偏函數與柯理化 —— CSDN](https://blog.csdn.net/neweastsun/article/details/75947785)
- 📜 [柯理化(curry) —— JS 函數式編程指南](https://llh911001.gitbooks.io/mostly-adequate-guide-chinese/content/ch4.html)
- 📜 [代碼組合(compose) —— JS 函數式編程指南](https://llh911001.gitbooks.io/mostly-adequate-guide-chinese/content/ch5.html)
- 📜 [關於 javascript 函數式編程中 compose 的實現 —— SegmentFault](https://segmentfault.com/a/1190000008394749)
- 📜 [實現 compose 的五種思路 —— SegmentFault](https://segmentfault.com/a/1190000011447164)
- 📜 [JavaScript 函數式編程之函陣列合函數 compose 和 pipe 的實現 —— SegmentFault](https://segmentfault.com/a/1190000015102804)
- 📜 [JavaScript 輕量級函數式編程-第 4 章:組合函數 ——掘金](https://juejin.im/post/59a62f3d6fb9a0248363fd9d#comment)

### 相關影片

- 🎥 [Compose vs Pipe: Functional Programming in JavaScript — Chyld Studios](https://www.youtube.com/watch?v=Wl2ejJOqHUU)
- 🎥 [JavaScript Functional Programing: Compose — Theodore Anderson](https://www.youtube.com/watch?v=jigHxo9YR30)
- 🎥 [Function Composition - Functional JavaScript — NWCalvank](https://www.youtube.com/watch?v=mth5WpEc4Qs)
- 🎥 [JavaScript Function Composition Explained — Theodore Anderson](https://www.youtube.com/watch?v=Uam37AlzPYw)
- 🎥 [Let's code with function composition — Fun Fun Function](https://www.youtube.com/watch?v=VGB9HbL1GHk)
- 🎥 [Partial Application vs. Currying — NWCalvank](https://www.youtube.com/watch?v=DzLkRsUN2vE)
- 🎥 [JavaScript Partial Application — Theodore Anderson](https://www.youtube.com/watch?v=jkebgHEcvac)

**[⬆ 返回目錄](#目錄)**

---

## 33. 代碼整潔之道

### 相關文章

- 📜 [Clean Code concepts adapted for JavaScript — Ryan McDermott](https://github.com/ryanmcdermott/clean-code-javascript)
- 📜 [JavaScript Clean Coding Best Practices — András Tóth](https://blog.risingstack.com/javascript-clean-coding-best-practices-node-js-at-scale/)
- 📜 [Function parameters in JavaScript Clean Code — Kevin Peters](https://medium.com/@kevin_peters/function-parameters-in-javascript-clean-code-4caac109159b)
- 📜 [Clean Code JavaScript — Sarah Drasner](https://css-tricks.com/clean-code-javascript/)
- 📜 [Keeping your code clean — Samuel James](https://codeburst.io/keeping-your-code-clean-d30bcffd1a10)
- 📜 [Best Practices for Using Modern JavaScript Syntax — M. David Green](https://www.sitepoint.com/modern-javascript-best-practices/)

- 📜 [[譯] JavaScript 代碼整潔之道 —— 邊城](https://www.zcfy.cc/article/clean-code-javascript-readme-md-at-master-ryanmcdermott-clean-code-javascript-github-2273.html)
- 📜 [Javascript 編程風格 —— 阮一峰](http://www.ruanyifeng.com/blog/2012/04/javascript_programming_style.html)
- 📜 [重構 - 代碼整潔之道 —— 掘金](https://juejin.im/post/5a5b2a5c6fb9a01cbc6e59f9)
- 📜 [讓你的代碼更簡短，更整潔，更易讀的 ES6 小技巧 —— 掘金](https://juejin.im/post/5a7d71836fb9a063435ecf51)
- 📜 [Web 前端：11 個讓你代碼整潔的原則 —— 伯樂在線](http://blog.jobbole.com/23617/)

**[⬆ 返回目錄](#目錄)**

---

## 34. 變量提升 (Hoisting)

### 相關文章

- 📜 [JavaScript Scoping and Hoisting —— Ben Cherry](http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html)
- 📜 [[翻譯] JavaScript Scoping and Hoisting —— SegmentFault](https://segmentfault.com/a/1190000004345355#articleHeader5)

- 📜 [JavaScript 變量提升 —— 菜鳥教程](http://www.runoob.com/js/js-hoisting.html)
- 📜 [ES6 變量作用域與提升：變量的生命週期詳解 —— 掘金](https://juejin.im/post/59905bea6fb9a03c34192c51)

**[⬆ 返回目錄](#目錄)**

---

## 35. Memoization

### 相關文章

- 📜 [JavaScript Memoization —— 司徒正美](https://www.cnblogs.com/rubylouvre/archive/2009/08/06/1540678.html)
- 📜 [memoization 提升遞迴效率 —— 博客園](https://www.cnblogs.com/yingshuizy/p/4517102.html)
- 📜 [如何提升 JavaScript 的遞迴效率 —— 51CTO](http://developer.51cto.com/art/201010/231513.htm)
- 📜 [JavaScript 高級技巧 Memoization —— SegmentFaut](https://segmentfault.com/a/1190000016703106)

**[⬆ 返回目錄](#目錄)**

---

## 36. 二進制, 十六進制, 十進制, 科學記數法

### 相關文章

- 📜 [二、八、十、十六進制轉換(圖解篇) —— 博客園](http://www.cnblogs.com/gaizai/p/4233780.html)
- 📜 [JavaScript 讀寫二進制數據 —— 掘金](https://juejin.im/post/5b93dadaf265da0a857a58a3)

### 相關影片

- 🎥 [二進制、十進制、十六進制互相轉化很難嗎？ —— 百度視頻](http://baishi.baidu.com/watch/7873060963471478456.html)

**[⬆ 返回目錄](#目錄)**

---
