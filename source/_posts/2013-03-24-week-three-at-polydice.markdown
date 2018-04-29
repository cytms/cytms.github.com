---
layout: post
title: "About Front-end"
date: 2013-03-24 18:50
comments: true
categories: [polydice]
---

{% img /images/view-one.png %}
scss, less, css 傻傻分不清楚

<!--more-->

與勞倫司先生確認好網頁架構後，感覺寫出比較像樣的東西了<br/>
這禮拜正著手為它鋪上表皮。

這次我選用以bootstrap為基礎開發的<a href="https://github.com/TalksLab/metro-bootstrap">metro</a>作為template。
bootstrap因為包裝了Jquery-ui及css template，讓許多開發者愛不釋手，並開發出各式各樣的客製化樣板。<a href="https://github.com/thomas-mcdonald/bootstrap-sass">這裡</a>有個方便的套件可以讓新手更快速的掌握bootstrap，只要更改bootstap.scss即可瞬產生出你想要的樣板。<br/>

boostrap metro是talkslab仿造windows 8的樣式開發而成的套件，其雖然很華麗，但他在less檔中有些參數沒有設好以至於在套用時會出現一些小問題，因此我將它的css轉成scss，如此你可以比較方便的修改他們的共同參數。

{% codeblock %}
sass-convert --from css --to scss [CSS_FILE] > [SCSS_FILE]
{% endcodeblock %}

再來你會遇到一個問題：icon路徑的對應。<br/>
首先不要慌張，找到你的config/application.rb
{% codeblock %}
config.assets.paths << Rails.root.join("app", "assets", "[FOLDER]")
{% endcodeblock %}

我的解決方法是將scss檔改附檔名變成scss.erb檔，在相對應的路徑改成

{% codeblock %}
<%= asset_path('[FILE_NAME]') + '?#iefix' %>
{% endcodeblock %}

如此它就會自動尋找app/assets/[FOLDER]中叫[FILE_NAME]的檔案，此法可以快又有效解決你路徑上的疑難雜症。

<h4>目前我遇到了兩個問題：</h4>

1) 切頁問題，因為使用<code> redirect :back </code>使我在管理者頁按delete時都會使頁面重洗一次跳到最上方。想到的解決方式為使用ajax執行delete，並將同頁的該欄位隱藏起來以避免一直洗刷頁面。<br/>
{% img /images/view-three.png %}<br/>
按完delete後會跑到第一個tab的頁面：s<br/>
{% img /images/view-two.png %}

2) 使用者頁面計算量大，因為在view中進行排名計算，使頁面有點累隔，想到的解決方法有兩個：其一為儲存排名狀態於db中，其二是請worker每日更新時儲存排名狀態於global value之中讓每個使用者都可以共享它。<br/>