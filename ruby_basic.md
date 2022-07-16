言語バージョン: Ruby 2.4.4

## Ruby I
-  1 章：Rubyを動かしてみよう
-  2 章：変数を使ってみよう
-  3 章：条件分岐をしてみよう
-  4 章：課題にチャレンジしよう

```ruby:hello world
puts "Hello World"
```

変数：型宣言なし
```ruby
name = "name"
puts name
```

```ruby:
length = 9
width = 8
area = length * width
# 「面積は◯◯です」となるように出力してください
puts "面積は#{area}です"
```

if
```ruby
if score > 80
  puts "よくできました
end
```

真偽値表示
```ruby
score = 80

# 「score > 80」を出力してください
puts score > 80

# 「score <= 80」を出力してください
puts score <= 80


# scoreの値が80以下の場合に、「がんばりましょう」と出力してください
if score <= 80
  puts "がんばりましょう"
end
```

elsif文
```ruby
score = 73

# scoreの値が60より大きい場合に「まずまずです」と出力されるように書き換えてください
if score > 80
  puts "よくできました"
elsif score > 60
  puts "まずまずです"
else
  puts "がんばりましょう"
end
```

## Ruby II
-  1 章：配列と繰り返し
-  2 章：ハッシュとシンボル
-  3 章：nilと様々な配列
-  4 章：課題にチャレンジしよう

配列
```ruby
# 変数languagesに、複数の文字列を要素に持つ配列を代入してください
languages = ["日本語","英語","スペイン語"]

# 全て表示
puts languages
```

配列表示
```ruby
languages = ["日本語", "英語", "スペイン語"]

# each文を用いて、要素ごとに「○○を話せます」と出力してください
# 配列名.each do |変数名|
# end
languages.each do |lan|
  puts lan + "を話せます"
end
```

### ハッシュとは
- 複数の値をまとめて管理する方法としては、配列の他にもハッシュというものがあります。
- 配列は複数の値を並べて管理するのに対して、ハッシュはそれぞれの値にキーと呼ばれる名前をつけて管理します。
- ハッシュは、{キー1 => 値1, キー2 => 値2}のようにつくります。
-  ーと値の間は「=>」でつなぎます。
-  また、配列と同様に、要素と要素はコンマ（,）で区切ります。


```ruby
# 配列
[値１，値２]

# ハッシュ
ハッシュ名 = {キー1 => 値1,キー2 => 値2}
```

```ruby:ハッシュに対する操作
exam = {"subject" => "Math", "score" => 80}

# キー「"subject"」の値を出力してください
puts exam["subject"]

# キー「"subject"」の値を「"Science"」に更新してください
exam["subject"] = "Science"

# もう一度、キー「"subject"」の値を出力してください
puts exam["subject"]

# キーが「"grade"」、値が「"good"」の要素を追加してください
exam["grade"] = "good"

# キー「"grade"」の値を出力してください
puts exam["grade"]
```

### シンボル
- キーの部分を文字列ではなく、先頭にコロン「:」を付けた書き方をすることもできます。
- 「:name」という書き方のことをシンボルと言います。
- シンボルとは、文字を「"」や「'」で囲む代わりに、先頭に「:」をつけた書き方のことをいいます。
- ハッシュのキーにシンボルを用いるときには、省略した書き方をすることができます。具体的には「:key =>」を「key:」というように省略することができます。

```ruby:シンボルの例
# 省略した書き方で書き換えてください
exam = {subject:"Math", score:80}
puts "#{exam[:subject]}: #{exam[:score]}点"
```

### nil
- 「何もない」という値
- ifの条件に真偽値以外を用いたとき、それがnilであればfalseとして扱われ、それ以外はtrueとして扱われます。

### 配列の要素にハッシュを入れる
```ruby
exams = [
  {subject: "Math", score: 80},
  {subject: "Science", score: 55}
]

# インデックス番号が1の要素の、キーが「:score」の値を出力してください
puts exams[1][:score]
```

###
```ruby:
exams = [
  {subject: "Math", score: 80},
  {subject: "Science", score: 55}
]

# each文を用いて、要素ごとに「○○の結果は△△点です」と出力してください
exams.each do |exam|
  puts "#{exam[:subject]}の結果は#{exam[:score]}点です"
end
```


### ハッシュと条件にnil
```ruby
characters = [
  {name: "にんじゃわんこ", age: 14},
  {name: "ひつじ仙人"},
  {name: "ベイビーわんこ", age: 5},
  {name: "とりずきん"}
]

characters.each do |character|
  puts "--------------------"
  puts "名前は#{character[:name]}です"
  
  # キー:ageの値に応じて年齢の情報を出力してください
  if character[:age]
    puts "年齢は#{character[:age]}歳です"
  else
    puts "年齢は秘密です"
  end
end

```

## Ruby III
-  1 章：メソッドを学ぼう
-  2 章：引数
-  3 章：戻り値
-  4 章：キーワード引数

メソッド＋引数
```ruby
def introduce(name)
  puts "こんにちは"
  puts "私は#{name}です"
end

# 引数を渡してメソッドを呼び出してください
introduce("宮脇")
```

### 真偽値を返すメソッドは、メソッド名の末尾に「?」をつける慣習がある


