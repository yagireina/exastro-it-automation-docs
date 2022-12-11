=================
マニュアルのビルド
=================

前提
====

| 以下がインストールされている事とします。\
| 　sphinx-build 5.3.0 以上

ビルドについて
==============

| 本マニュアルは以下の作成手順をとります。
|   ビルド元 (図左側) を所定のフォーマットで記述  --> ビルドして結果(図右側)を得る
|
| 図右側の赤枠箇所はビルドによって自動生成されます
.. figure:: ../../images/ja_manual_design/before_after_2_0.png
   :width: 5.84375in
   :height: 1.09375in
   :align: center
   :alt: build_before_after

   ビルド元とビルド結果
   
ビルドの流れ
============

| ビルド作業は以下のステップで実施します。
#. 大章ごとにディレクトリを作成
#. 大章一覧を記述したファイル (index.rst) を作成
#. 作成した大章用ディレクトリ内に中章の内容 (=「右 pane のボディ」部分 ) を記述した 「.rst ファイル」 を作成
#. 作成した大章用ディレクトリ内に画像ファイル格納用ディレクトリを作成
#. 中章一覧を記述したファイル (index.rst) を作成
#. 「.rst ファイル」群をビルドしてhtml ファイル生成

.. note:: | .rst ファイルは .docx (Word) ファイルから生成することもできます。本マニュアルでは直接 .rst ファイルを作成する方法を説明します。
| 
| ステップ 1～6 の各手順について、赤枠内ドキュメントを例に挙げて説明します。
.. figure:: ./build_flow/image4.png
   :width: 5.1083in
   :height: 2.3537in
   :align: center
   :alt: build_sample_target

   サンプルビルド対象

ビルド手順詳細
==============

| ★…追加箇所

大章ごとにディレクトリを作成
----------------------------
.. code-block:: bash
 
   ドキュメントルート(documentation/v2.0/ja)
   　|-- install (大章「インストール」用ディレクトリ  ★

.. note:: | ディレクトリ名は各大章名(英語版)から引用し、以下の通りのフォーマットとします。
          | It Automation Base it_automation_base (すべて小文字、単語間は \_ でつなぎます。)

大章一覧を記述したindex.rstファイルを作成
-----------------------------------------
.. code-block:: bash

   ドキュメントルート(documentation/v2.0/ja)
   　|-- install
   　|-- index.rst (大章一覧を記載します。) ★

.. note:: | index.rst ファイルの構文については :ref:`index-rns` をご参照下さい

中章の内容を記述した 「.rst ファイル」 を作成
---------------------------------------------

| 作成した大章用ディレクトリ内に中章の内容 (=「右 pane のボディ」部分 )を記述した 「.rst ファイル」 を作成します。
.. code-block:: bash

   ドキュメントルート(documentation/v2.0/ja)
   　|-- install
   　|　 |-- installation.rst (中章の内容を記述します。)  ★
   　|-- index.rst

.. note:: | .rst ファイルの構文については :ref:`doc-rns` をご参照下さい

画像ファイル格納用ディレクトリを作成
------------------------------------

.. code-block:: bash

  ドキュメントルート(documentation/v2.0/ja)
   　|-- install
   　|　 |-- installation.rst
   　|　 |-- installation 画像ファイル格納用ディレクトリ  ★ (.rst ファイル名と同名にします。) 
   　|-- index.rst

中章一覧を記述したファイルを作成
--------------------------------

.. code-block:: bash

   ドキュメントルート(documentation/v2.0/ja)
   　|-- install
   　|　 |-- installation.rst
   　|　 |-- installation 
   　|　 |-- index.rst (中章一覧を記載します。) ★
   　|-- index.rst

ビルド先ディレクトリを作成
--------------------------------

| documentation ディレクトリ配下に html ディレクトリを作成します。

.. code-block:: bash

  documentation
  　|-- html ★
  　|-- v2.0
  　|   |-- ja
  　|-- install
  　|　 |-- installation.rst
  　|　 |-- installation 
  　|　 |-- index.rst (中章一覧) 
  　|-- index.rst

| ここまでがビルドに必要なディレクトリ、ファイルの配置です。


「.rst ファイル」群をビルドしてhtml ファイル生成
------------------------------------------------

| documentation ディレクトリにカレントをうつし、以下コマンドを入力すると
| htmlディレクトリ配下に html ファイル群が生成されます。

.. code-block:: bash

   sphinx-build -b html ./ ./html
