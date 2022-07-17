
https://prog-8.com/courses/rails5

# Ruby_on_Rails5

## Ruby on Rails5 I

Ruby on Railsを始めよう
- Ruby on Railsを始めよう
- Railsの基礎を学ぼう

Railsアプリケーションの開発を始めよう
- トップページを作ってみよう
- ビューを理解しよう
- コントローラを理解しよう
- ルーティングを理解しよう
- ルーティングを変えてみよう
- サービス紹介ページを追加しよう

目標物を完成させよう
- レイアウトを整えよう
- 画像を表示してみよう
- トップページのURLを変更しよう
- リンクを作ろう

### Railsアプリケーションの
準備をしよう

アプリケーション名：tweet_app
```ruby:
//プロジェクト作成
rails new tweet_app

//サーバー起動
rails server

//トップページを自動生成してみよう
//アドレス：localhost:3000/home/top
rails generate controller home top


//view

//controller

//routing
//ブラウザとコントローラを繋ぐ役割を担うのがルーティング
```

ルーティング（対応表）
|URL|コントローラ|アクション|
|---|---|---|
|home/top|home|top|
||||

```ruby:routes.rb
Rails.application.routes.draw do
  //get "URL" => "コントローラー名#アクション名"
  // アドレス localhost:3000/home/top
  get "home/top" => "home#top"
  
  // アドレス localhost:3000/top
  //  get "top" => "home#top"
  
  get "about" => "home#about"
end
```

```ruby:home_controller.rb
class HomeController < ApricationController
  //controllerのactionと対応
  def top
  end
  
  //
  def about
  end
end
```

### 画像の保存場所
ビューファイル
```ruby
//about.html.erb
//必ず"/"（スラッシュ）をつける
<img src="/tweets.png">

//
background-image: url("/top.jpg");
```


app
- views/
  - home/
    - top.html.erb（上記コマンドで自動作成）
    - about.html.erb（手動で新規作成）
- controllers/
  - home_controller.rb
- config/
  - routes.rb//ルーティングの設定ファイル
- assets
  - images/
  - javascripts/
  - stylesheets/
    - home.scss
 tweet_app/
  - public/
    - top.jpg
    - tweets.png


```ruby:top.html.erb
<header>
  <div class="header-logo">
    <!--トップページへのリンクにしてください-->
    <a href="/">TweetApp</a>
    TweetApp
  </div>
  <ul class="header-menus">
    <li>
      <!--サービス紹介ページへのリンクにしてください-->
      <a href="/about">TweetAppとは</a>
      TweetAppとは
    </li>
  </ul>
</header>

<div class="main top-main">
  <div class="top-message">
    <h2>つぶやきで、世界はつながる</h2>
    <p>今の気持ちをつぶやいてみよう！</p>
  </div>
</div>
```

```ruby:about.html.erb
<header>
  <div class="header-logo">
    <!--トップページへのリンクにしてください-->
    <a href="/">TweetApp</a>
    TweetApp
  </div>
  <ul class="header-menus">
    <li>
      <!--サービス紹介ページへのリンクにしてください-->
      <a href="/about">TweetAppとは</a>
      TweetAppとは
    </li>
  </ul>
</header>
<div class="about-main">
  <h2>TweetAppとは</h2>
  <p>
    SNSサービスです。
    近況やつぶやきを投稿し、他のユーザーと楽しくコミュニケーションできます。
  </p>
  <img class="about-img" src="/tweets.png">
</div>
```

```ruby:routes.rb
Rails.application.routes.draw do
  get "/" => "home#top"
  get "about" => "home#about"
end
```

