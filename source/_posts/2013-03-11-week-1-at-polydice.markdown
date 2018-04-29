---
layout: post
title: "Week One @Polydice"
date: 2013-03-11 00:27
comments: true
categories: [polydice]
---
{% img /images/2013-03-11.jpg %}
我的實習週記

<!--more-->

<h3>[我在做甚麼]</h3>
三月分我進行的專案是撰寫類似<a href="http://www.appdata.com/">AppData</a>的網站，使用者可以自行輸入app_id，系統會先過濾掉無效的id（像是id重複或是無效），再由網站管理者做人工確認，最後將app做排序呈現在首頁。

<h3>[DB migrate]</h3>
如果預估資料量少的話（<del>約數百到千筆</del>萬筆內）可適用 Rails 內建的 ActiveRecord ，ActiveRecord 為 Object-relational mapping 的應用，可以將 SQL 語法包裝起來，讓使用者在操作DB時可以更加便利並增加程式的可讀性及安全性。

<h3><a href="http://en.wikipedia.org/wiki/Object-relational_mapping">[甚麼是 Object-relational mapping？]</a></h3>
一種技術，實現物件導向的概念，以物件表現列、以屬性表現欄，以純OOP的概念來操控資料庫。像是rails的ActiveRecord和 .NET Entity Framework。

<h3>[FB API client library]</h3>
因為要調查FB APP的排行榜，必須透過 fb api 取得 app 的使用人數。我選擇使永cardinalblue所開發的<a href="https://github.com/cardinalblue/rest-graph">rest-graph</a> 作 client library，但icook較常使用<a href="https://github.com/arsduo/koala">koala</a>，兩個工具其實非常類似，都協助取得 access token 以利 fb graph 的分析。

<h3>[Web crawler]</h3>
我習慣用nokogiri來爬取網路資料，但這個工具可能對針對特定CSS進行網頁分析是比較有幫助的，如果是要取得get/post所傳送的資料，利用<a href="https://github.com/typhoeus/typhoeus">Typhoeus</a>相對而言是比較有效率的。
