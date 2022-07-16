# rails

progate  
https://prog-8.com/rails5/study/1/1  

## Tweetクローン作製

### 環境構築（なし）

###

```console
# プロジェクト作成（app,config,db...）
rails new tweet_app

# サーバーを起動（localhost:3000へ）
rails server

# topページを作成（アクセス：localhost:3000/home/top）
rails generate controller home top
```

railsで必要なもの
- view
- controller
- routing

### 
app
- views
  - home/
    - top.html.erb
    - about.html.erb
- controllers
  - home_controller.rb
- config/
  - routes.rb
- assets/ # 画像、スタイルシート、JSのリソースフォルダ
  - images/
  - javascripts/ 
  - stylesheets/
    - home.scss # rails generate controller home..でファイルが生成


public
- top.jpg
- tweets.png

### controller
```ruby:home_controller.rb
class HomeController < ApplicationController
  def top
  end
  
  # aboutアクションを追加してください
  def about
  end
end
```

### routing（routing -> controller -> controller）

|URL|controller|action|
|---|---|---|
|home/top|home|top|
|etc|etc|etc|

```ruby:routes.rb
Rails.application.routes.draw do
  // get <URL> => <controller#action>
  get "home/top" => "home#top"
end
```

### リンクの作成
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
```

