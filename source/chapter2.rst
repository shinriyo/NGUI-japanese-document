================
2.Interaction
================

.. This example shows that your UI can easily be a part of your 3D scene. Since NGUI simply generates meshes for you, you can position them in your scene freely.
このExmapleは3DシーンのUIを簡単にしてくれるのを示します。
NGUIは簡単にメッシュを生成してくれるので、シーン上に自由に配置できます。

.. You can create signs, interactable in-game HUD windows, dynamic effects such as Scrolling Combat Text from World of Warcraft, and just about anything else you can think of.
HUDウィンドウベースのゲームでインタラクティブ、このようなWorld of Warcraftのからスクロールコンバットテキストなどの動的な効果を、考えられるものは何でも作成することができます。

.. When it comes to interaction, you will find NGUI’s event system to be extremely flexible, with only two conditions:
それは相互作用に来るとき、NGUIのイベントシステムは2つだけの条件で、非常に柔軟であることがわかります。

.. The camera that sees your object must have a UICamera script attached.
1.このカメラは **UICamera** スクリプトが添付されているオブジェクトだけ見ることが出来ます。

2.このオブジェクトがコライダーを持っている必要があります。ウィジェットであるため必要はありません。どんなゲーム内のオブジェクトでも動作します。

.. There are a variety of scripts under the Component/NGUI/Interaction menu that you can use:
使用できる **Component/NGUI/Interaction** のメニューに様々なスクリプトがあります：

.. For example in order to create an object that changes color on touch or mouse over, you can simply attach UIButtonColor script to its collider and specify what object it should be working with.
 例えば、Exampleを引き継ぐタッチまたはマウスで色を変更するオブジェクトを作成するためには、単純にその衝突にUIButtonColorスクリプトを添付することができ、それが作業すべきかのオブジェクトを指定します。

.. It doesn’t need to be a widget either — if you specify an object with a renderer or a light as its target, and it will also work just fine.
これはウィジェットである必要もありません—レンダラや、そのターゲットとしてライトを持つオブジェクトを指定した場合も、うまく動作するでしょう。

.. Want the object to grow slightly?
オブジェクトをわずかに成長したいですか？

.. UIButtonScale. Move? UIButtonOffset. You can activate remote disabled Tween components by using UIButtonTween.
UIButtonScale。動きますか？ UIButtonOffsetです。UIButtonTweenを使用して、リモートのdisabledのTweenコンポーネントをアクティブにすることができます。

.. You can even make it possible to drag an object around by attaching UIDragObject script to the collider and specifying what it should be dragging.
それが可能なコライダーにUIDragObjectスクリプトを添付し、それをドラッグすべきかを指定することによって、周りのオブジェクトをドラッグすることさえもできます。

.. You can look at Example 7 to see how this script was used to make an interactable scroll list.
このスクリプトはinteractableスクロールリストを作成するために使用された方法を確認するためにExample7で見ることができます。

.. But in this example we stick to the basics: the buttons trigger a remote tween animation on the cubes and the window, making its position change.
しかし、このExampleでは、基本線でいきます：このボタンは、その位置変更を行う、キューブとウィンドウ上のリモートのトゥイーンアニメーションをトリガします。

.. When it comes to creating your custom event scripts, NGUI makes it as simple as possible. 
それは、カスタムイベントスクリプトを作成時に、NGUIは出来るだけ簡単にしてくれます。

.. Simply create a MonoBehaviour that implements one of the functions mentioned on the Event page, and attach it to the collider of your own choice.
単にイベントのページに記載のいずれかの関数を実装しMonoBehaviourを作成し、選択する自身のコライダーを取り付けます。

.. For example the following script will print “Hello World!” to the debugger when you click on a collider that has it attached.
例えば、それがアタッチされているコライダーをクリックしたとき、次のスクリプトはデバッガへ "Hello World！"と表示します。

.. code-block:: python
   :linenos:
   using UnityEngine;
   
   public class ClickEventReciever : MonoBehaviour
   {
       void OnClick ()
       {
           Debug.Log("Hello World");
       }
   }
