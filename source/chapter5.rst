=======================
5.Lights and Refraction
=======================

In this example I have simply taken the 2nd Example and changed the widgets to use the Refractive atlas.
このExampleでは、シンプルに2番目のExampleを取り、Refractiveアトラスを使用してウィジェットを変更しました。

This atlas is simply a copy of the SciFi atlas with a different material.
このアトラスは、単に別の物質とのSciFiアトラスのコピーです。

The material uses a different shader that works with lit objects and supports normal mapping as well as a mask map for refraction and specularity.
マテリアルが点灯しているオブジェクトで動作し、通常のマッピングと同様に屈折とスペキュラのマスクマップをサポートする別のシェーダを使用しています。

By default NGUI will not generate normals and tangents for the widgets, but this can be turned on by selecting the UIPanel and enabling the appropriate checkbox, which is exactly what’s done for this example.
デフォルトではNGUIは、法線とウィジェットの接線を生成しませんが、これはUIPanelを選択し、このExampleでは行われているか正確には適切なチェックボックスを有効にすることで、オンにすることができます。

最初のExampleとは1つだけ他の顕著な違いがあります：

the Show and Hide buttons have child objects with Point Lights attached to them which are controlled via additional UIButtonColor scripts attached to the buttons.
ボタンにアタッチされた追加のUIButtonColorスクリプトを介して制御され、それらに接続されたPoint Lightsを使用して、ShowとHideボタンは子オブジェクトを持っています。

This makes the buttons light up when the mouse hovers over them.
これはボタンがそれらの上にときにマウスを置いた点灯になります。

That’s it!
