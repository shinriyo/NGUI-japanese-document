8.Scroll View（2番目のカメラ）

This example shows how you can create a scroll view by simply having a secondary camera that draws to a part of the screen.
このExampleでは、単純に画面の一部に描画し、セカンダリカメラを持っていることによってスクロールビューを作成する方法を示しています。

This is the ideal approach of handling scroll views in a 2D UI because it’s very fast and doesn’t involve the use of shaders, making it suitable for older devices such as iPhone 1, 2, and 3G. It does, however have two fairly important drawbacks:
これは非常に高速なので、2DのUIでスクロールビューを処理するのに理想的なアプローチであり、iPhoneなど1、2、3Gなどの古い機器に適して、シェーダの使用が含まれていません。それは、しかし、2つの非常に重要な欠点を持っていません：

It’s limited to 2D.

It can’t be rotated or moved off-screen. If you want to do that, you should fade out the scroll view’s contents first.
それが回転またはオフスクリーンに移動することはできません。それを行いたい場合は、まず、スクロールビューの内容をフェードアウトする必要があります。

If you are fine with these limitations, you can get this list working anywhere.
これらの制限と問題がない場合は、このリストには、どこでも動かすことができるでしょう。

If you want something more… then your best bet is to stick with the previous example that shows how to implement the same scroll view system via UIPanel’s Clipping instead.
もっと何かしたい場合は...そしてあなたの最善の策ではなく、Uipanelののクリッピングを介して同じスクロールビューシステムを実装する方法を示しています。前のExmapleに固執することです。

But… I digress. Back to how this example works.
しかし...私は脇に逸れる。このExampleでは、どのように動作するかにバックアップします。

In this list there are two cameras. The main camera takes care of drawing the main window and has a pair of game objects specifying the top-left and bottom-right corners of the scroll view.
このリストでは、2つのカメラがあります。メインカメラは、メインウィンドウの描画の世話をスクロールビューの左上と右下のコーナーを指定して、ゲームオブジェクトのペアを持っています。

The second camera is positioned off-screen and draws another piece of the UI — the items inside the scroll list.
2番目のカメラは、オフスクリーンに位置し、UI（このアイテムはスクロールのリストの中に入ってます）の別の部分を描画しています。

With UIViewport script conveniently handling all the math behind the steps necessary to drawing to the part of the screen specified by the two game objects, all that’s missing is the ability to move the scroll view items with the mouse.
UIViewportスクリプトは便利な2つのゲームオブジェクトで指定された画面の一部に描画するために必要な手順の背後にあるすべての数学を扱うと、欠けている、すべてのマウスでスクロールビューの項目を移動する機能です。

This is accomplished by actually moving the camera instead via the UIDragCamera script attached to colliders in the scene (background, items).
これは実際には、シーン内のコライダー（背景、アイテム）に接続されているUIDragCameraスクリプト経由ではなくカメラを移動することによって達成されます。

This script points to a UIDraggableCamera script attached to the secondary camera, and on that script you can specify the Root to consider for widget bounds as well as the Scale that limits movement (in this case X of 1 means full movement on X and 0 = no movement on the Y axis).
このスクリプトは、2Dカメラに取り付けUIDraggableCameraスクリプトを指して、そのスクリプトでは、ウィジェットの境界のために考慮するルートと同様の動きを（1、この場合Xの制限スケールを指定することができ、Xと0 =上の完全な移動を意味しますY軸には動きません）。

You can also specify the effect to use, and the amount of momentum applied when you release the touch.
また、使用するエフェクトを指定することができます、あなたはタッチを離すと勢いの量が適用されます。

All in all, this is a much smaller script than UIDraggablePanel, and as such it has less functionality.
すべてのすべてで、これはUIDraggablePanelよりもはるかに小さいスクリプトであり、そういうものとして、それは以下の機能を備えています。

On the bright side, less code means easier to modify, if you happen to need something more.
明るい側では、未満ののコードでは、あなたがより多くの何かを必要とする起こる場合には、変更するには、容易になりことを意味します。


