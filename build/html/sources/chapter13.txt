========================================================================
13.Character Inventory　※アセットの中のシーンは13ではなくXです。
========================================================================

.. Let me begin by saying that this is the most complicated example bundled within the NGUI’s package, but not because of the UI. This example actually features a fairly advanced random item generation system that uses user-specified items to generate alternate versions of those items with a random level and quality setting.
このため、UIのNGUIのパッケージにバンドルされた最も複雑なExampleですが、UIがないということから始めましょう。このExampleでは、実際にランダムなレベルと品質の設定で、これらのアイテムの代替バージョンを生成するためにユーザーが指定したアイテムを使用して、かなり高度なランダムアイテム生成システムを備えています。

.. Please note that this is a bonus example that comes with NGUI. If you are not interested in implementing an inventory system for your game, you can safely skip it as the majority of what’s involved is not UI-related at all.
これはNGUIに付属している **bonus** のExampleであることに注意してください。ゲームのために在庫管理システムの実装に興味を持っていない場合、安全にどのように関与していると、すべてでは、UIに関連していない大多数のようにそれをスキップすることができます。

.. The purpose of this example was to explore how NGUI could be integrated with another advanced system. As such, this example features a large number of custom scripts that all begin with the “Inv” prefix, such as “InvEquipment“, “InvBaseItem“, “InvTools“, etc. Conveniently for you, all of the custom scripts can be found in a single location: inside the InventorySystem folder.
このExampleの目的は、NGUIが他の先進的なシステムと統合する方法を探ることでした。このように、このExampleでは、 **“InvEquipment“** 、 **“InvBaseItem“** 、 **“InvTools“** など、などのプレフィックス **“INV“** で始まるしたカスタムスクリプトの多くを備えています。便利な、カスタムスクリプトのすべてが単一の場所で見つけることができます： **InventorySystem** フォルダ内です。

.. image:: ../images/invdatabase.jpg

.. Still reading? Alright. Let’s start with how the items are created: InvDatabase.Select the ItemDatabase game object.
まだ読んでいますか？大丈夫ですね。このアイテムが作成された方法から始めましょう： **InvDatabase** 。 **ItemDatabase** ゲームのオブジェクトの選択です。

.. This is where all the items used by this example are created and stored. As you can see you are presented with a custom inspector tool that lets you navigate and edit items.
このExampleで使用されるすべてのアイテムが作成および格納される場所です。見ることができるとして、アイテムを移動して編集することができますカスタムインスペクタツールが表示されます。

.. You can press Alt+Shift+i at any time to find objects by name (or go via the Inventory menu up top).
**[Alt] + [Shift] + [i]** キーを押すことでいつでも名前でオブジェクトを発見できます（またはトップアップインベントリメニューを経由して）。

.. All item stats are entered as if they were of max level. This lets you easily compare items one to another to see which one is supposed to be better. Keep in mind, you are not creating in-game items here. You are merely creating item templates that will be used to generate actual items. When the system generates Game Items, they will be created within the item level range specified on your template and will be given a random quality level.
それらが最大レベルであったかのようにすべてのアイテムの統計情報が入力されます。これは、簡単にあるアイテムと別のアイテムがどちらがベターなのかを推測して比較できます。念頭に置いて、ここでゲーム内アイテムを作成していません。単に実際のアイテムを生成するために使用されるアイテムのテンプレートを作成しています。システムは **Game Items** を生成するとき、それらはテンプレートで指定されたアイテムレベルの範囲内で作成され、ランダムな品質レベルが与えられます。

.. Final game item stats are calculated by taking the template’s stats and mixing it with the item’s level, adjusted by the item’s quality.
最後のゲームアイテムの統計情報は、テンプレートの統計を取って、アイテムの質によって調整されたアイテムのレベルでそれを混合することによって計算されます。

.. Before moving on to the next component, note the Slot field here. Each item can go into a certain slot. When equipping items later, the prefab specified by the Attachment field will be instantiated for every single slot on the character that matches this field. This is why you see two bracers, two shoulderpads, and two boots although only one attachment game object has been specified.
次のコンポーネントに移動する前に、ここにある **Slot** フィールドに注意してください。各アイテムは、特定のスロットに行くことができます。後でアイテムを装備する場合は、 **Attachment** フィールドで指定されたプレハブは、このフィールドに一致するキャラクター1人1人のスロット用にインスタンス化されます。こういうわけで、2つの腕甲、2つのショルダーパッド、2つのブーツが1つのゲームオブジェクトにアタッチされているだけで定義されているのをご覧下さい。

