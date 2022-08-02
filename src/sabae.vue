<template>
  <!DOCTYPE html>
  <html lang="ja">
  <head>
    <meta charset="UTF-8">
    <title>sparql</title>
    <script type="text/javascript" src="http://code.jquery.com/jquery-2.0.3.min.js"></script>
    <script type="text/javascript">
  </head>

  <body>
    <div id="disp"></div>
    <p>このアプリケーションは、以下の著作物を改変して利用しています。<br>
鯖江市、さばかん、クリエイティブ・コモンズ・ライセンス 表示 2.1 日本（http://creativecommons.org/licenses/by/2.1/jp/）、オープンデータ・アプリコンテスト利用規約（http://www.opendata.gr.jp/2013contest/terms/index.html#rules）</p>

  </body>
  </html>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}

// GETリクエストを送信
	$.get(
		"https://jpsearch.go.jp/rdf/sparql/",	// エンドポイント
		{query:`
      PREFIX schema: <http://schema.org/> 
			SELECT ?desc ?img 
			WHERE { 
			GRAPH ?g { 
				?id schema:description ?desc.
				?id schema:image ?img.
			}
			} limit 20
		`},	// クエリ(説明文と画像を最大20件まで要求)
		success,	// 返ってきたデータを処理する関数
		"json"	// 返ってきてほしいデータの形式
	);

	// getリクエストで得たdataを処理する
	function success(data) {
		var head = data.head.vars;
    var results = data.results.bindings;
    var html = "<table>";

    for(var i=0; i<results.length; i++) {
      html += "<tr><td>";
      html += results[i].desc.value;
      html += "</td><td>";
      html += "<img src=\""+results[i].img.value+"\"></img>";
      html += "</td></tr>";
    }
    html += "</table>";
    $("#disp").html(html);
	}

	</script>
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