### キーワード引数を持つメソッド
- 通常のメソッドの書き方に加えて、
- 定義側で、引数の後にコロンを付ける
- 呼び出し側で、値の前に引数名を書く

```ruby
# キーワード引数を使うように書き換えてください
def buy(item:, price:, count:)
	puts "#{item}を#{count}台のお買い上げです"
	puts "合計金額は#{price * count}円です"
end

# キーワード引数を使うように書き換えてください
buy(item:"テレビ", price:15000, count:2)
```

## Ruby IV
- 1 章：クラスとインスタンス
- 2 章：インスタンスメソッド
- 3 章：「料理注文システム」を作ろう

### クラスの定義

### attr_accessor
- クラスのデータを定義する方法の1つに「attr_accessor シンボル」を使う方法があります。
- クラス（設計図）を元に、新しくインスタンスを生成するには、「クラス名.new」とします。
- 「インスタンス.変数名 = 値」とすることで、そのインスタンス変数に値をセットすることができます。

```ruby
class Menu
  attr_accessor :name //インスタンス変数
end

menu1 = Menu.new
menu1.name = "すし"
puts menu1.name
```

### インスタンスメソッドの中でインスタンス変数を扱う
- インスタンスメソッドの中では、特殊な変数「self」を用いて「self.変数名」とすることで、インスタンス変数を扱うことができるようになります。
- インスタンスメソッドでは、変数「self」に、呼び出したインスタンス自身が代入されています。

```ruby:selfの例
class Menu
  attr_accessor :name
  attr_accessor :price
  
  def info
    # 「#{}」の中身を埋めてください
    return "#{self.name} #{self.price}円"
  end
end

menu1 = Menu.new
menu1.name = "ピザ"
menu1.price = 800

puts menu1.info
```

```ruby
class Menu
  attr_accessor :name
  attr_accessor :price
  
  def info
    return "#{self.name} #{self.price}円"
  end
  
  # get_total_priceメソッドを定義してください
  def get_total_price(count)
    total_price = self.price * count
    if count >= 3
      return total_price - 100
    end
    return total_price
  end
  
end

menu1 = Menu.new
menu1.name = "ピザ"
menu1.price = 800

# menu1に対してget_total_priceメソッドを呼び出してください
puts menu1.get_total_price(3)
```

### initialize
- インスタンスが生成された直後にinitializeメソッドが呼び出され、その中の処理が実行されます。

```ruby
class Menu
  attr_accessor :name
  attr_accessor :price
  
  # initializeメソッドを書き換えてください
  def initialize(name:,price:)
    self.name = name
    self.price = price
  end
  
  def info
    return "#{self.name} #{self.price}円"
  end
  
  def get_total_price(count)
    total_price = self.price * count
    if count >= 3
      total_price -= 100
    end
    return total_price
  end
end

# 引数を渡してインスタンスを生成してください
menu1 = Menu.new(name:"すし",price:1000)

puts menu1.info
```
### require
```ruby
require "./menu"
```

```ruby:index
require "./menu"

menu1 = Menu.new(name: "ピザ", price: 800)
menu2 = Menu.new(name: "すし", price: 1000)
menu3 = Menu.new(name: "コーラ", price: 300)
menu4 = Menu.new(name: "お茶", price: 200)

menus = [menu1, menu2, menu3, menu4]

# 変数indexを定義して「0」を代入してください
index = 0

menus.each do |menu|
  # 番号をつけてメニューの内容が出力されるように書き換えてください
  puts "#{index}." + menu.info
  
  # 変数indexに1を加えて値を更新してください
  index += 1
end
```

### 入力を受け取る
`gets.chomp`
- このコードが実行されると、コンソールが入力待機状態になります。
「変数 = gets.chomp」とすることで、エンターキーを押されるまでに入力された値を変数に代入することができます。

`gets.chomp.to_i`で入力した値を数値に変更する

```ruby:index.rb
require "./menu"

menu1 = Menu.new(name: "ピザ", price: 800)
menu2 = Menu.new(name: "すし", price: 1000)
menu3 = Menu.new(name: "コーラ", price: 300)
menu4 = Menu.new(name: "お茶", price: 200)

menus = [menu1, menu2, menu3, menu4]

index = 0
menus.each do |menu|
  puts "#{index}. #{menu.info}"
  index += 1
end

puts "--------------"
puts "メニューの番号を選択してください"

# 入力を数値として受け取って変数orderに代入してください
order = gets.chomp.to_i

# 選択されたメニューのインスタンスを変数selected_menuに代入してください
selected_menu = menus[order]

# 「選択されたメニュー: ○○」となるように出力してください
puts "選択されたメニュー：#{selected_menu.name}"

puts "個数を入力してください(3つ以上で100円割引)"

# 入力を数値として受け取って変数countに代入してください
count = gets.chomp.to_i

# 「お会計は○○円です」となるように出力してください
puts "お会計は#{selected_menu.get_total_price(count)}円です"
```
```ruby:menu.rb
class Menu
  attr_accessor :name
  attr_accessor :price
  
  def initialize(name:, price:)
    self.name = name
    self.price = price
  end
  
  def info
    return "#{self.name} #{self.price}円"
  end
  
  def get_total_price(count)
    total_price = self.price * count
    if count >= 3
      total_price -= 100
    end
    return total_price
  end
end

```


