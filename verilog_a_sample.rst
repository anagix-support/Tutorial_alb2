.. _verilog_a_sample:
==============================================
初めてのverilog-AとSpectreを使ったシミュレーション
==============================================
（2013.10.24更新 - :ref:`「verilog-Aで記述した回路セルのシミュレーション」<verilog_a_cell>` を追加）

このチュートリアルでは、抵抗をverilog-Aでモデル化し、Spectreを使ってシミュレーションします。verilog-Aを
モデルライブラリの中に作成する方法と、回路セルとして作成する方法の２つの方法があります。

*注意:* Spectreのバージョンが古いと、verilog-Aのシミュレーションはできないようです。例えば、IC5141
に付属するspectre (ver. 5.10.41_USR6.081308 -- 13 Aug 2008)では、Error found by spectre during AHDL read-in.
というエラーになります。最新のMMSIM版のSpectreを使ってください。

抵抗１つの回路を作成する
---------------------
:ref:`ALB最初の一歩<alb_first_step>` で作成した 以下のsimple回路をコピーして、その中の抵抗を verilog-Aのモデルに置き換えます。


.. http://alb.anagix.com:8180/myGyazo/data/77b87b278a06a2db15e1744ca8fb3848.png

.. image:: images/77b87b278a06a2db15e1744ca8fb3848.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/77b87b278a06a2db15e1744ca8fb3848.png

紫色の帯（ページを切り替えるタブを集めています）の中から、Cellsというタブをクリックしてください。


.. http://alb.anagix.com:8180/myGyazo/data/db37e2054ae9152db99db1b686a7b9f3.png

.. image:: images/db37e2054ae9152db99db1b686a7b9f3.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/db37e2054ae9152db99db1b686a7b9f3.png

コピーしたいセルの行の右側にある Copyをクリックします。


.. http://alb.anagix.com:8180/myGyazo/data/17e06ea75f604364fdedbf01582157f4.png

.. image:: images/17e06ea75f604364fdedbf01582157f4.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/17e06ea75f604364fdedbf01582157f4.png

セルに名前をつけます。va sampleにしました。Save します。


.. http://alb.anagix.com:8180/myGyazo/data/0ca325b1d60d6337ff6039107e0b3ebc.png

.. image:: images/0ca325b1d60d6337ff6039107e0b3ebc.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/0ca325b1d60d6337ff6039107e0b3ebc.png

ElementsとNetsが表示されていないのに注目してください。以下に示すように、ネットリストのフォーマットが
Spectreのnativeのものではないからです。Spectreで verilog-Aを使うためには、nativeのフォーマットに
変える必要があります。::

	 simulator lang=spice
	 r1 1 0 10K
	 v1 1 0 10
	 * .dc v1 0 10 0.01
	 * .print dc i(v1)

Edit Cell Implementationを実行し、以下のように Spectre nativeのフォーマットに変えてください。::

     	  r1 (1 0) resistor r=10K
	  v1 (1 0) vsource dc=10

ElementsとNetsが表示されるようになります。


.. http://alb.anagix.com:8180/myGyazo/data/cb7cc84e89f6e808a6abe53a16a0f9a7.png

.. image:: images/cb7cc84e89f6e808a6abe53a16a0f9a7.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/cb7cc84e89f6e808a6abe53a16a0f9a7.png

モデルライブラリを作成する
------------------------

セルのページには、セルの上位の階層である、ライブラリおよびプロジェクトへのリンクが、
< Seijiro Moriyama < testLib のようにプロジェクト、ライブラリ順に表示されています。


.. http://alb.anagix.com:8180/myGyazo/data/f8c888809f6ca86148283216cfc728fc.png

.. image:: images/f8c888809f6ca86148283216cfc728fc.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/f8c888809f6ca86148283216cfc728fc.png

Seijiro Moriyamaをクリックして、プロジェクトのページに移ります。


.. http://alb.anagix.com:8180/myGyazo/data/4459b1ed44577d9c14beee20423e3d72.png

