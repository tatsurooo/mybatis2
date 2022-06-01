# やったこと
## dockerセットアップ
1. vagrant、virtualBoxのインストール（仮想マシンを構築してMySQLを立ち上げる）
2. git bashを立ち上げる（以下、git bash上での動作）
3. $cd docker-ce-vagrant
4. $vagrant up（vagrantの起動）
5. $vagrant ssh（ssh経由でvagrantの仮想マシンに接続）
6. $sudo snap install docker（snapでdockerのインストール）
7. $sudo docker version（dockerのバージョン確認）
8. $sudo chmod 666 /var/run/docker.sock（「sudo」なしで操作ができる）
9. $docker version（「sudo」なしで、バージョン確認が出力された）

## MySQLサーバのdockerコンテナを起動
1. $docker run -e MYSQL_ROOT_PASSWORD=password mysql
     - docker run…dockerコンテナという仮想サーバを起動
     - mysql…立ち上げるコンテナの種類
     - -e MYSQL_ROOT_PASSWORD=password…環境変数の設定でMySQL の root ユーザのパスワードを指定
2. docker ps（コンテナIDを調べる）
3. docker exec -it [container ID] bash　（コンテナの中に入る）
4. root@[container ID]:/# mysql -uroot -p（user:root のパスワードを設定する）
5. Enter password:password（パスワードを「password」に設定）
## MySQLにてデータベースの作成
1. mysql> show databases; (データベース一覧が表示される)
2. mysql> create database gamelist;（gamelistのデータベースを作成）
3. mysql> use gamelist;（gamelistの中に入る）
4. mysql> create table test_users(id int auto_increment primary key, name varchar(20), price int);（テーブルtest_usersに入れる情報の設定）
5. mysql> insert into test_users(name,price) values('super mario', '1500');（情報の作成）
6. 6同様にデータをいくつか作成
7. mysql> select * from test_users;（test_usersから全ての情報を選んで出力させる）
8. ![image](https://user-images.githubusercontent.com/97898586/171424506-4a5d7cb5-01f1-4106-ad1f-1d0cfd7df90f.png)
9. mysql> commit（コミットする）
## spring bootの立ち上げ
1. spring inializrで事前準備
    - gradle（プログラムをビルドするツール）
    - java
    - spring web,mysql driver,mybatisを選択し、ダウンロード
2. eclipseで1.をインストールし、小山さんの講義内容を真似てプログラムを書いた
3. 実行できず





* 原因
docker mysqlが接続できていない
* 対処法のヒントをご教示ください。

なお、docker ps -a でステータスを見ると以下のとおりです。
![image](https://user-images.githubusercontent.com/97898586/171432875-75886594-d52b-488f-9ead-de70c2c9f20e.png)
- 最新のコンテナIDだけportsがないことに今気づきました。-

また、ホストのIPアドレスを調べた結果、以下のとおりの表示が出力された。
![image](https://user-images.githubusercontent.com/97898586/171432365-29e92749-6364-4c14-b0d4-3d2ea2dd949e.png)
