.. _alta_first_step:
==============
ALTA最初の一歩
==============

アナジックスALBサーバに接続する
----------------------------
ALTAの画面で、Settingsのタブを表示し、ALB Siteを
http://alb.anagix.com:8180
に変更してください。すでにサインアップしていただいたアナジックスのサーバです。
User IDとPasswordを入力し、Login してください。


.. http://alb.anagix.com:8180/myGyazo/data/a72a396dc288f649bf4a9f94173c8fb1.png

.. image:: images/a72a396dc288f649bf4a9f94173c8fb1.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/a72a396dc288f649bf4a9f94173c8fb1.png

Setupボタンを押すと、以下の画面が表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/97fda60676239d3678fc0258f84d26fc.png

.. image:: images/97fda60676239d3678fc0258f84d26fc.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/97fda60676239d3678fc0258f84d26fc.png

プロジェクトを選択する
-------------------
Choose projectのプルダウンにプロジェクトの一覧が表示されます。

.. http://alb.anagix.com:8180/myGyazo/data/dfc04125f3f6f1a430b0bc714f83db47.png

.. image:: images/dfc04125f3f6f1a430b0bc714f83db47.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/dfc04125f3f6f1a430b0bc714f83db47.png

ALTA sampleを選択すると、ALBタブ画面にかわります。画面の左側に回路、右側にモデルライブラリが表示
されています。


.. http://alb.anagix.com:8180/myGyazo/data/8c5aaeff0c612e607158298967628d13.png

.. image:: images/8c5aaeff0c612e607158298967628d13.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/8c5aaeff0c612e607158298967628d13.png

circuitsから、circuits->opamp->instance0->testbenches と展開すると上図の画面になります。

LTspiceに回路を表示する
---------------------
CMRR(asc)の上でダブルクリックするか、下のCommandsからEditをクリックして
ください。下図のようにALTAの画面が、Schematicタブに変わります．


.. http://alb.anagix.com:8180/myGyazo/data/2233a771ea4af2f6ce9d4b5748ab3f3a.png

.. image:: images/2233a771ea4af2f6ce9d4b5748ab3f3a.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/2233a771ea4af2f6ce9d4b5748ab3f3a.png

続いて、以下のようにLTspice画面が出てくれば成功です。


.. http://alb.anagix.com:8180/myGyazo/data/570d2db10938af973566d431d82c7cab.png

.. image:: images/570d2db10938af973566d431d82c7cab.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/570d2db10938af973566d431d82c7cab.png

Runボタン（人が走っているアイコン）をクリックするとシミュレータが走ります。


.. http://alb.anagix.com:8180/myGyazo/data/74fe656282d9f07d09a225b7ca451844.png

.. image:: images/74fe656282d9f07d09a225b7ca451844.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/74fe656282d9f07d09a225b7ca451844.png

回路やシミュレーション条件を編集してセーブし、LTspiceを終了すると、ALB上のデータベースが更新されます。
（ALTA sampleには一般ユーザは書き込みはできないので注意してください。）

ローカルPC上の回路データは自動的に削除されますが、ローカルPC上に残すためには、ALTAの上で


Remove job dir.のチェックを外した後で、LTspiceを終了するようにしてください。

以上
