---
layout: post
title: "Structural Coding Style"
date: 2013-04-01 11:08
comments: true
categories: [polydice]
---
愚人節快樂～
<!-- More -->

<h3>DRY & CoC</h3>
流行不能跟，潮流不能擋。目前程式設計師面臨了兩大潮流：Don't Repeat Your Code (DRY) 和 Convention over configuration (CoC)。而 Ruby on Rails 即為運用兩大潮流到極致的語言及網頁框架。雖然我嘴巴常說好懶得寫程式，但殊不知自己寫出來的程式多的嚇死人，完全忽視了這股潮流，沉浸在繁雜的程式架構上，常常不知不覺讓費了很多時間與精神在修改及維護網站上。<br />
oop老師常常說『程式設計是展開性的』，你常常先寫一個大架構再慢慢的填寫裡面的小物件，你可以以物件的形式一直增加的你的程式。以這次實作為例，我可能會需要使用到資料表的evaluation來分析以字串形式儲存的Hash或Array，此時就可以在model中多加一個method

{% codeblock %}
def eval_info
	return eval(self.info)
enf
{% endcodeblock %}

如此就可以將分析的過程包裝起來，一來可以減少eval(app.info)的寫法散佈在網站的各個角落外，還可以達到information hiding的特性，避免可能發生的安全問題。

<h3>ujs</h3>
為了避免HTML, CSS, Javascript混雜在一起而產生網站維護上的問題，Unobtrusive JavaScript (ujs) 被廣為推廣。身為一個 programmer newbie，常常會把Javascript的function嵌進HTML像這樣
{% codeblock %}
<div class="btn" onclick="hello();"></div>
{% endcodeblock %}
點選這個div就會call function hello()，未來如果改了hello()的參數或function名稱，就要回頭找HTML我哪裡呼叫了hello()，找到最後頭昏昏眼花花還製造了一推蟲子而令人不勝其擾。使用ujs，你就可以設定在頁面開始時，哪些物件會bind哪些事件，範例如下：

{% codeblock index.html %}
<div id="hello_button" class="btn"></div>
{% endcodeblock %}

{% codeblock index.js %}
window.onload = function() {
    document.getElementById('hello_button').onClick = hello;
};
{% endcodeblock %}
如此一來你就可以直接在js檔中修改你要binding的物件和事件，避免蒐集散落一地的code的困擾。

<h3>IA與UX</h3>
Information Architecture (IA)是一套設計方法，主要是規劃如何組織及標籤資料(organizing & labeling data)，使訊息可以被有效的傳輸，讓使用者擁有美好的使用經驗。以我的理解而言，就是要假設自己是個使用者，想想我會希望使用怎樣的產品、會喜歡怎樣的設計。這似乎又與User Expeirence(UX)的經營環環相扣且息息相關，日前聽了系上畢業的學長介紹台積電中的企業系統整合處(BSID)，其主要開發電子化商務、合作平台、商業智慧、CRM 和 SRM 等與使用者有直接關係的商品，此部門就非常強調UX，除了系統最基本的需求-正確性外，該部門也很重視簡單、快速、直覺的設計介面，希望提供更好的使用者體驗。

<h3>小結</h3>
洋洋灑灑的得知許多舉足輕重的概念，但無法落實也是枉然。期許自己未來在架設系統時也可以慢條斯理、有條不紊的撰寫每一行程式，將自己的構想以結構化且物件導向的方式呈現在使用者面前，使系統更加容易維護，同時也節省不必要的資源浪費。