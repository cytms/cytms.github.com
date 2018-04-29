---
layout: post
title: "elasticsearch 101"
date: 2014-05-19 23:26
comments: true
categories: AWS
---

如果有安裝 Homebrew 的話直接 `brew installation` 就可以完成 es 的安裝。

<!-- More -->
#### 首先，先跟大家簡介一下 es 的基本功能及資料
{% codeblock %}
# 設定檔位置，可在該資料夾編輯 yml 檔
/usr/local/Cellar/elasticsearch/0.90.2/config

# 打開es引擎並指定 elasticsearch.yml 為 mapping 和 setting 的依據
elasticsearch -f -D config/elasticsearch.yml

# 刪掉叫做 recepes 的 index
curl -XDELETE 'http://localhost:9200/recipes/' 
{% endcodeblock %}

若要把它嵌在 rails 中，則可使用 [Tire](https://github.com/karmi/tire) 作為輔助工具。在 rails application 底下可以直接下 `rake environment tire:import CLASS='Recipe' FORCE=true` 即可建立該 class 的 index。

因為每次建 index 都會花費一小段時間，若單純想要測試可不可以 work 的話可以在 console 內執行 `Recipe.index.import Recipe.first(200)` 就可以僅建前幾筆的 index 即可。

#### 如果你要安裝 plugins
放置 plugin 的資料夾為 `/usr/local/var/lib/elasticsearch/plugins/`
{% codeblock %}
# 進到 elasticsearch 的資料夾中進行安裝
bin/plugin -install elasticsearch/elasticsearch-analysis-xxx/1.x.x
mvn clean package

# 在 target 中會產生出 SNAPSHOT.jar 檔，將該檔案複製到 plugin 的資料夾中即可
cp target/elasticsearch-analysis-xxx-1.x.x-SNAPSHOT.jar
 ../plugins/analysis-xxx/elasticsearch-analysis-xxx-1.x.x.jar

{% endcodeblock %}