======
ユーザ
======


はじめに
========

| 本章では、Exastro Suite におけるユーザについて説明します。


ユーザとは
==========

| Exastro システムの利用者のことを指します。
| ユーザのタイプには大きく分けて下記の3種類が存在します。

- プラットフォーム管理者
- オーガナイゼーション管理者
- 利用ユーザ

| :dfn:`プラットフォーム管理者` は、Exastro システム全体の管理者のことで、オーガナイゼーションやオーガナイゼーション管理者の作成、プランの設定といったシステム全体に関わる操作を実行できる一方で、オーガナイゼーション内のワークスペース、および、Exastro IT Automation に関する操作は実行できません。
| :dfn:`オーガナイゼーション管理者` は、オーガナイゼーションの管理者のことで、プラットフォーム管理者により作成されたオーガナイゼーションに対してユーザの作成やロールの割当といったオーガナイゼーションの管理をするための操作を実行できます。
| :dfn:`利用ユーザ` は、上記2つ以外のすべてのユーザのことで、Exastro の各ツールの操作を実行できます。

| 上記のユーザ毎に作成方法が異なりますので、それぞれの方法について説明します。


プラットフォーム管理者の作成
============================

| プラットフォーム管理者は、インストール時に :ref:`installation_kubernetes_Keycloak 設定` で :kbd:`global.keycloakDefinition.secret.KEYCLOAK_USER` に指定しインストールした際に作成されます。


オーガナイゼーション管理者の作成
================================

| オーガナイゼーション管理者は、オーガナイゼーション作成時に :doc:`../platform_management/organization` で :kbd:`organization_managers` に指定することで作成されます。


利用ユーザの作成
================

| 利用ユーザは、下記の方法で作成します。

#. | Exastro Platformにオーガナイゼーション管理者でログインします。


#. | Exastro Platformのメニューより :menuselection:`ユーザ管理` をクリックします。

   .. image:: ./user/image1.png
      :width: 200px
      :align: left

   .. note::
      | オーガナイゼーション管理者以外でログインしている時は、メニューに :menuselection:`ユーザ管理` は表示されません。

#. | keycloakのユーザ画面が表示されるので、 :guilabel:`ユーザの追加` ボタンをクリックします。

   .. figure:: ./user/image2.png
      :width: 600px
      :align: left

#. | keycloakのユーザの追加画面が表示されるので、ユーザの情報を入力して :guilabel:`保存` ボタンをクリックします。

   .. figure:: ./user/image3.png
      :width: 600px
      :align: left


#. | 登録が正常に終了すると、以下の画面が表示されますので、 :menuselection:`クレデンシャル` タブをクリックします。

   .. figure:: ./user/image4.png
      :width: 600px
      :align: left


#. | 「パスワード」および「新しいパスワード（確認）」に初期パスワードを入力し :guilabel:`パスワードを設定` をクリックします。

   .. figure:: ./user/image5.png
      :width: 600px
      :align: left

   .. note:: | 一時的を「オン」にした場合は、パスワードを設定したユーザで次回ログイン時にパスワードの変更が必要になります。

#. | 確認ダイアログが表示されるので、 :guilabel:`Set password` ボタンをクリックします。

   .. figure:: ./user/image6.png
      :width: 600px
      :align: left
