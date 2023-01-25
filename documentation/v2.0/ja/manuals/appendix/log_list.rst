==============================
Exastro IT Automation ログ一覧
==============================


| Exastro IT Automationの各コンテナの出力メッセージに関するログについて。
| コンテナごとにログの例と文字列の意味を以下に記載します。

.. code-block::

    %(asctime)s %(levelname)s (%(userid)s) %(pathname)s(%(lineno)d) %(message)s
    例：2023/01/11 11:27:05.976995 INFO (None) /app/platform_init.py(88) platform initialize setting start

.. list-table:: platform-job
   :widths: 10 15 15 20
   :header-rows: 1
   :align: left

   * -  フォーマット文字列
     -  フォーマットの意味
     -  ログの例
     -  備考
   * -  %(asctime)s
     -  ログ出力日時
     -  2023/01/11 11:27:05.976995
     -    
   * -  %(levelname)s
     -  メッセージレベル
     -  INFO
     -  DEBUG, INFO, WARNING, ERROR, CRITICAL が出力される。
   * -  (%(userid)s)
     -  アクセスユーザー（Noneは指定なし）
     -  （None）
     -    
   * -  %(pathname)s
     -  ログ出力元のソース
     -  /app/platform_init.py
     -    
   * -  (%(lineno)d)
     -  ログ出力元の行
     -  \(88\)
     -   
   * -  %(message)s
     -  メッセージ
     -  platform initialize setting start
     -  

.. list-table:: platform-api
   :widths: 10 10 20 20
   :header-rows: 1
   :align: left

   * - | フォーマット文字列
     - | フォーマットの意味
     - | ログの例
     - | 備考
   * - | %(asctime)s
     - | ログ出力日時
     - | 2023/01/11 11:27:05.976995
     - |
   * - | %(levelname)s
     - | メッセージレベル
     - | INFO
     - | DEBUG, INFO, WARNING, ERROR, CRITICAL が出力される。
   * - | (%(userid)s)
     - | アクセスユーザー（Noneは指定なし）
     - | （None）
     - |
   * - | %(pathname)s
     - | ログ出力元のソース
     - | /app/platform_init.py
     - |
   * - | (%(lineno)d)
     - | ログ出力元の行
     - | (88)
     - |
   * - | %(message)s
     - | メッセージ
     - | platform initialize setting start
     - |

