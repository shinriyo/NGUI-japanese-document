========================
5.Lights and Refraction
========================

.. In this example I have simply taken the 2nd Example and changed the widgets to use the Refractive atlas. This atlas is simply a copy of the SciFi atlas with a different material. The material uses a different shader that works with lit objects and supports normal mapping as well as a mask map for refraction and specularity.
このExampleでは、シンプルに2番目のExampleから流用し、 **Refractive atlas** を用いてウィジェットを変更しました。このアトラスは、単に別のマテリアルを使用した ``SciFi Atlas`` のコピーです。マテリアルが点灯しているオブジェクトで動作し、通常のマッピングと同様に屈折とスペキュラのマスクマップをサポートする別のシェーダを使用しています。

.. By default NGUI will not generate normals and tangents for the widgets, but this can be turned on by selecting the UIPanel and enabling the appropriate checkbox, which is exactly what’s done for this example.
デフォルトではNGUIは、法線とウィジェットの接線を生成 **しません** が、これは **UIPanel** を選択し、このExampleでは行われているか正確には適切なチェックボックスを有効にすることで、オンにすることができます。


.. There is only one other notable difference from the first example: the Show and Hide buttons have child objects with Point Lights attached to them which are controlled via additional UIButtonColor scripts attached to the buttons. This makes the buttons light up when the mouse hovers over them.
最初のExampleとは1つだけ他の顕著な違いがあります： **Show** と **Hide** ボタンは、このボタンにアタッチされた追加の **UIButtonColor** スクリプトを介して制御され、それらに接続された **Point Lights** を用いた子オブジェクトを持っています。マウスホバー／オーバーしたときに、ボタンがライトアップされます。

.. That’s it!
こうなります！

.. image:: ../images/example5.jpeg

