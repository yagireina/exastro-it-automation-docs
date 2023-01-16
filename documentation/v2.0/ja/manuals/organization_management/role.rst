======
ロール
======

はじめに
========

| 本章では、Exastro Suite におけるロールについて説明します。


ロールとは
==========

| {{ #1 記載お願いいたします。 }}


ロール紐づけ
=============

| {{ #2 記載お願いいたします。 }}

| ロール管理では下記２つの使用方法を行うことが可能です。
- | :ref:`role_workspace`
  | ロールごとにワークスペースへのアクセス権限をメンテナンスできます。 
- | :ref:`role_user`
  | ユーザ毎にアクセスを許可するロールを付与することで、ユーザごとにワークスペースへのアクセスを制御することができます。

.. _role_workspace:
ロール追加・ワークスペース紐づけ
----------------------------------

#. | Exastro Platformにオーガナイゼーション管理者 または _${ws-id}-adminロールに紐づくユーザーでログインします。


#. | Exastro Platformのメニューより :menuselection:`ロール管理` をクリックします。

   .. image:: ./role/image1.png
      :width: 2.22054in
      :height: 1.90683in

   
   
   .. note:: | オーガナイゼーション管理者以外でログインしている時は、メニューに :menuselection:`ロール管理` は表示されません。

#. | ロール一覧画面が表示されるので、:guilabel:`作成` ボタンをクリックします。

   .. figure:: ./role/image2.png
      :width: 8.22054in
      :height: 1.90683in
      :align: center

#. | 新規ロール画面が表示されるので、ロールの情報を入力し、:guilabel:`登録` ボタンをクリックします。

   .. figure:: ./role/image3.png
      :width: 8.22054in
      :height: 1.90683in
      :align: center

   .. note:: | 「使用ワークスペース」にワークスペースの一覧が表示されるので、当該ロールに紐づけるワークスペースを選択します。
    
    .. figure:: ./role/image4.png
       :width: 8.22054in
       :height: 1.90683in
       :align: center

.. _role_user:
ユーザー・ロール紐づけ
----------------------------------

#. | Exastro Platformにオーガナイゼーション管理者 または _${ws-id}-adminロールに紐づくユーザーでログインします。
#. | Exastro Platformのメニューより :menuselection:`ロール管理` をクリックします。

   .. image:: ./role/image5.png
      :width: 2.22054in
      :height: 1.90683in

   .. note:: | オーガナイゼーション管理者、_${ws-id}-adminロールに紐づくユーザー以外でログインしている時は、メニューに :menuselection:`ロール管理` は表示されません。

#. | ロール一覧画面が表示されるので、ユーザーとロールの紐づけを変更したいロールを選択し :guilabel:`ユーザー` ボタンをクリックします。

   .. figure:: ./role/image6.png
      :width: 8.22054in
      :height: 1.90683in
      :align: center

#. | ロール付与・解除画面が表示されるので、ロールとの紐づけを変更したいユーザーを選択し、 :guilabel:`適用` ボタンをクリックします。

   .. figure:: ./role/image7.png
      :width: 8.22054in
      :height: 1.90683in
      :align: center
