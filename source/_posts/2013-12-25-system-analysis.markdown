---
layout: post
title: "System Analysis"
date: 2013-12-25 14:13
comments: true
categories: mmai
author: 張宇婷
---
{% img /images/2013-12-25-1413/sa.png %}
以上是我們的iGotIt系統架構圖

<!--More-->
<h3>Group Members</h3>
<p>張竣貿、張宗浩、張宇婷</p>

<h3>Project Title</h3>
<p>iGotIt – 商店招牌辨識系統</p>

<h3>Project Description</h3>
<p>常常走到某家店看起來很好吃的店門口都會猶豫要不要進去試試看，這時如果只要照張像，就可以找到相關評價一定可以幫助我們判斷他有沒有雷。因此我們決定實作行動裝置APP讓使用者可隨處拍攝照片，並透過手機端進行影像處理，將特徵點(features)傳遞到後台與資料庫中的資料進行比對，在回傳相關文件以利使用者辨知悉店家的評價。</p>

<h3>Related Work</h3>
<ul>
	<li><a href="http://www.cs.ucf.edu/courses/cap6411/cap6411/spring2006/Lecture11.pdf">Graph cut</a></li>
	<li><a href="http://www.cs.umd.edu/~djacobs/pubs_files/deformations_iccv.pdf">Deformation Invariant Image Matching</a></li>
	<li><a href="http://ieeexplore.ieee.org/xpl/login.jsp?reload=true&tp=&arnumber=5665875&url=http%3A%2F%2Fieeexplore.ieee.org%2Fxpls%2Fabs_all.jsp%3Farnumber%3D5665875">Le Festin: Shop sign recognition assisted food recommendation system</a></li>
</ul>

<h3>Possible Working Item</h3>
<p>目前我們從兩個方向著手進行：後台資料的處理與前台行動裝置APP的撰寫。</p>
<p>後台資料蒐集與處理部分，我們利用Java和OpenCV進行特徵點的萃取。OpenCV為影像處理的強大套件，我們將利用內建的Graph Cut Library找出影像的重點部位，再使用Color Histogram和Gabor Filter進行計算，並將處理解果輸出到線上資料庫(Parse)，以利使用者即時的比對。</p>
<p>行動裝置APP的開發，主要目的為讓使用者可以隨時隨地的拍攝照片，而拍攝玩的照片可以即時的使用OpenCV for mobile 進行特徵點的計算，將計算結果回傳至Parse以加速比對的效率。</p>
<p>系統使用流程圖如下所示：</p>
{% img /images/2013-12-25-1413/flow.png %}

<h3>Job Assignment</h3>
<table>
<tr><th>組員名稱</th><th>工作內容</th></tr>
<tr>
	<td>張竣貿</td>
	<td>
		蒐集資料	12/13<br />
		線上伺服器架設	12/30<br />
		利用OpenCV進行影像處理並萃取特徵點	1/3<br />
	</td>
</tr>
<tr>
	<td>張宗浩</td>
	<td>
		蒐集資料	12/13
		利用OpenCV進行影像處理並萃取特徵點	1/3
	</td>
</tr>
<tr>
	<td>張宇婷</td>
	<td>
		撰寫手機拍攝功能並萃取特徵點	12/30
		資料傳送到線上伺服器	1/3
	</td>
</tr>
</table>


