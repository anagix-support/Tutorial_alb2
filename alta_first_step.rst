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


.. http://alb.anagix.com:8180/myGyazo/data/d29c4d04a234b7aa5d9c52fd1e53d1b1.png

.. image:: images/d29c4d04a234b7aa5d9c52fd1e53d1b1.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/d29c4d04a234b7aa5d9c52fd1e53d1b1.png

Setupボタンを押すと、以下の画面が表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/f5e60262fe4cc333c67cf5cfebc9dce8.png

.. image:: images/f5e60262fe4cc333c67cf5cfebc9dce8.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/f5e60262fe4cc333c67cf5cfebc9dce8.png

プロジェクトを選択する
-------------------
Choose projectのプルダウンにプロジェクトの一覧が表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/241f7d13b4a08267caa7e164b079da85.png

.. image:: images/241f7d13b4a08267caa7e164b079da85.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/241f7d13b4a08267caa7e164b079da85.png

ALTA sampleを選択すると、ALBタブ画面にかわります。画面の左側に回路、右側にモデルライブラリが表示
されています。


.. http://alb.anagix.com:8180/myGyazo/data/e8a4198286dab9a01ba8820bb7889a06.png

.. image:: images/e8a4198286dab9a01ba8820bb7889a06.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/e8a4198286dab9a01ba8820bb7889a06.png

circuitsから、circuits->opamp->instance0->testbenches と展開すると上図の画面になります。

LTspiceに回路を表示する
---------------------
CMRR(asc)の上でダブルクリックするか、下のCommandsからEditをクリックして
ください。下図のようにALTAの画面が、Schematicタブに変わります．


.. http://alb.anagix.com:8180/myGyazo/data/08faa250d9b9c5950695c03e888fb223.png

.. image:: images/08faa250d9b9c5950695c03e888fb223.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/08faa250d9b9c5950695c03e888fb223.png

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


.. raw:: html

   <input type="checkbox" value="true">Remove job dir.</input>

のチェックを外した後で、LTspiceを終了するようにしてください。

.. raw:: html

   <DIV align="right">以上</DIV>

   <!-- DIV style="text-align: right;" >以上</DIV -->