.. image:: images/4459b1ed44577d9c14beee20423e3d72.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/4459b1ed44577d9c14beee20423e3d72.png

New Model Libraryをクリックして、モデルライブラリを作成します。


.. http://alb.anagix.com:8180/myGyazo/data/e5f549ecfea3681b6b75e7ec92eec256.png

.. image:: images/e5f549ecfea3681b6b75e7ec92eec256.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/e5f549ecfea3681b6b75e7ec92eec256.png

verilog-a samplesという名前にしました。Simulatorは、Spectreを選択し、
Create Model Libraryを実行してください。（Simulatorが VerilogAではないことに注意してください。）


.. http://alb.anagix.com:8180/myGyazo/data/7aab5072b255ed4d8fe42dcafd8b0849.png

.. image:: images/7aab5072b255ed4d8fe42dcafd8b0849.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/7aab5072b255ed4d8fe42dcafd8b0849.png

ここで作成したモデルライブラリは、いわば箱です。具体的なシミュレータ（ここではSpectre）に対応
した記述(description)を作成するために New simulator dependent implementationをクリックしてください。


.. http://alb.anagix.com:8180/myGyazo/data/e4b5d38f69e4d0953c02bb4e66f45ca8.png

.. image:: images/e4b5d38f69e4d0953c02bb4e66f45ca8.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/e4b5d38f69e4d0953c02bb4e66f45ca8.png

Descriptionは、以下のようにしましたが、ここで res_va が、これから作成するverilog-Aモデルの名前です。
spectreシミュレーションのために作成されるファイルの名前が res_va.modです。::

	  simulator lang=spectre
	  ahdl_include "res_va.mod"


*注意:* 以下では、verilog-Aモデルをモデルライブラリに作成しますが、回路セルとして作成し、直接シミュレーション
する方法もあります。:ref:`「verilog-Aで記述した回路セルのシミュレーション」<verilog_a_cell>` を参照してください。


抵抗のverilog-aモデルを作成する
-----------------------------

モデルライブラリ（verilog-a samples）の下に、モデルを作成します。


.. http://alb.anagix.com:8180/myGyazo/data/8af48a633b1735e6e728cd62b377e1be.png

.. image:: images/8af48a633b1735e6e728cd62b377e1be.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/8af48a633b1735e6e728cd62b377e1be.png

New Modelをクリックしてください。


.. http://alb.anagix.com:8180/myGyazo/data/b7c1db6c9af650ef92262e18997a373a.png

.. image:: images/b7c1db6c9af650ef92262e18997a373a.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/b7c1db6c9af650ef92262e18997a373a.png

モデル名は、res_va です。Simulatorは、VerilogAではなくSpectreを選択してください。
（これは重要なポイントです。）

Create Modelでモデルが作成されますが、モデルは、いわば箱です。中身は、シミュレータごとに作成する必要が
あります。


.. http://alb.anagix.com:8180/myGyazo/data/c499342722a5d17cd7d1828e57110200.png

.. image:: images/c499342722a5d17cd7d1828e57110200.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/c499342722a5d17cd7d1828e57110200.png

New Model Implementation をクリックして、verilog-Aのモデル記述を作成しましょう。


.. http://alb.anagix.com:8180/myGyazo/data/0b8c55fd23ef6d1f54a6541b4a67182b.png

.. image:: images/0b8c55fd23ef6d1f54a6541b4a67182b.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/0b8c55fd23ef6d1f54a6541b4a67182b.png

verilog-Aのプログラム例を示します::

	`include "discipline.h"
	`include "constants.h"
	
	 module res_va(plus,minus);
	   inout plus, minus;
	   electrical plus,minus,vpm;
	
	    real tempC,tfac,ReffV,Reff;
	    parameter real r=1;
	    parameter real tc1=0;
	    parameter real tc2=0;
	    parameter real vc1=0;
	    parameter real vc2=0;
	
	    analog begin
	
	    tempC = ($temperature-273.15)-25;
	
	    tfac=1+(tc1*tempC)+(tc2*tempC*tempC);
	    V(vpm) <+ V(plus, minus);
	    Reff=r*(1+(vc1*abs(V(vpm)))+(vc2*V(vpm)*V(vpm)))*tfac;
	    V(plus,minus) <+ Reff*I(plus,minus);
	    end
	 endmodule
	
