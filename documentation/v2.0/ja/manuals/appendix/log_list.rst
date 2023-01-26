==============================
Exastro IT Automation ログ一覧
==============================


| Exastro IT Automationの各コンテナの出力メッセージに関するログについて。
| コンテナごとにログの例と文字列の意味を以下に記載します。


platform-job
============

.. code-block:: 

    %(asctime)s %(levelname)s (%(userid)s) %(pathname)s(%(lineno)d) %(message)s
    例：2023/01/11 11:27:05.976995 INFO (None) /app/platform_init.py(88) platform initialize setting start

.. list-table:: 
   :widths: 10 15 15 20
   :header-rows: 1
   :align: left

   * -  フォーマット文字列
     -  フォーマットの意味
     -  ログの例
     -  備考
   * -  %\(asctime\)s
     -  ログ出力日時
     -  2023/01/11 11:27:05.976995
     -    
   * -  %\(levelname\)s
     -  メッセージレベル
     -  INFO
     -  DEBUG, INFO, WARNING, ERROR, CRITICAL が出力される。
   * -  \(%\(userid\)s\)
     -  アクセスユーザー（Noneは指定なし）
     -  （None）
     -    
   * -  %\(pathname\)s
     -  ログ出力元のソース
     -  /app/platform_init.py
     -    
   * -  \(%\(lineno\)d\)
     -  ログ出力元の行
     -  \(88\)
     -   
   * -  %\(message\)s
     -  メッセージ
     -  platform initialize setting start
     -  


platform-api
============

.. code-block:: 

    %(asctime)s %(levelname)s (%(userid)s) %(pathname)s(%(lineno)d) %(message)s
    例：2023/01/06 10:15:47.537174 INFO (2d6aabce-04c7-4938-a616-fa283cd6693) /app/common_library/common/api_keycloak_roles.py(372) Get keycloak user list for each role. realm_name=org3, client_id=743c50ae-7656-40d2-9ac1-b6cc6e39d15c, role_name=_workspace-1-admin

.. list-table:: 
   :widths: 10 15 15 20
   :header-rows: 1
   :align: left

   * - | フォーマット文字列
     - | フォーマットの意味
     - | ログの例
     - | 備考
   * - | %\(asctime\)s
     - | ログ出力日時
     - | 2023/01/06 10:15:47.537174
     - |
   * - | %\(levelname\)s
     - | メッセージレベル
     - | INFO
     - | DEBUG, INFO, WARNING, ERROR, CRITICAL が出力される。
   * - | \(%\(userid\)s\)
     - | アクセスユーザー（Noneは指定なし）
     - | \(2d6aabce-04c7-4938-a616-fa283cd6693\)
     - |
   * - | %\(pathname\)s
     - | ログ出力元のソース
     - | /app/common_library/common/api_keycloak_roles.py
     - |
   * - | \(%\(lineno\)d\)
     - | ログ出力元の行
     - | \(372\)
     - |
   * - | %\(message\)s
     - | メッセージ
     - | platform initialize setting start
     - |

platform-web
============


.. code-block::

    LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined \
    LogFormat "%h %l %u %t \"%r\" %>s %b" common \ 
    <IfModule logio_module> \
      # You need to enable mod_logio.c to use %I and %O \
      LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %I %O" combinedio \
    </IfModule>

.. list-table:: commonでログ保存を指定した場合
   :widths: 10 15 15 20
   :header-rows: 1
   :align: left

   * - | フォーマット文字列
     - | フォーマットの意味
     - | ログの例
     - | 備考
   * - | %h
     - | アクセス元のホスト名
     - | クライアントの識別子
     - | 認証ユーザ名
     - |
   * - | %l
     - | クライアントの識別子
     - | 
     - |
   * - | &u
     - | 認証ユーザ名
     - |
     - |
   * - | %t
     - | リクエストを受け付けた時刻
     - |
     - |
   * - | \%r\
     - | リクエストの最初の行
     - |
     - |
   * - |%>s
     - | 最後のレスポンスのステータス
     - |
     - |
   * - | %b
     - | 送信されたバイト数
     - |
     - |
  
.. list-table:: combinedフォーマットでログ保存を指定した場合
   :widths: 10 15 15 20
   :header-rows: 1
   :align: left

   * - | フォーマット文字列
     - | フォーマットの意味
     - | ログの例
     - | 備考
   * - | \%{Referer}i\
     - | リファラー
     - |
     - |
   * - | \%{User-Agent}i\
     - | User Agent
     - |
     - |


.. list-table:: combinedioフォーマットでログ保存を指定した場合
   :widths: 10 15 15 20
   :header-rows: 1
   :align: left

   * - | フォーマット文字列
     - | フォーマットの意味
     - | ログの例
     - | 備考
   * - | &I
     - | 受け取ったバイト数
     - |
     - |
   * - | %O
     - | 送信したバイト
     - |
     - |