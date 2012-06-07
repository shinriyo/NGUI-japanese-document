================================
8.Scroll View（2番目のカメラ）
================================

.. This example shows how you can create a scroll view by simply having a secondary camera that draws to a part of the screen. This is the ideal approach of handling scroll views in a 2D UI because it’s very fast and doesn’t involve the use of shaders, making it suitable for older devices such as iPhone 1, 2, and 3G. It does, however have two fairly important drawbacks:
このExampleでは、単純に画面の一部に描画し、2番目のカメラを持っていることによってスクロールビューを作成する方法を示しています。これは非常に高速で、シェーダの使用が含まれていませんので、2DのUIでスクロールビューを処理するのに理想的なアプローチであり、iPhone 1、2、3Gなどの古い機器に適しています。しかし、非常に重大な2つの欠点があります：

.. It’s limited to 2D.
1. 2Dに限定されています。

.. It can’t be rotated or moved off-screen. If you want to do that, you should fade out the scroll view’s contents first. If you are fine with these limitations, you can get this list working anywhere.
2. 回転させたりオフスクリーンに移動することはできません。それを行いたい場合は、まず最初に、スクロールビューの内容をフェードアウトする必要があります。これらの制限と問題がない場合は、このリストを、どこへでも動かすことができるでしょう。

.. If you want something more… then your best bet is to stick with the previous example that shows how to implement the same scroll view system via UIPanel’s Clipping instead. But… I digress. Back to how this example works.
もっと何かしたい場合は...そしてあなたの最善の策ではなく、 **UIPanel’s Clipping** を介して同じスクロールビューシステムを実装する方法を示しています。前のExmapleに固執することです。しかし...本筋を離れます。どのようにExample動作するかに戻りましょう。

.. In this list there are two cameras. The main camera takes care of drawing the main window and has a pair of game objects specifying the top-left and bottom-right corners of the scroll view. The second camera is positioned off-screen and draws another piece of the UI — the items inside the scroll list.
このリストでは、2つのカメラがあります。 **Main Camera** は、メインウィンドウの描画の世話をスクロールビューの左上と右下のコーナーを指定しているゲームオブジェクトのペアがありまます。2番目のカメラは、オフスクリーンに位置し、UI（このアイテムはスクロールのリストの中にある）の別の部分を描画しています。

.. With UIViewport script conveniently handling all the math behind the steps necessary to drawing to the part of the screen specified by the two game objects, all that’s missing is the ability to move the scroll view items with the mouse. This is accomplished by actually moving the camera instead via the UIDragCamera script attached to colliders in the scene (background, items).  This script points to a UIDraggableCamera script attached to the secondary camera, and on that script you can specify the Root to consider for widget bounds as well as the Scale that limits movement (in this case X of 1 means full movement on X and 0 = no movement on the Y axis). You can also specify the effect to use, and the amount of momentum applied when you release the touch.
**UIViewport** スクリプトは便利な2つのゲームオブジェクトで指定された画面の一部に描画するために必要な手順の背後にあるすべての数学を扱うと、欠けている、すべてのマウスでスクロールビューの項目を移動する機能です。これは実際には、シーン内のコライダー（背景、アイテム）に接続されている **UIDragCamera** スクリプト経由ではなくカメラを移動することで実現しています。このスクリプトは、2番目のカメラに取り付け **UIDraggableCamera** スクリプトを示し、そのスクリプト上ではウィジェットの境界のために考慮する **Root** と同様の動きを **Scale** で指定することができます（この場合、 ``X`` が ``1`` のときはX上での完全な動作、 ``0 =`` はY軸で動かないことを意味します）。また、使用するエフェクトを指定することができます、タッチを離すと運動量が適用されます。

.. All in all, this is a much smaller script than UIDraggablePanel, and as such it has less functionality. On the bright side, less code means easier to modify, if you happen to need something more.
概していえば、これは **UIDraggablePanel** よりもはるかに小さいスクリプトであり、そういうものとしてより少ない機能を備えています。明るい面では、より少ないコードは、何か起こったときに変更が容易であることを意味します。

.. image:: ../images/example2.jpeg
