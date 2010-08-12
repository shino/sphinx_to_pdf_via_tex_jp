===============================================================
日本語 Sphinx ドキュメントの PDF 化(TeX 経由)のサンプル
===============================================================

目的
=====================

このサンプルプロジェクトは、日本語を含む Sphinx ドキュメントから PDF ファ
イルを生成することを目的としています。あくまで個人的なサンプルです。網
羅的な Sphinx の機能に対する PDF 出力確認を行うことを目的とするのもでは
ありません。

実装方法
=====================

PDF 出力のため、Sphinx 自体が持っている LaTeX 出力機能を利用します。
Sphinx の機能だけで、英語のみのドキュメントは make -C _build/latex
all-pdf コマンドにて PDF 生成が可能です。ただし日本語を含むドキュメント
の場合、エラーが発生するため、いくつかの修正が必要になります。

具体的には、以下の点で修正を行ないます。

* _build/latex/Makefile の置き換え

  * latex コマンドを xelatex に置き換える

* TeX ファイルの中身の置き換え

TeX は素人のため、 Sphinx が生成する tex ファイルに手を入れることは最低
限にする方針です。

PDF 生成方法
=====================

環境設定
^^^^^^^^^^^^^^^^^^^^^

Sphinx と TexLive が必要です。TeXLive は XeTeX だけでも良いかもしれませ
んが未確認です。

以下に、MacPorts を用いた例を示します。

Sphinx のインストール::

 $ sudo port install py26-sphinx

必要なら、 sphinx-\*-2.6 にエイリアスを設定するなどしてください。

TexLive のインストール::

 $ sudo port install texlive +full

PDF 生成方法
^^^^^^^^^^^^^^^^^^^^^

Sphinx で latex を生成した後、 PDF ファイルを生成します。

::

 $ make latex
 $ make pdf

デバッグ用途には、PDF 生成のターゲットを構成するサブターゲットを
個別に実行することが有用な場合があります。

::

 $ make pdf-patch     # _build/latex/ 以下のファイルにパッチをあてる
 $ make pdf-generate  # xelatex の実行
 $ make pdf-open      # PDF ファイルを開く

pdf-open は open コマンドを用いているため、 Mac OS X 以外では動作
しない可能性があります。例えば、 GNOME 環境の場合は、 gnome-open を
open にエイリアスすることで動作するはずです。

参考
=====================

Sphinx の勉強には、 Sphinx-Users.jp が有用です。

* http://sphinx-users.jp/

本プロジェクト内のサンプル作成には、 Sphinx-Users.jp のドキュメントを参
考にしています。

* プロジェクトを作る http://sphinx-users.jp/gettingstarted/make_project.html

XeTeX の日本語環境については、以下のサイトを参考にしています。

* XeLaTeX で日本語する件について [電脳世界の奥底にて] http://zrbabbler.hp.infoseek.co.jp/xelatex.html
* XeTeX - TeX Wiki http://oku.edu.mie-u.ac.jp/~okumura/texwiki/?XeTeX
* XeTeXに関するメモ http://math.kyokyo-u.ac.jp/users/skiriki/

ライセンスはクリエイティブ・コモンズを利用しています。

* Creative Commons http://creativecommons.org/

CSV ファイルのサンプルとして、郵便番号のデータを利用しています。

* 郵便番号データダウンロード - 日本郵便 http://www.post.japanpost.jp/zipcode/download.html



動作確認環境
====================

動作確認は以下の環境で行っています。

* Mac OS X (10.6)

* Sphinx 1.0.1

* TeXLive 2009 (MacPorts を用いて、 +full でインストール)

  * XeTeX 3.1415926-2.2-0.9995.2 (TeX Live/MacPorts 2009_3)

課題
====================

* 日本語のスタイル

  * CHAPTER ONE

  * CONTENTS

  * その他いろいろ

* 文書内のリンクがどう PDF で表現されるか確認する。

* テーブルの表示方法

  * 行ごとに横罫線を入れる。

  * 一行おきに背景色を薄い灰色にする。

* 警告のディレクティブの場合に、"Danger", "Note" などの文字列部分を変更できるか試す。

* 行をまたぐ文章の場合、行またぎ箇所に半角空白が入ってしまうことへの対応。

  * 英語での TeX の挙動になっていると思われる。

  * 空行(^$)以外の行末に % を付けることで解決は可能。自動化をどうするかを検討する必要がある。

  * 拡張を導入してみたが、整形済みテキストでも行連結が行われるため無効にしている。

    渋日記: 日本語でSphinxを使う時のストレスを減らす拡張機能
    http://blog.shibu.jp/article/40049067.html

* xelatex 実行時に "Font shape <フォント名> undefined" がいくつか発生している。

  * 影響範囲が不明

  * 「3.1 コード」のダラーマーク($)のフォントがおかしいのは関連しているかも。

* パッチ等の修正を conf.py の LaTeX 関連の設定で回避できるか検討する。

* _build/latex/Makefile の修正をファイル置き換えから patch にする。

* このファイル自体(README.rst)が、 github で見ると行間が詰まっていて読みにくい。

  * reST から HTML の line-height の指定が可能か?

解決済みの課題
====================

* [bug] 意図しない空白(?)が入る。

  * 意図しない空白が入ったことを確認した箇所

    * 表紙のタイトル

    * テーブルのヘッダー

  * 2010-08-08 追記 Sphinx 1.0.1 に上げたことで解決しているかもしれない。しばらく様子見。

* CSV テーブルを使用した場合の PDF 出力を確認する。

  * 横幅が紙サイズに収まらず切れてしまう。

  * シンプルテーブル、リストテーブルでは、自動で改行されるので、
    csv -> table の変換 & include での回避が簡単かもしれない

  * 2010-08-08 追記: tabularcolumns ディレクティブにて、手動調整ではあるが回避可能

  * 数字、半角カナのセルでは、セルの幅に収まらずはみ出している値がある

    * フォント設定の変更で収まるようになった

	* 変更前 ``\setromanfont{Hiragino Mincho Pro W3}``

	* 変更後 ``\setromanfont[Scale=MatchLowercase]{Hiragino Mincho Pro W3}``



変更履歴
========================================

2010-08-08 shino
  環境を Sphinx 1.0.1 に変更

2010-07-24 shino
  新規作成

コピーライト、ライセンス、免責条項
========================================
Copyright (c) 2010 Shun'ichi Shinohara

The files under this project are licensed by Creative Commons
Attribution-ShareAlike 3.0 Unported.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
