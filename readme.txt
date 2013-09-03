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