このモデルでは、抵抗の温度依存性と電圧依存性を表現しています。


.. http://alb.anagix.com:8180/myGyazo/data/56e67221d6e89439954f32e642199e63.png

.. image:: images/56e67221d6e89439954f32e642199e63.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/56e67221d6e89439954f32e642199e63.png

モデル記述を修正するには、Edit Model Implementationボタンをクリックしてください。

回路からverilog-aモデルを呼び出す
-----------------------------
モデルのページの先頭に、'< プロジェクト名 < ライブラリ名'という形で、プロジェクトとライブラリへの
リンクが表示されています。プロジェクト（Seijiro Moriyama）をクリックしてプロジェクトに行き、
先に作成した回路（va sample）のページに行きます。


.. http://alb.anagix.com:8180/myGyazo/data/a5ba92f2093f4712eed14f2c1eeb1585.png

.. image:: images/a5ba92f2093f4712eed14f2c1eeb1585.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/a5ba92f2093f4712eed14f2c1eeb1585.png

ライブラリ（testLib）の頭の部分（>>の部分）をクリックすると、以下のようにtestLibの中が
展開して表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/95ecf4abf2e2578c4da38dabdb5a3a0e.png

.. image:: images/95ecf4abf2e2578c4da38dabdb5a3a0e.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/95ecf4abf2e2578c4da38dabdb5a3a0e.png

セル（va sample）をクリックしてください。セルのページが表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/10cc801bd94693116b553478fe2a7bcf.png

.. image:: images/10cc801bd94693116b553478fe2a7bcf.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/10cc801bd94693116b553478fe2a7bcf.png

ネットリストを表示していますが、この中で、抵抗r1のモデルがresistorとなっていることに注目
してください。Edit Cell Implementationボタンをクリックし編集ページ
で、これをres_vaに変更してください。


.. http://alb.anagix.com:8180/myGyazo/data/dc2c568d52677d1ef95ca76ce8947d36.png

.. image:: images/dc2c568d52677d1ef95ca76ce8947d36.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/dc2c568d52677d1ef95ca76ce8947d36.png

