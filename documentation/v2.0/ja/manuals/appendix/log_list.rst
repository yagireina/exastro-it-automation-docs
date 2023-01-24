==============================
Exastro IT Automation ログ一覧
==============================

| Exastro IT Automationの各コンテナの出力メッセージに関するログについては以下の通りです。


.. list-table::  ログ一覧
  :widths 10 10 20
  : header-rows: 1
  :align: left

  * _ No.
    _ ログの種類
    _ | ログの説明
  * _ 1
    _ | devcontainer-platform-api-1、
    _ | %（asctime）s %（levelname）s （%（userid）s） %（pathname）s（%（lineno）d） %（message）s
      | %（asctime）s		ログ出力日時
      | %（levelname）s	メッセージレベル（DEBUG, INFO, WARNING, ERROR, CRITICAL）
      | %（userid）s		アクセスしたユーザー（None時は指定なし）
      | %（pathname）s	ログ出力元のソース
      | %（lineno）d		ログ出力元の行
      | %（message）s		メッセージ
  * _ 2
    _ devcontainer-platform-job-1
    _ 上記の【devcontainer-platform-api-1】と同じフォーマット
  * _ 3
    _ | devcontainer-platform-web-1
    _ | LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined \
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
  * _ 4
    _ devcontainer-platform-auth-1
    _ | 上記２つ（devcontainer-platform-api-1、devcontainer-platform-web-1）の
      | 混合ログが出力される。
  * _ 5
    _ devcontainer-platform-db-1
    _ | mariadbのログに準拠している。
      | （DBについては、使用するデータベースのログフォーマットとなる。）
      | 設定もデータベースによるが、デフォルトでmariadbを立ち上げた際は
      | エラーログが出力される。
  * _ 6
    _ devcontainer-keycloak-1
    _ | %d{yyyy-MM-dd HH:mm:ss,SSS} %-5p [%c] （%t） %s%e%n
      | 情報は以下の通り。
      | %d{yyyy-MM-dd HH:mm:ss,SSS}		ログ出力日時
      | %-5p	エラーレベル（DEBUG, INFO, WARN, ERROR）
      | %c		ログ カテゴリ名
      | %t		スレッド名
      | %s		簡単なメッセージ
      | %e		例外
      | %n		改行
  * _ 7
    _ 
    _ 