.. Search for “Attachment” in the Hierarchy view to see where those points are on the character. And yes, I had to eyeball them when positioning them. Note the InvAttachmentPoint script on those game objects. All equipped items get instantiated and attached as children of these game objects.
これらの点は、キャラクター上にある場所を確認するためにはHierarchyビューで **“Attachment”** を検索してください。それらを配置するときに、はい、眼球、それらをしました。これらのゲームオブジェクトに **InvAttachmentPoint** スクリプトに注意してください。すべての装備アイテムがインスタンス化され、これらのゲームオブジェクトの子としてアタッチされています。

.. image:: ../images/invhierarchy.jpg

.. If you examine the actual hierarchy of the scene you will notice that there are 3 root game objects: one for the 2D UI, one for the 3D UI, and one for the Scene itself.
シーンの実際の階層構造を調べる場合、 **2D UI** が1つ、 **3D UI** が1つであり、 **Scene** 自体のいずれか、3つのルートのゲームオブジェクトがあることに気付くでしょう。

.. If you hit Alt+Shift+P to bring up the Panel Tool you will also notice that each one of those root nodes has a UIPanelattached.
パネルツールを起動するには **[Alt] + [Shift] + [P]** を押してあれば、また、それらのルートノードのそれぞれが **UIPanel** がアタッチされていることに気づくでしょう。

.. 2D UI is used for the Tooltip, as I wanted it to look crisp and clear on the screen.
- **2D UI** は、それが画面上に鮮明な見ていたように、 **Tooltip** に使用されます。

.. 3D UI is used to draw all the UI elements you see: buttons, item slots, items, backpack.
- **3D UI** は見るすべてのUI要素を描画するために使用されます：ボタン、アイテムスロット、アイテム、バックパック。
.. Scene is where the character is located, but it also contains the widget used to draw the background.
- **Scene** 内にキャラクターが配置されているが、それはまた、 **background** を描画するために使われるウィジェットを含んでいます。

.. Let’s start with the Tooltip. If you select it in the hierarchy you will notice that it has a UITooltip script attached.
**Tooltip** で始めてみましょう。hierarchy内でそれを選択した場合は、それが添付され **UITooltip** スクリプトを持っているnotthatます。

.. This custom script is used to create tooltips for items that you specify. All it needs to know is the camera that will be used to draw it so it can position itself properly, the text label to fill with text, and the background sprite to resize so that it envelops the text. If “Scaling Transitions” is enabled, the tooltip will be shown via a mix of scaling and color adjustments, making it “swoop in”. The way this script is used via code is simple: UITooltip.ShowItem(<game item>);
このカスタムスクリプトは、指定したアイテムのツールチップを作成するために使用されます。それは知っている必要がありますすべては、それがテキストを包み込むようにサイズを変更するにはテキストを埋めるために、適切に **texg** ラベルを自分自身を配置することができますので、それを描画するために使用されるカメラ、背景スプライトです。“ ``Scaling Transitions`` ”が有効になっている場合は、ツールチップは、それ“ ``swoop in`` ”を作る、スケーリング、色調整の組み合わせを介して表示されます。このスクリプトはコードを介して使用されている方法は単純です： **UITooltip.ShowItem(<gameアイテム>);**

.. Moving on to the 3D UI, you may notice a disabled Storage Icon Template, and chances are you have already noticed that the actual backpack widgets are nowhere to be found while in the editor. That’s because the backpack gets created dynamically via a script on the Backpack game object — UIItemStorage.
**3D UI** に移るには、無効な **Storage Icon Template** が表示されることがあり、すでに、実際のバックパックのウィジェットは、エディタ中にどこにも見つからないことをチャンスに気づいたされています。  **UIItemStorage** - **Backpack** ゲームオブジェクトのスクリプトを介して動的に作成されるためです。