つぎに、インスタンス(Instance0）のページで、インスタンスから参照するモデルライブラリを
定義します。Edit instanceをクリックしてください。


.. http://alb.anagix.com:8180/myGyazo/data/535e5413ce544e98e4699b2f5d706eb5.png

.. image:: images/535e5413ce544e98e4699b2f5d706eb5.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/535e5413ce544e98e4699b2f5d706eb5.png

Model Libraryとしてプルダウンの中から、verilog-a samplesを選択し、Saveしてください。


.. http://alb.anagix.com:8180/myGyazo/data/188f0c49f9ca57237c0d3d9d22f8c07f.png

.. image:: images/188f0c49f9ca57237c0d3d9d22f8c07f.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/188f0c49f9ca57237c0d3d9d22f8c07f.png

シミュレーションする
------------------
シミュレーションの実行は、インスタンスのページから行います。


.. http://alb.anagix.com:8180/myGyazo/data/fba7e91d176652a9efa2d60bec0818f7.png

.. image:: images/fba7e91d176652a9efa2d60bec0818f7.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/fba7e91d176652a9efa2d60bec0818f7.png

プロットが存在しますが、このセルのコピー元（simple）のシミュレーション結果であり、まぎらわしいですね。Quick plotボタンの
横のXボタンをクリックして削除してください。


.. http://alb.anagix.com:8180/myGyazo/data/9ccb5829db776d8bb378e34b2dacc42a.png

.. image:: images/9ccb5829db776d8bb378e34b2dacc42a.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/9ccb5829db776d8bb378e34b2dacc42a.png

このままでは、下図に示すように、テストベンチ（tb）の行の右側に、Simulateがないため、
シミュレーションを起動できません。


.. http://alb.anagix.com:8180/myGyazo/data/1067f407ccad5195a9285ba6c0e49f95.png

.. image:: images/1067f407ccad5195a9285ba6c0e49f95.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/1067f407ccad5195a9285ba6c0e49f95.png

一度、Edit Instanceでインスタンス編集のページに行き、そのまま Saveしてください。もちろん
シミュレーションの目的などを Descriptionや詳細をBodyに書き込んでも構いません。


.. http://alb.anagix.com:8180/myGyazo/data/3d569301133323ef7bc170511629825a.png

.. image:: images/3d569301133323ef7bc170511629825a.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/3d569301133323ef7bc170511629825a.png

Simulateをクリックしてください。Status表示がstartingに変わります。Update status
を（何度か）クリックするとstatusがcompletedに変わります。また、Quick plotボタンが現れます
ので、クリックしてみましょう。


.. http://alb.anagix.com:8180/myGyazo/data/95c49e5a3315258c58eef78e2f7d53a0.png

.. image:: images/95c49e5a3315258c58eef78e2f7d53a0.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/95c49e5a3315258c58eef78e2f7d53a0.png

抵抗値10Kの抵抗の電流ー電圧特性が得られます。

温度をパラメータに変えてシミュレーションする
---------------------------------------

温度を変えるとどのように特性が変化するか調べ、常温の結果と比較しましょう。

温度をあらわすパラメータとして、@tempという変数名を使うことにします。Edit instanceをクリックして
インスタンスの編集画面に行きます。


.. http://alb.anagix.com:8180/myGyazo/data/010b5913b6b405e605c4c2e779c4b3df.png

.. image:: images/010b5913b6b405e605c4c2e779c4b3df.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/010b5913b6b405e605c4c2e779c4b3df.png

Parametersに、@temp=120 を設定しました。

次に、インスタンスのページでテストベンチ（tb）の右側のEditをクリックして、
Edit Testbench Implementationページに行ってください。


.. http://alb.anagix.com:8180/myGyazo/data/41f3f846b35ad1bcbc6b685c6dd89ecf.png

.. image:: images/41f3f846b35ad1bcbc6b685c6dd89ecf.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/41f3f846b35ad1bcbc6b685c6dd89ecf.png


このように、::
	.options temp=#{@temp}

を書き加えて、Saveします。

回路（va sample）の記述も変更する必要があります。va sampleのリンクをクリックして、
セルのページに行き、Edit Cell Implementationボタンをクリックしてください。


.. http://alb.anagix.com:8180/myGyazo/data/10104fefe2ba0cb60f87b2f4361db07e.png

.. image:: images/10104fefe2ba0cb60f87b2f4361db07e.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/10104fefe2ba0cb60f87b2f4361db07e.png

r1の記述に、tc1=0.001が加わっています。Saveし、インスタンス（Instance0）のページに
戻り、Simulateを実行してください。


.. http://alb.anagix.com:8180/myGyazo/data/5c16afc2bbc28e2b05beb8b72d544387.png

.. image:: images/5c16afc2bbc28e2b05beb8b72d544387.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/5c16afc2bbc28e2b05beb8b72d544387.png

これまでの設定に誤りが無ければ、上図のように２つのプロット（tbとtb@temp=120）が表示されます。

シミュレーションにエラーがあった場合、エラーの内容は、テストベンチ（tb）の行の右側にある
Logをクリックすると表示されます。また、ネットリストは Netlistで確認できます。

結果を比較する
-------------

結果を比較するのに簡単な方法は、プロットを重ねる方法です。しかし、
パラメータ（ここでは@temp）を使用すると、実行結果は、パラメータを使用しないときとは
別のプロットになります。

そこで、重ねてプロットしたいPlotをMarkし、別のプロットの上に Overlayする方法があります。

重ねたい方（この場合、tb）の行の右側で Markをクリックしてください。次に、重ねられる側
（この場合、tb@temp=120）の行の右側で Overlayをクリックしてください。以下のように
tb@temp=120のカーブの上に、tbのカーブを重ねたプロットが得られます。


.. http://alb.anagix.com:8180/myGyazo/data/4588096780a522ef2b3eb1dc4c126322.png

.. image:: images/4588096780a522ef2b3eb1dc4c126322.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/4588096780a522ef2b3eb1dc4c126322.png

青色が、常温、緑色が、１２０度のカーブです。このMarkとOverlayを使ったやりかたは、別の
回路のシミュレーション結果を重ね合わせる場合にも有効です。

.. _verilog_a_cell:

verilog-Aで記述した回路セルのシミュレーション
----------------------------------------
前節まででは、モデルライブラリのなかにverilog-Aモデルを作成しました。

回路セルをverilog-Aで記述してシミュレーションすることもできます。

まず、Examplesライブラリに、res_va というCellを作成します。


.. http://alb.anagix.com:8180/myGyazo/data/d65c49ddd0ac4b4845ad103a655836b9.png

.. image:: images/d65c49ddd0ac4b4845ad103a655836b9.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/d65c49ddd0ac4b4845ad103a655836b9.png

Simulatorは、Cell implementation をこれから作成するので、まだ表示されていませんが、Cellを
作成する際にVerilogAを選択しています。

Cell implementationを作成します。モデルの中身は、前述の res_vaモデルと同じです。


.. http://alb.anagix.com:8180/myGyazo/data/1c89c6312ebf3ce58f5b8660419df252.png

.. image:: images/1c89c6312ebf3ce58f5b8660419df252.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/1c89c6312ebf3ce58f5b8660419df252.png

シミュレーションのために Instanceを作成します。direct_simという名前を付けました。


.. http://alb.anagix.com:8180/myGyazo/data/cb651d453cc19ca140ded39ccc28048c.png

.. image:: images/cb651d453cc19ca140ded39ccc28048c.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/cb651d453cc19ca140ded39ccc28048c.png

続いてテストベンチ（Instant testbench）を作成します。ネットリストの内容は、前述の va_sampleというセルと同じです。
ここでは va_testbenchという名前にしました。Simulatorは、Spectreです。ControlとPostprocessは、前述の
テストベンチ（tb） と同じものを使っています。


.. http://alb.anagix.com:8180/myGyazo/data/b22c6ffbe4a90f4a9566ecab1f9aa608.png

.. image:: images/b22c6ffbe4a90f4a9566ecab1f9aa608.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/b22c6ffbe4a90f4a9566ecab1f9aa608.png

テストベンチに View Settingsを作成します。tbのものと同じ内容で作成します。


.. http://alb.anagix.com:8180/myGyazo/data/52235c808fe08ed2863d64236c141faa.png

.. image:: images/52235c808fe08ed2863d64236c141faa.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/52235c808fe08ed2863d64236c141faa.png


以上で準備完了です。


.. http://alb.anagix.com:8180/myGyazo/data/2a80260a8a974cdd47e6aeb24fd7dffc.png

.. image:: images/2a80260a8a974cdd47e6aeb24fd7dffc.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/2a80260a8a974cdd47e6aeb24fd7dffc.png

Instanceにもどってシミュレーションを実行してください。

ALTAを使ってローカルマシーンでシミュレーションする
--------------------------------------------

別のチュートリアル（:ref:`ALTAを使ったローカルマシーンでのシミュレーション<alta_simulation>` ）に詳述したように、ローカルの
LinuxマシーンにSpectreが入っていれば、ALTA上でシミュレーションしたり、ALBからALTAを介してSpectreを実行する
ことができます。

まずLinuxマシーン上のALTAを起動しログインします。そして今回の
プロジェクト（Seijiro Moriyama）を開いてください。


.. http://alb.anagix.com:8180/myGyazo/data/b028ea0a0d3beb05cc4ee55526224bf0.png

.. image:: images/b028ea0a0d3beb05cc4ee55526224bf0.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/b028ea0a0d3beb05cc4ee55526224bf0.png

tb(Spectre)を選択して、Simulateボタンをクリックすると、Simulation Tabに切り替わります。


.. http://alb.anagix.com:8180/myGyazo/data/b1dd202a86057c2772ef3cb66fca6982.png

.. image:: images/b1dd202a86057c2772ef3cb66fca6982.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/b1dd202a86057c2772ef3cb66fca6982.png

Simulate nowボタンをクリックするとSpectreが走ります。成功すれば以下のようなフォームが表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/1b6bcb8e0a01e973364088f8410813c7.png

.. image:: images/1b6bcb8e0a01e973364088f8410813c7.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/1b6bcb8e0a01e973364088f8410813c7.png

Plotボタンをクリックすると以下のようなグラフが表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/c1eab0c89b4c5b8e2a214fe0eff8b2e4.png

.. image:: images/c1eab0c89b4c5b8e2a214fe0eff8b2e4.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/c1eab0c89b4c5b8e2a214fe0eff8b2e4.png

このグラフでは、Y軸の電流がマイナスなのですが、Settingsを変更することで、逆にすることができます。


.. http://alb.anagix.com:8180/myGyazo/data/51c963ebe80b68dcd06895125443075f.png

.. image:: images/51c963ebe80b68dcd06895125443075f.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/51c963ebe80b68dcd06895125443075f.png

この例では、電流値を -1000 倍して、符号を変えるとともに、電流の単位を mAにしています。また、
Y軸の表示を、0から、10mAまで、1mAきざみに変更しています。OKをクリックすると以下のグラフ表示に変わります。


.. http://alb.anagix.com:8180/myGyazo/data/212633c6aea172a3c873ddb6bc4e4e14.png

.. image:: images/212633c6aea172a3c873ddb6bc4e4e14.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/212633c6aea172a3c873ddb6bc4e4e14.png

Upload nowボタンをクリックするとこの結果がALBに送られます。

*注意:* 次の節のALBからのALTAを介したSpectre実行のために、Simulation Tabの Start automaticallyの
チェックが外れているのでチェックを入れてください。このチェックが入っていないと、ALBからAltaコマンドを
実行しても、Simulation Tabが表示された状態で留まり、シミュレーションに入らないので注意してください。

ALBからALTAを介してSpectreを実行する
---------------------------------

ALBのインスタンスの画面に戻ります。


.. http://alb.anagix.com:8180/myGyazo/data/27d0dbe0dd638048107d426009a2a216.png

.. image:: images/27d0dbe0dd638048107d426009a2a216.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/27d0dbe0dd638048107d426009a2a216.png

上図のようにParametersに、@temp=-40 を設定してください。


.. http://alb.anagix.com:8180/myGyazo/data/d020a2f19d341191a7459fd22dbbc468.png

.. image:: images/d020a2f19d341191a7459fd22dbbc468.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/d020a2f19d341191a7459fd22dbbc468.png

Testbenchの行の右側に表示されたコマンドの中から、Altaを実行すると、ALTAに回路データが
送られ、Spectreが実行され、結果がALBに戻ります。ALTAの画面が、Simulation Tabから
ALBブラウザーTabに切り替わりますので、シミュレーションが終了したことがわかります。

Update statusをクリックするとStatusがcompletedに変わます。また、下図のように、temp@=-40
のグラフが作成されます。


.. http://alb.anagix.com:8180/myGyazo/data/965ac7a15b2ef990804309a7a99b4ac6.png

.. image:: images/965ac7a15b2ef990804309a7a99b4ac6.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/965ac7a15b2ef990804309a7a99b4ac6.png

このように、ALBサーバでAltaコマンドを実行すると、ALTAを介してSpectreを実行することができ、
ALBサーバでシミュレータを実行したのと同じ結果を得ることができます。

ALBサーバでは、Spectreを実行できないが、ローカルのALTA上でSpectreを
実行できる場合に有効です。また、長時間のシミュレーションの場合、ALBサーバで実行させることは
好ましくないので、この方法をお試しください。

.. raw:: html

   <DIV align="right">以上</DIV>

   <!-- DIV style="text-align: right;" >以上</DIV -->


