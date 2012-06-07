=============
1.UIAnchor
=============

.. This example shows one of NGUI’s most important scripts — UIAnchor. In its simplest form, this script can be used to automatically position the game object it’s attached to. There are several uses for this script:

このExampleは、NGUIの一番重要なスクリプトの一つ「UIAnchor」です。シンプルなフォームで、このスクリプトは、それに接続されたゲームオブジェクトを自動的に配置するのに使用します。このスクリプトにはいくつかの用途があります：

.. The main window is anchored to the center, with UIAnchor ofsetting it correctly by half a pixel to make the UI look scrisp on Windows machines.
1. このメインウィンドウは、Windowsマシン上のUIのようなscrisp [#f1]_ を作る半分のピクセルによりそれを正しくUIAnchorのオフセット [#f2]_ を用いている中央に固定されているアンカーです*。

.. rubric:: 脚注

.. [#f1] 【訳注】原文のofsettingはoffsettingだと思います。
.. [#f2] 【訳注】原文のscrispは不明

.. Each one of the 8 buttons is anchored to the side or corner of the screen. They will stay in their respective spots even if the screen aspect ratio changes*.
2. 8つのボタンが1つずつスクリーンの端や角に配置されています。それらのそれぞれの場所の中で、画面のアスペクト比が変更する場合でもご利用いただけます※。

.. UIRoot script is also used in this example.  When attached to the root object of the UI, it will scale that object by the inverse of the screen’s height, thus maintaining a 1 pixel = 1 unit ratio, ensuring pixel-perfect UIs. You can also use UIRoot to position objects based on the relative coordinates, where a value of 0 means no movement, a value of 0.25 means +25% of the width or height (depending on whether it’s X or Y), etc.
**UIRoot** スクリプトもこのExampleで使用されています。UIRootオブジェクトにアタッチすると、それは、このようにpixel-perfectなUIを確保し、1ピクセル = 1を維持し、画面の高さの逆数でそのオブジェクトをスケーリングします。0の値は動きが無いことで、0.25の値は、幅か高さの+25％を意味する（それがXかYかに応じて）、など、相対座標に基づくオブジェクトの位置にUIRootを使用することもできます。

.. UIStretch script is also used, attached to the background tiled sprite. This script is capable of stretching the widget relative to the size of the screen.
**UIStretch** スクリプトもTIledSpriteにの背景にアタッチされて使用されています。このスクリプトはスクリーンのサイズにあわせてウィジットを引き伸ばすことが出来ます。

※Unityの現在の動作は、ゲームウィンドウの寸法を変更すると、編集モードでは、スクリプト上のアップデートをトリガしないことにご注意下さい。つまり、何か変更したりPlayを単に押す（または[Ctrl] + [S]キーを単に2回押す）までUIが正しく更新されません。Playモードのとき、すべてが期待どおりに動作します。

.. image:: ../images/ex0.jpeg