.. By selecting that game object and examining the script, you will notice that you can specify the maximum number of items, rows, and columns in addition to the template game object it will use to create the backpack’s cells. Now, it’s not limited to being a backpack — Item Storage can be anything — a store item list, a chest in the game, a vault… even another player’s inventory. In addition to the creation of the backpack, this script has several useful functions you can use in your code:
そのゲームのオブジェクトを選択し、スクリプトを調べることによって、あなたはそれがバックパックのセルを作成するために使用するテンプレートのゲームオブジェクトに加えて、アイテム、行、列の最大数を指定することができていることがわかります。今、それはバックパックに限らずです - ItemStorageは、何でもできます - アイテムリストのストアは、ゲーム内のチェスト、金庫も...他のプレイヤーの在庫もです。バックパックの作成に加えて、このスクリプトはいくつかの有用な機能を持っています。 コード内で使用することができます。

.. UIItemStorage.GetItem(slot) gives you the item in the specified slot, or ‘null’ if none.
- **UIItemStorage.GetItem(スロット)** を使用すると、指定したスロット内のアイテム、またはない場合、 **’null’** を示します。

.. UIItemStorage.Replace(slot, game item) lets you replace an item at the specified slot with another one, returning the item it replaced.
- **UIItemStorage.Replace(スロット、ゲームアイテム)** を使用すると、それが置き換えられたアイテムを返し、別のいずれかで指定されたスロットにアイテムを置き換えることができます。

.. If you want to remove an item from the container, simply pass ‘null’ as the second parameter. You can destroy the returned item to effectively get rid of it altogether.
- コンテナからアイテムを削除したい場合は、単に2番目のパラメータとして **‘null‘** を渡します。あなたが効果的に完全にそれを取り除くために戻されたアイテムを破棄することができます。

.. Of course you also can always see what’s in the item container by accessing UIItemStorage.items.
- もちろん、常に **UIItemStorage.items** にアクセスすることによって、アイテムのコンテナ内に何があるかを見ることができます。

.. If you select the disabled Storage Icon Template object, you will notice UIStorageSlot script attached to it, which works with the UIItemStorage class. It’s what allows you to pick up items and notify the storage class that the item has been removed. The script itself is short, but only because it’s derived from UIItemSlot — a generalized script that’s also used by UIEquipmentSlot — the script on the 3 inventory icons. In short, all these scripts allow you to do is move items from their respective containers.
``disabled`` になっている **Storage Icon Template** を選択した場合には、 **UIItemStorage** クラスで動作し、それに接続されている **UIStorageSlot** スクリプトを、気づくでしょう。それはあなたがアイテムをピックアップし、アイテムが削除されていることをストレージクラスに通知することができものだ。スクリプト自体は短いですが、それは **UIItemSlot** から派生しているだけです - また **UIEquipmentSlot** で使用されている一般的なスクリプト - 3インベントリのアイコン上でスクリプトを実行します。要するに、これらのスクリプトのすべては、それぞれのコンテナからアイテムを移動するだけを許可しています。

.. UIEquipmentSlot works directly with InvEquipment class which you can find by selecting the Orc.
**UIEquipmentSlot** は、オークを選択することによって見つけることができ、 **InvEquipment** クラスで直接動作します。

.. When creating your own custom container, you will want to create an item slot class by deriving from UIItemSlot (use UIEquipmentSlot as an example) and making it work with your custom container.
独自のカスタムコンテナを作成するときには、 **UIItemSlot** （例として **UIEquipmentSlot** を使用します）から派生し、それはカスタムコンテナで動作することにより、アイテムスロットのクラスを作成したくなるでしょう。

.. Finally, you may inquire — where are the orc’s initial items coming from? The answer? EquipItems script attached to the Orc. It takes item IDs and generates random game items which are then equipped by the inventory equipment system.
最後に、尋ねるかもしれ - ここでオークの最初のアイテムは、から来ていますか？答えは？  **EquipItems** スクリプトは、オークに接続されている。これは、アイテムIDを取得し、インベントリの機器システムが装備されているランダムなゲームアイテムを生成します。

.. Well, that’s about it!
ええと、それはそれについてです！

.. image:: ../images/example3.jpeg
