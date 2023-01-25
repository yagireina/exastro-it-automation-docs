======
プラン
======

はじめに
========

| 本章では、Exastro Suite における プラン設定 について説明します。
| プランの設定はPlatform管理者のみ可能です（オーガナイゼーションユーザーからはアクセス出来ません）。


プランとは
==========

| Exastro IT Automation の機能を利用するためには、必ずワークスペースの作成が必要となり、ワークスペース数をプラン設定で指定する必要があります。
|
| ※ ワークスペースについては :doc:`../../manuals/organization_management/workspace` を参照ください。
| 
| {{#1 想像で書いているところが多い部分です。プランとは何であるかご教示いただきたいです。}}


運用とシステムの動きについて
----------------------------

-  例 １月まで「最大ワークスペース数＝５のプラン」、２月から「最大ワークスペース数＝３のプラン」に変更

.. figure:: /images/ja/diagram_chart/manuals/operation_and_system_movement_num.png
    :alt: 運用とシステムの動き



#. ユーザーから「最大ワークスペース数＝３」へのプラン変更申し込みがあった場合、登録済みデータが「ワークスペース数＝４」であるため、2月からリミット値が超過することをSaaS管理者から警告します。
  
#. 登録済みデータが「ワークスペース数＝４」であるため、リミット値であるプランの「最大ワークスペース数＝５」を超過せずユーザーはワークスペースの追加ができます。
  
#. 登録済みデータが「ワークスペース数＝５」であるため、リミット値であるプランの「最大ワークスペース数＝５」を超過したワークスペースの追加ができません（エラーになります）。

#. 「最大ワークスペース数＝３」を超過しているが、利用停止等のシステム的な規制はこの段階ではありません。
  
#. リミット値である「最大ワークスペース数＝３」を超過しているため、SaaS管理者からオーガナイゼーションの警告が行われます。
  
#. ユーザーが リミット値を超過した状態で使い続けた場合、SaaS管理者は利用停止を実施します。
  
#. ユーザーはログイン不可および、「全リミット0プラン」に変更されます。　※スケジュールしていたものも動かなくなります。


.. danger::
    | 登録したワークスペース数を超えた利用が継続される場合はExastro IT Automation の利用が停止されます。


プラン設定
==========

前提条件
--------

| 本作業には下記のコマンドが必要となるため、事前にインストールをしてください。

- 作業クライアントに必要なアプリケーション

  - :kbd:`curl`
  - :kbd:`git`
  - :kbd:`jq`
 

プラン設定の流れ
----------------
| プランを登録する流れは以下の通りとなります。


.. image:: /images/ja/diagram_chart/manuals/plan_setting_flow.png
   :width: 6.68819in
   :height: 3.35972in
   :align: center
   :alt: プラン設定の流れ



事前準備
--------
| GitHub リポジトリから取得した資材の中にある、シェルスクリプトを実行しオーガナイゼーションを作成します。
| confファイルは、各種設定・取得シェルで使用します。

#. オーガナイゼーション作成用シェルスクリプトを、リポジトリから :kbd:`git clone` により取得します。

   .. code-block:: bash

      # Exastro Platform の資材を入手
      git clone https://github.com/exastro-suite/exastro-platform.git


#. 取得した資材のtoolsフォルダに移動し、オーガナイゼーション作成用シェルスクリプト内のAPI実行先URLを、Platform管理者用サイトアドレスに変更します。

   .. code-block:: bash

      vi api-auth.conf

   | 変更箇所

   - api-auth.conf

     .. code-block:: bash
        
        CONF_BASE_URL={Platform管理者用サイトアドレス}
        CURL_OPT=-svk

| ※HTTPSで実行する場合は、 `CURL_OPT=-sv` から `CURL_OPT=-svk` に変更してください。


プラン設定項目の確認
--------------------
- コマンド
    
  .. code-block:: bash

      ./get-plan-item-list.sh


- コマンド実行後に入力（入力例）

  .. code-block:: bash

      your username : Platform管理者自身のユーザー名を入力します
      your password : Platform管理者自身のパスワードを入力します

- 成功時の結果表示
  
  | `"result": "000-00000"` が、成功したことを示しています。

  .. code-block:: bash

      < HTTP/1.1 200 OK
      < Date: Fri, 09 Dec 2022 06:58:26 GMT
      < Server: Apache/2.4.37 (Red Hat Enterprise Linux) mod_wsgi/4.7.1 Python/3.9
      < Content-Length: 451
      < Content-Type: application/json
      < 
      { [451 bytes data]
      * Connection #0 to host platform-auth left intact
      {
      "data": [
          {
          "id": "platform.roles",
          "informations": {
              "description": "default limit"
          }
          },
          {
          "id": "platform.users",
          "informations": {
              "description": "default limit"
          }
          },
          {
          "id": "platform.workspaces",
          "informations": {
              "description": "default limit"
          }
          }
      ],
      "message": "SUCCESS",
      "result": "000-00000",
      "ts": "2022-12-09T06:58:26.764Z"
      }

- RestAPIを直接呼び出す場合は以下の内容で呼び出すことが出来ます。

  .. code-block:: bash

      BASE64_BASIC=$(echo -n "Platform管理者のユーザー名を設定してください:Platform管理者のパスワードを設定してください" | base64)
      BASE_URL=Platform管理者用サイトアドレスを設定してください

      curl -k -X GET \
          -H "Content-Type: application/json" \
          -H "Authorization: basic ${BASE64_BASIC}" \
          -d  @- \
          "${BASE_URL}/api/platform/plan_items"


プラン登録
----------

- 登録するプランのjsonファイルを設定
    
  | 取得した toolsフォルダ配下にある、 `add-plan.sample.json` を コピーして使用してください。


- 登録するPlanの設定
    
  | add-plan.jsonにコピーした例

  .. code-block:: bash

      vi add-plan.json


  .. code-block:: bash

      {
          "id": "plan-standard",
          "name": "スタンダードプラン",
          "informations": {
              "description": ""
          },
          "limits": {
              "platform.workspaces": 100,
              "platform.users": 200,
              "platform.roles": 200
          }
      } 

  ※limitsは、プラン設定項目の確認で取得した内容をもとに作成します

- 項目説明

  .. list-table:: プラン設定項目
     :widths: 20, 20, 40
     :header-rows: 1
     :align: left

     * - 項目
       - 項目の内容
       - 形式
     * - id 
       - プランID 
       - | 英小文字、数字、ハイフン、アンダースコア(最大３６文字)
         | ※先頭文字は英小文字であること
         | ※予約語(後述)に合致しないこと
     * - name 
       - プラン名
       - 最大２５５文字
     * - informations.description 
       - 説明
       - 最大２５５文字
     * - limits.xxxxxx.xxxxx
       - 取得したプラン項目の内容を設定
       - 数値
 
- コマンド
   
  .. code-block:: bash

      ./add-plan.sh add-plan.json


- コマンド実行後に入力（入力例）
   
  .. code-block:: bash

      your username : Platform管理者自身のユーザー名を入力します
      your password : Platform管理者自身のパスワードを入力します

- 成功時の結果表示
  
  | `"result": "000-00000"` が、成功したことを示しています。
   
  .. code-block:: bash

      < HTTP/1.1 200 OK
      < Date: Fri, 09 Dec 2022 08:12:35 GMT
      < Server: Apache/2.4.37 (Red Hat Enterprise Linux) mod_wsgi/4.7.1 Python/3.9
      < Content-Length: 104
      < Content-Type: application/json
      < 
      { [104 bytes data]
      * Connection #0 to host platform-auth left intact
      {
      "data": null,
      "message": "SUCCESS",
      "result": "000-00000",
      "ts": "2022-12-09T08:12:36.219Z"
      }

- 失敗時の結果表示イメージ
  
  .. code-block:: bash

      < HTTP/1.1 400 BAD REQUEST
      < Date: Fri, 09 Dec 2022 08:16:09 GMT
      < Server: Apache/2.4.37 (Red Hat Enterprise Linux) mod_wsgi/4.7.1 Python/3.9
      < Content-Length: 265
      < Connection: close
      < Content-Type: application/json
      < 
      { [265 bytes data]
      * Closing connection 0
      {
        "data": null,
        "message": "指定されたプランはすでに存在しているため作成できません。",
        "result": "400-27001",
        "ts": "2022-12-09T08:16:09.830Z"
      }

- RestAPIを直接呼び出す場合は以下の内容で呼び出すことができます。

  .. code-block:: bash

    BASE64_BASIC=$(echo -n "Platform管理者のユーザー名を設定してください:Platform管理者のパスワードを設定してください" | base64)
    BASE_URL=Platform管理者用サイトアドレスを設定してください

    curl -k -X POST \
        -H "Content-Type: application/json" \
        -H "Authorization: basic ${BASE64_BASIC}" \
        -d  @- \
        "${BASE_URL}/api/platform/plans" \
        << EOF
    {
      "id": "plan-standard",
      "name": "スタンダードプラン",
      "informations": {
        "description": ""
      },
      "limits": {
        "platform.workspaces": 100,
        "platform.users": 200,
        "platform.roles": 200
      }
    }     
    EOF


設定済みプランの確認 
--------------------

- コマンド
   
  .. code-block:: bash

      ./get-plan-list.sh


- コマンド実行後に入力（入力例）
   
  .. code-block:: bash

     your username : Platform管理者自身のユーザー名を入力します
     your password : Platform管理者自身のパスワードを入力します


- 成功時の結果表示
  
  | `"result": "000-00000"` が、成功したことを示しています。
   
  .. code-block:: bash

      < HTTP/1.1 200 OK
      < Date: Thu, 12 Jan 2023 08:26:42 GMT
      < Server: Apache/2.4.37 (Red Hat Enterprise Linux) mod_wsgi/4.7.1 Python/3.9
      < Content-Length: 4274
      < Content-Type: application/json
      < 
      { [4274 bytes data]
      * Connection #0 to host platform-auth left intact
      {
        "data": [
          {
            "create_timestamp": "2022-12-07T06:04:31.000Z",
            "create_user": "system",
            "id": "_default",
            "informations": {
              "description": "default plan"
            },
            "last_update_timestamp": "2022-12-07T06:04:31.000Z",
            "last_update_user": "system",
            "limits": {
              "platform.workspaces": 100,
              "platform.roles": 1000,
              "platform.users": 10000
            },
            "name": "_default plan"
          },
          {
            "create_timestamp": "2022-12-09T08:12:36.000Z",
            "create_user": "bd09d674-298f-4b55-9777-0758bf6f294e",
            "id": "plan-standard",
            "informations": {
              "description": ""
            },
            "last_update_timestamp": "2022-12-09T08:12:36.000Z",
            "last_update_user": "bd09d674-298f-4b55-9777-0758bf6f294e",
            "limits": {
              "platform.roles": 200,
              "platform.users": 200,
              "platform.workspaces": 100
            },
            "name": "スタンダードプラン"
          }
        ],
        "message": "SUCCESS",
        "result": "000-00000",
        "ts": "2023-01-12T08:26:42.375Z"
      }


- RestAPIを直接呼び出す場合は以下の内容で呼び出すことができます。

  .. code-block:: bash

    BASE64_BASIC=$(echo -n "Platform管理者のユーザー名を設定してください:Platform管理者のパスワードを設定してください" | base64)
    BASE_URL=Platform管理者用サイトアドレスを設定してください

    curl -k -X GET \
        -H "Content-Type: application/json" \
        -H "Authorization: basic ${BASE64_BASIC}" \
        -d  @- \
        "${BASE_URL}/api/platform/plans"


オーガナイゼーションへのプラン設定
----------------------------------

- 登録するプランのjsonファイルを設定します。

  | 取得した toolsフォルダ配下にある、add-organization-plan.sample.json を コピーして使用してください。

- 登録するPlanの設定
  
  | 例はオーガナイゼーションID:org1、プランID:plan-standardを例として説明します。
  | 
  | add-org1-plan.jsonにコピーした例） 


  .. code-block:: bash

    vi add-org1-plan.json


  .. code-block:: bash
      
      {
        "id": "plan-standard",
        "start_datetime": "2022-12-01 00:00:00"
      }

- 項目説明
  
  .. list-table:: オーガナイゼーションへのプラン設定項目
     :widths: 20, 20, 40
     :header-rows: 1
     :align: left

     * - 項目
       - 項目の内容
       - 形式
     * - id 
       - プランID 
       - プラン設定で設定したプランID
     * - start_datetime 
       - プラン開始日 
       - 日時形式、時分秒必須


- コマンド
   
  .. code-block:: bash

      ./add-organization-plan.sh add-org1-plan.json


- コマンド実行後に入力（入力例）
   
  .. code-block:: bash

     organization id : プラン設定するorganization idを入力します
     
     your username : Platform管理者自身のユーザー名を入力します
     your password : Platform管理者自身のパスワードを入力します

- 成功時の結果表示
  
  | `"result": "000-00000"` が、成功したことを示しています。
   
  .. code-block:: bash

      < HTTP/1.1 200 OK
      < Date: Mon, 12 Dec 2022 01:22:42 GMT
      < Server: Apache/2.4.37 (Red Hat Enterprise Linux) mod_wsgi/4.7.1 Python/3.9
      < Content-Length: 104
      < Content-Type: application/json
      < 
      { [104 bytes data]
      * Connection #0 to host platform-auth left intact
      {
        "data": null,
        "message": "SUCCESS",
        "result": "000-00000",
        "ts": "2022-12-12T01:22:42.886Z"
      }

- 失敗時の結果表示イメージ
   
  .. code-block:: bash

     < HTTP/1.1 404 NOT FOUND
      < Date: Mon, 12 Dec 2022 01:40:02 GMT
      < Server: Apache/2.4.37 (Red Hat Enterprise Linux) mod_wsgi/4.7.1 Python/3.9
      < Content-Length: 127
      < Content-Type: application/json
      < 
      { [127 bytes data]
      * Connection #0 to host platform-auth left intact
      {
        "data": null,
        "message": "organization not found id:org2",
        "result": "404-00001",
        "ts": "2022-12-12T01:40:03.268Z"
      }


- RestAPIを直接呼び出す場合は以下の内容で呼び出すことができます。
  
  .. code-block:: bash

      BASE64_BASIC=$(echo -n "Platform管理者のユーザー名を設定してください:Platform管理者のパスワードを設定してください" | base64)
      BASE_URL=Platform管理者用サイトアドレスを設定してください
      ORG_ID=プラン設定するorganization idを設定してください

      curl -k -X POST \
          -H "Content-Type: application/json" \
          -H "Authorization: basic ${BASE64_BASIC}" \
          -d  @- \
          "${BASE_URL}/api/platform/${ORG_ID}/plans" \
          << EOF
      {
          "id": "plan-standard",
          "start_datetime": "2022-12-01 00:00:00"
      }
      EOF


オーガナイゼーションへのプラン解除
----------------------------------

- コマンド
 
  .. code-block:: bash

     ./delete-organization-plan.sh


- コマンド実行後に入力（入力例）
 
  .. code-block:: bash

      organization id : プラン解除するorganization idを入力します
      start datetime (yyyy-mm-dd hh:mm:ss) : プラン解除するstart datetimeを入力します (yyyy-mm-dd hh:mm:ss形式)

      your username : Platform管理者自身のユーザー名を入力します
      your password : Platform管理者自身のパスワードを入力します

- 成功時の結果表示
  
  | `"result": "000-00000"` が、成功したことを示しています。
   
  .. code-block:: bash

      < HTTP/1.1 200 OK
      < Date: Mon, 12 Dec 2022 01:46:58 GMT
      < Server: Apache/2.4.37 (Red Hat Enterprise Linux) mod_wsgi/4.7.1 Python/3.9
      < Content-Length: 104
      < Content-Type: application/json
      < 
      { [104 bytes data]
      * Connection #0 to host platform-auth left intact
      {
        "data": null,
        "message": "SUCCESS",
        "result": "000-00000",
        "ts": "2022-12-12T01:46:58.794Z"
      }

- 失敗時の結果表示イメージ
  
  .. code-block:: bash

      < HTTP/1.1 404 NOT FOUND
      < Date: Mon, 12 Dec 2022 01:46:14 GMT
      < Server: Apache/2.4.37 (Red Hat Enterprise Linux) mod_wsgi/4.7.1 Python/3.9
      < Content-Length: 205
      < Content-Type: application/problem+json
      * HTTP error before end of send, stop sending
      < 
      { [205 bytes data]
      * Closing connection 0
      {
        "detail": "The requested URL was not found on the server. If you entered the URL manually please check your spelling and try again.",
        "status": 404,
        "title": "Not Found",
        "type": "about:blank"
      }

- RestAPIを直接呼び出す場合は以下の内容で呼び出すことができます。
  
  .. code-block:: bash

      BASE64_BASIC=$(echo -n "Platform管理者のユーザー名を設定してください:Platform管理者のパスワードを設定してください" | base64)
      BASE_URL=Platform管理者用サイトアドレスを設定してください
      ORG_ID=プラン解除するorganization idを設定してください
      START_DATETIME=プラン解除するプラン開始日時を設定してください(yyyy-mm-dd hh:mm:ss形式)

      curl -k -X DELETE \
          -H "Content-Type: application/json" \
          -H "Authorization: basic ${BASE64_BASIC}" \
          -d  @- \
          "${BASE_URL}/api/platform/${ORG_ID}/plans/${START_DATETIME}"