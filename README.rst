===============================================================
日本語 Sphinx ドキュメントの PDF 化(TeX 経由)のサンプル
===============================================================

目的
=====================

このサンプルプロジェクトは、日本語を含む Sphinx ドキュメントから PDF ファイルを生成することを目的としています。
あくまで個人的なサンプルです。網羅的な Sphinx の機能に対する PDF 出力確認を行うことを目的とするのもではありません。

実装方法
=====================

PDF 出力のため、Sphinx 自体が持っている LaTeX 出力機能を利用します。
Sphinx の機能だけで、英語のみのドキュメントは make -C _build/latex all-pdf コマンドにて PDF 生成が可能です。ただし日本語を含むドキュメントの場合、エラーが発生するため、いくつかの修正が必要になります。

具体的には、以下の点で修正を行ないます。

 * _build/latex/Makefile の置き換え
   * latex コマンドを xelatex に置き換えるだけ
 * TeX ファイルの中身の置き換え

TeX は素人のため、 Sphinx が生成する tex ファイルに手を入れることは最低限にする方針です。

参考
=====================

Sphinx の勉強には、 Sphinx-Users.jp が有用です。http://sphinx-users.jp/

本プロジェクト内のサンプル作成には、 Sphinx-Users.jp のドキュメントを参考にしています。

 * プロジェクトを作る http://sphinx-users.jp/gettingstarted/make_project.html

XeTeX の日本語環境については、以下のサイトを参考にしています。

 * XeLaTeX で日本語する件について [電脳世界の奥底にて] http://zrbabbler.hp.infoseek.co.jp/xelatex.html
 * XeTeX - TeX Wiki http://oku.edu.mie-u.ac.jp/~okumura/texwiki/?XeTeX
 * XeTeXに関するメモ http://math.kyokyo-u.ac.jp/users/skiriki/
 
ライセンスはクリエイティブ・コモンズを利用しています。

 * Creative Commons http://creativecommons.org/
 
動作確認環境
====================

動作確認は以下の環境で行っています。

* Mac OS X (10.6)
* Sphinx 0.6.7
* TeXLive 2009 (MacPorts を用いて、 +full でインストール)

  * XeTeX 3.1415926-2.2-0.9995.2 (TeX Live/MacPorts 2009_3)

TODO
====================

* 行をまたぐ文章の場合に、半角空白が入ってしまう。

  * 行末に % を付けることで解決は可能。自動化をどうするかを検討する必要がある。

* CSV テーブルを使用した場合の PDF 出力確認


コピーライト、ライセンス
========================================
Copyright (c) 2010 Shun'ichi Shinohara

The files under this project are licensed by Creative Commons Attribution-ShareAlike 3.0 Unported.

