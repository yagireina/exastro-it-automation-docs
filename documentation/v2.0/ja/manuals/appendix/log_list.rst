==============================
Exastro IT Automation ログ一覧
==============================

| Exastro IT Automationの各コンテナの出力メッセージに関するログについては以下の通りです。


.. list-table:: リストテーブルサンプル
   :widths: 10 10 20
   :header-rows: 1
   :align: left
   * - No
     - ログの種類
     - | ログの説明
       | (複数行)
   * - 1
     - | devcontainer-platform-api-1
     - | %(asctime)s %(levelname)s (%(userid)s) %(pathname)s (%(lineno)d) %(message)s
       | 
       | %(asctime)s ログ出力日時
       | %(levelname)s メッセージレベル
       | (%(userid)s) アクセスユーザー（Noneは指定なし）
       | %(pathname)s ログ出力元のソース
       | (%(lineno)d) ログ出力元の行
       | %(message)s メッセージ
   * - 2
     - devcontainer-platform-job-1
     - No.1（evcontainer-platform-api-1）と同じフォーマット 
   * - 3
     - devcontainer-platform-web-1
     - | LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined \
       | LogFormat "%h %l %u %t \"%r\" %>s %b" common \ 
       | <IfModule logio_module> \
       | # You need to enable mod_logio.c to use %I and %O \
       | LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %I %O" combinedio \
       | </IfModule>
       |
       | デフォルトのapacheログ形式となっており、commonでログ保存を指定した場合は以下の内容。
       | %h    アクセス元のホスト名
       | %l    クライアントの識別子
       | %u    認証ユーザー名
       | %t    リクエストを受け付けた時刻
       | \%r\  リクエストの最初の行の値
       | %>s   最後のレスポンスのステータス
       | %b    送信されたバイト数
       | 
       | combinedフォーマットは上記に加え以下が追加されている。
       | \%{Referer}i\     リファラー
       | \%{User-Agent}i\  User Agent
       |
       | combinedioフォーマットはさらに以下の項目が追加されている。
       |
       | %I  受け取ったバイト数
       | %O  送信したバイト数
   * - 4
     - | devcontainer-platform-auth-1
     - | 上記2つ（devcontainer-platform-api-1、devcontainer-platform-web-1）の
       | 混合ログが出力される。
   * - 5
     - | devcontainer-platform-db-1
     - | mariadbのログに準拠している。
       | （DBについては、使用するデータベースのログフォーマットとなる。）
       | 設定もデータベースによるが、デフォルトでmariadbを立ち上げた際は
       | エラーログが出力される。
   * - 6
     - | devcontainer-keycloak-1
     - | %d{yyyy-MM-dd HH:mm:ss,SSS} %-5p [%c] （%t） %s%e%n
       |
       | %d{yyyy-MM-dd HH:mm:ss,SSS}		ログ出力日時
       | %-5p	エラーレベル（DEBUG, INFO, WARN, ERROR）
       | %c		ログ カテゴリ名
       | %t		スレッド名
       | %s		簡単なメッセージ
       | %e		例外
       | %n		改行
   * - 7
     - | devcomtainer-ita-api-admin
     - | 日付　ログレベル ユーザID フリーエリア
   * - 8
     - | devcontainer-phpmyadmin-1
     - | 開発用のコンテナ
   * - 9
     - | devcontainer-ita-web-server-1
     - | No.3 同様、apacheのログが出力されている。
   * - 10
     - | ita-api-organization
     - | 日付 ログレベル フリーエリア
       | ERROR, INFO, DEBUGが基本的なログレベル
       | ERRORログは1000種類近くあり、その内容次第で対応を取る。
   * - 11
     - | devcontainer-ita-mariadb
     - | mariadbのログに準拠している。
       | 