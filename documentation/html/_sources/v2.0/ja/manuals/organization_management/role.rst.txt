======
ロール
======

はじめに
========

| 本章では、Exastro Suite におけるロールについて説明します。


ロールとは
==========

| ロールとは、ユーザやワークスペース内のデータといった Exastro システムにおけるリソースに対する操作(作成、更新、削除)権限の集合のことです。


ロール作成とユーザへの紐づけ
============================

| ロールの新規作成方法とユーザへの紐づけ方法について下記の流れで説明します。

#. | :ref:`role_workspace`
   | ロールごとにワークスペースへのアクセス権限をメンテナンスできます。 
#. | :ref:`role_user`
   | ユーザ毎にアクセスを許可するロールを付与することで、ユーザごとにワークスペースへのアクセスを制御することができます。

.. _role_workspace:

ロール追加・ワークスペース紐づけ
--------------------------------

#. | Exastro Platformにオーガナイゼーション管理者 または _${ws-id}-adminロールに紐づくユーザでログインします。


#. | Exastro Platformのメニューより :menuselection:`ロール管理` をクリックします。

   .. image:: ./role/image1.png
      :width: 200px
      :align: left
      
   .. note:: | オーガナイゼーション管理者以外でログインしている時は、メニューに :menuselection:`ロール管理` は表示されません。

#. | ロール一覧画面が表示されるので、:guilabel:`作成` ボタンをクリックします。

   .. figure:: ./role/image2.png
      :width: 600px
      :align: left

#. | 新規ロール画面が表示されるので、ロールの情報を入力し、:guilabel:`登録` ボタンをクリックします。

   .. figure:: ./role/image3.png
      :width: 600px
      :align: left

| :menuselection:`使用ワークスペース` にワークスペースの一覧が表示されるので、当該ロールに紐づけるワークスペースを選択します。
    
   .. figure:: ./role/image4.png
      :width: 600px
      :align: left

.. _role_user:

ユーザ・ロール紐づけ
--------------------

#. | Exastro Platformにオーガナイゼーション管理者 または _${ws-id}-adminロールに紐づくユーザでログインします。
#. | Exastro Platformのメニューより :menuselection:`ロール管理` をクリックします。

   .. image:: ./role/image5.png
      :width: 200px
      :align: left

   .. note:: | オーガナイゼーション管理者、_${ws-id}-adminロールに紐づくユーザ以外でログインしている時は、メニューに :menuselection:`ロール管理` は表示されません。

#. | ロール一覧画面が表示されるので、ユーザとロールの紐づけを変更したいロールを選択し :guilabel:`ユーザ` ボタンをクリックします。

   .. figure:: ./role/image6.png
      :width: 600px
      :align: left

#. | ロール付与・解除画面が表示されるので、ロールとの紐づけを変更したいユーザを選択し、 :guilabel:`適用` ボタンをクリックします。

   .. figure:: ./role/image7.png
      :width: 600px
      :align: left
