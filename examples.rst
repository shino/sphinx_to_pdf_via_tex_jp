=========================================
Sphinx 記法と日本語、文字に関するサンプル
=========================================

コード
======

::

   $ python egg.py
   Hello Python World, and Sphinx!

画像
=====

.. image:: _static/sphinx.png

強調
=====

* アスタリスク1つ: *テキスト*  強調( イタリック ) <- 日本語文字では(フォント依存だがほぼ)無効
* アスタリスク2つ: **テキスト** 強い強調( 太文字 )
* バッククオート: ``テキスト`` コードサンプル( 固定長 )

文字
=====

* コピーライト記号 ©
* キロメートルなど ㎞ ㌶ ㎡
* 括弧付き ㈱ ㈲
* まる付き ① ⑩

警告
=========

DANGER

.. DANGER::
   Beware killer rabbits!

note

.. note:: This is a note admonition.
   This is the second line of the first paragraph.

   - The note contains all indented body elements
     following.
   - It includes this bullet list.

admonition

.. admonition:: And, by the way...

   You can make up your own admonition too.

テーブル
==============

グリッドテーブル
^^^^^^^^^^^^^^^^^^^^

LaTeX 出力ではセルの連結はサポートされていない。

.. table:: グリッドテーブルの例

   +------------+------------+-----------+
   | Header 1   | Header 2   | Header 3  |
   +============+============+===========+
   | body row 1 | column 2   | column 3  |
   +------------+------------+-----------+
   | body row 2 | Cells      |           |
   +------------+------------+-----------+
   | body row 3 | Cell       | Cells     |
   +------------+------------+-----------+


シンプルテーブル
^^^^^^^^^^^^^^^^^^^^^^

.. table:: シンプルテーブルの例

   =====  =====  ======
     甲     乙    和
   =====  =====  ======
   偽     偽     偽
   真     偽     真
   偽     真     真
   真     真     真
   =====  =====  ======

リストテーブル
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table:: Frozen Delights!
   :widths: 15 10 30
   :header-rows: 1

   * - Treat
     - Quantity
     - Description
   * - Albatross
     - 2.99
     - On a stick!
   * - Crunchy Frog
     - 1.49
     - If we took the bones out, it wouldn't be
       crunchy, now would it?
   * - Gannet Ripple
     - 1.99
     - On a stick!



シンプルテーブルでセル内の自動改行
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. table:: シンプルテーブルの例

   ======================================================  ======================================================  ============================================================
   長い行のサンプル                                         あ                                                      い
   ======================================================  ======================================================  ============================================================
   あああああああああああああああああああああああああああ  あああああああああああああああああああああああああああ  いいいいいいいいいいいいいいいいいいいいいいいいいいいいいい
   ======================================================  ======================================================  ============================================================

リストテーブルでセル内の自動改行
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table:: Frozen Delights!
   :widths: 15 10 30
   :header-rows: 1

   * - Treat
     - Quantity
     - Description
   * - Albatross
     - 2.99
     - アホウドリアホウドリアホウドリアホウドリアホウドリアホウドリアホウドリアホウドリアホウドリアホウドリアホウドリアホウドリアホウドリアホウドリアホウドリアホウドリ
   * - くらんちーふろぐくらんちーふろぐくらんちーふろぐくらんちーふろぐくらんちーふろぐくらんちーふろぐくらんちーふろぐ
     - 1.49
     - If we took the bones out, it wouldn't be
       crunchy, now would it?
       If we took the bones out, it wouldn't be
       crunchy, now would it?
       If we took the bones out, it wouldn't be
       crunchy, now would it?
       If we took the bones out, it wouldn't be
       crunchy, now would it?
   * - Gannet Ripple
     - 1.99
     - On a stick!



CSV テーブル
===============

.. tabularcolumns:: |p{1cm}|p{0.7cm}|p{1cm}|p{1cm}|p{1cm}|p{1cm}|p{1cm}|p{1cm}|p{2cm}|p{0.2cm}|p{0.2cm}|p{0.2cm}|p{0.2cm}|p{0.2cm}|p{0.2cm}|

.. csv-table:: 郵便番号表 東京
   :header: "コード", "5桁", "7桁", "都道府県名", "市区町村名", "町域名", "都道府県名", "市区町村名", "町域名", "A", "B", "C", "D", "E", "F"
   :widths: 4, 5, 5, 11, 12, 13, 11, 12, 13, 2,2,2,2,2,2
   :file: _static/zipcode_tokyo.csv

CSV を list-table に変換して include
============================================================

.. include:: _static/zipcode_tokyo.rst

