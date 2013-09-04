http://railstutorial.jp/chapters/a-demo-app.html#top

2章 デモアプリの作成

2.1 アプリの計画
$ cd rails_projects
$ rails new demo_app
$ cd demo_app
にてdemoアプリ作成

Gemfileを更新して、環境をインストール

$ bundle update
$ bundle install --without production


2.2 Users リソース
Usersリソース(データモデルとWebインターフェイス)を、
Railsプロジェクトに標準装備されているscaffoldジェネレータで生成します。

scaffoldコマンドの引数には、リソース名を単数形にしたもの (この場合はUser) を
使用し、必要に応じてデータモデルの属性をオプションとしてパラメータに追加します

$ rails generate scaffold User name:string email:string

# idパラメータはRailsによって自動的に主キーとして
# データベースに追加されるため、追加不要


データベースを作成したら、RakeコマンドでMakeを行う

$ bundle exec rake db:migrate

# データベースを更新し、usersデータモデルを作成する
# 現在のGemfileに対応するバージョンのRakeが確実に実行されるようにするために、
# rakeを実行するときにbundle execを使用している


ローカルWebサーバを起動する
$ rails s

 http://localhost:3000/

http://localhost:3000/users 等と指定することでページが閲覧できる

URI			アクション	備考
/users		index	すべてのユーザーを一覧するページ
/users/1	show	id=1のユーザーを表示するページ
/users/new	new		新規ユーザーを作成するページ
/users/1/edit	edit	id=1のユーザーを編集するページ

2.2.2 MVCの挙動

2.3Mircroposts リソース
Usersと同様にMicropostのリソースも作成する

$ rails generate scaffold Micropost content:string user_id:integer

新しいデータモデルでデータベースを更新(Makeを行う)
$ bundle exec rake db:migrate

$ rails s でServer起動

http://localhost:3000/microposts　で閲覧可能

micropost.rb(Model)に以下の行を追加して、
文字制限を行った。
#  validates :content, :length => { :maximum => 10 }

2.3.3ユーザーとマイクロポストをhas_manyで関連づける