```ruby:home.scss
/* reset ================================ */
* {
  box-sizing: border-box;
}

html {
  font: 100%/1.5 'Avenir Next', 'Hiragino Sans', sans-serif;
  line-height: 1.7;
  letter-spacing: 1px;
}

ul, li {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

a {
  text-decoration: none;
  color: #2d3133;
  font-size: 14px;
}

h1, h2, h3, h4, h5, h6, p {
  margin: 0;
}

input {
  background-color: transparent;
  outline-width: 0;
}

form input[type="submit"] {
  border: none;
  cursor: pointer;
}

/* 共通レイアウト ================================ */
body {
  color: #2d3133;
  background-color: #3ecdc6;
  margin: 0;
  min-height: 1vh;
}

.main {
  position: absolute;
  top: 64px;
  width: 100%;
  height: auto;
  min-height: 100%;
  background-color: #f5f8fa;
}

.container {
  max-width: 600px;
  margin: 60px auto;
  padding-left: 15px;
  padding-right: 15px;
  clear: both;
}

/* ヘッダー ================================ */
header {
  height: 64px;
  position: absolute;
  z-index: 1;
  width: 100%;
}

.header-logo {
  float: left;
  padding-left: 20px;
  color: white;
  font-size: 22px;
  line-height: 64px;
}

.header-logo a{
  color: white;
  font-size: 22px;
}

.header-menus {
  float: right;
  padding-right: 20px;
}

.header-menus li {
  float: left;
  line-height: 64px;
  font-size: 13px;
  color: white;
  padding-left: 15px;
}

.header-menus a {
  float: left;
  font-size: 13px;
  color: white;
}

.header-menus .fa {
  padding-right: 5px;
}

.header-menus input[type="submit"] {
  padding: 0 20px;
  float: left;
  line-height: 64px;
  color: white;
  margin: 0;
  font-size: 13px;
}

/* top ================================ */
.top-main {
  padding: 200px 0 100px;
  text-align: center;
  position: absolute;
  top: 0;
  width: 100%;
  height: auto;
  min-height: 100%;
  color: white;
  background-color: #3ecdc6;
  background-repeat: no-repeat;
  background-position: center 50%;
  background-size: cover;
  background-image: url("/top.jpg");
}

.top-message {
  position: relative;
}

.top-main h2 {
  font-size: 70px;
  font-weight: 500;
  line-height: 1.3;
  -webkit-font-smoothing: antialiased;
  margin-bottom: 20px;
}

.top-main p {
  font-size: 24px;
}

/* about ================================ */
.about-main {
  padding: 180px 8% 0;
  color: white;
}

.about-main h2 {
  font-size: 64px;
  font-weight: 500;
  line-height: 1.4;
}

.about-main p {
  font-weight: 200;
  font-size: 20px;
}

.about-img {
  width: 84%;
}

/* フォーム================================ */
.form {
  max-width: 600px;
  margin: 0 auto;
  background-color: white;
  box-shadow: 0 2px 6px #c1ced7;
}

.form-heading {
  font-weight: 300;
  margin: 60px 0 20px;
  font-size: 48px;
  color: #bcc8d4;
}

.form-body {
  padding: 30px;
}

.form-error {
  color: #ff4d75;
}

.form input {
  width: 100%;
  border: 1px solid #d8dadf;
  padding: 10px;
  color: #57575f;
  font-size: 16px;
  letter-spacing: 2px;
  border-radius: 2px;
}

.form textarea {
  width: 100%;
  min-height: 110px;
  font-size: 16px;
  letter-spacing: 2px;
}

.form input[type="submit"] {
  background-color: #3ecdc6;
  color: white;
  cursor: pointer;
  font-weight: 300;
  width: 120px;
  border-radius: 2px;
  margin-top: 8px;
  margin-bottom: 0;
  float: right;
}

.form-body:after {
  content: '';
  display: table;
  clear: both;
}

/* フラッシュ ================================ */
.flash {
  padding: 10px 0;
  color: white;
  background: rgb(251, 170, 88);
  text-align: center;
  position: absolute;
  top: 64px;
  z-index: 10;
  width: 100%;
  border-radius: 0 0 2px 2px;
  font-size: 14px;
}

```
