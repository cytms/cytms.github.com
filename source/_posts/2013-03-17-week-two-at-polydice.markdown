---
layout: post
title: "MVC Notes"
date: 2013-03-17 22:59
comments: true
categories: [polydice]
---

{% img /images/2013-03-17.jpg %}
萬事起頭難

<!--more-->

<h3>Model</h3>
資料表存放的地方。任何關於欄位的限制（如：不可重複等）都規定在此。延續上一週[我在做什麼]，我的Model應只有一個來存放App的資料，再用<a href="https://github.com/pluginaweek/state_machine">state-machine</a>來控制每筆App的狀態，以下為我的sample code：
{% codeblock model/app.rb %}
state_machine :initial => :waiting  do
	# 起初先宣告一開始的狀態為waiting，此外還有checked和deleted兩種狀態
	state :checked
	state :deleted
	# 再來說明每種狀態會經做什麼動作變成其他狀態
	event :delete do 
		transition [:waiting, :checked] => :deleted
	end
	# ...
end
{% endcodeblock %}

如此一來你可以執行該transition來更改你的狀態
{% codeblock %}
	app.delete!
{% endcodeblock %}

<h3>Controller</h3>
對資料表執行某些動作的地方。基本的動作像是新增、讀取、更改、刪除(CRUD)都會被定義於controller中。有種設計風格叫做RESTful，它幫助我們用一種比較標準化的方式來命名跟組織controllers和actions，應盡量使用以降低controller的負擔。如果有重複使用的action應使用善加利用繼承概念以便未來網站維護之用。
{% codeblock %}
rails g controller admin/apps
{% endcodeblock %}

在admin資料夾中新增一個base_controller.rb
{% codeblock base_controller.rb %}
class Admin::BaseController < ApplicationController
	before_filter :authenticate_user! # devise中的使用者驗證method
end
{% endcodeblock %}

然後再將admin/apps controller繼承base controller
{% codeblock %}
class Admin::AppsController < Admin::BaseController
{% endcodeblock %}
透過物件導向的繼承概念，可以將避免重複的程式撰寫，方便未來網站管理。

<h3>View</h3>
如果使用RESTful的設計風格，再設計表單時你可以直接設定method即可透過http完成對model的操作。
{% codeblock %}
<%= link_to 'delete', app_path(app), :method => :delete %>
{% endcodeblock %}

<h3>Devise</h3>
一個註冊、登出登錄、更改密碼等多功能使用者管理套件，它可以讓你安全的存取使用者資訊，完善的api讓功能們隨call隨到。

<h3>Workers</h3>
幫助你定時完成某項任務。本網站需要每日定時更新資料庫中的資料才可以確保排名是即時的，因此可使用<a href="https://github.com/yzalis/Crontab">crobtab</a>實現你的願望。若待處理事件需要queue來控管的話，可考慮使用<a href="https://github.com/defunkt/resque">resque</a>和<a href="https://github.com/mperham/sidekiq">sidekiq</a>

說的落落長卻少了成品，我會督促我自己在星期三前都摸摸看 <br/>
重點只是想要說：有規劃的專案就像是有目標的船隻，船長才知道駛往何方 <br/>

{% blockquote iCook創辦人-Lawrence %}
我們在開的船越來越大艘，有時候自己都覺得自己無力駕駛，很難想像有一天如果是開航空母艦，一次要跟上百個人合作的時候要怎麼辦？
從最簡化的狀況，就是需要充足的規劃，無論是一個人、兩個人或是十個人、數十個人的專案，應該都是如此。
{% endblockquote %}