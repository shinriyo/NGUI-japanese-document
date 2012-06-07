========================================================================
13.Character Inventory　※アセットの中のシーンは13ではなくXです。
========================================================================

Let me begin by saying that this is the most complicated example bundled within the NGUI’s package, but not because of the UI.

This example actually features a fairly advanced random item generation system that uses user-specified items to generate alternate versions of those items with a random level and quality setting.

Please note that this is a bonus example that comes with NGUI. If you are not interested in implementing an inventory system for your game, you can safely skip it as the majority of what’s involved is not UI-related at all.

The purpose of this example was to explore how NGUI could be integrated with another advanced system. As such, this example features a large number of custom scripts that all begin with the “Inv” prefix, such as “InvEquipment“, “InvBaseItem“, “InvTools“, etc. Conveniently for you, all of the custom scripts can be found in a single location: inside the InventorySystem folder.

    Still reading? Alright. Let’s start with how the items are created: InvDatabase.Select the ItemDatabase game object.
        
        This is where all the items used by this example are created and stored. As you can see you are presented with a custom inspector tool that lets you navigate and edit items.
            
        You can press Alt+Shift+i at any time to find objects by name (or go via the Inventory menu up top).

        All item stats are entered as if they were of max level. This lets you easily compare items one to another to see which one is supposed to be better.

        Keep in mind, you are not creating in-game items here. You are merely creating item templates that will be used to generate actual items. When the system generates Game Items, they will be created within the item level range specified on your template and will be given a random quality level.

        Final game item stats are calculated by taking the template’s stats and mixing it with the item’s level, adjusted by the item’s quality.

        Before moving on to the next component, note the Slot field here. Each item can go into a certain slot. When equipping items later, the prefab specified by the Attachment field will be instantiated for every single slot on the character that matches this field. This is why you see two bracers, two shoulderpads, and two boots although only one attachment game object has been specified.

        Search for “Attachment” in the Hierarchy view to see where those points are on the character. And yes, I had to eyeball them when positioning them. Note the InvAttachmentPoint script on those game objects. All equipped items get instantiated and attached as children of these game objects.

        If you examine the actual hierarchy of the scene you will notice that there are 3 root game objects: one for the 2D UI, one for the 3D UI, and one for the Scene itself.
            
        If you hit Alt+Shift+P to bring up the Panel Tool you will also notice that each one of those root nodes has a UIPanelattached.

        2D UI is used for the Tooltip, as I wanted it to look crisp and clear on the screen.

           3D UI is used to draw all the UI elements you see: buttons, item slots, items, backpack.

              Scene is where the character is located, but it also contains the widget used to draw the background.

              Let’s start with the Tooltip. If you select it in the hierarchy you will notice that it has a UITooltip script attached.

              This custom script is used to create tooltips for items that you specify. All it needs to know is the camera that will be used to draw it so it can position itself properly, the text label to fill with text, and the background sprite to resize so that it envelops the text. If “Scaling Transitions” is enabled, the tooltip will be shown via a mix of scaling and color adjustments, making it “swoop in”. The way this script is used via code is simple: UITooltip.ShowItem(<game item>);

              Moving on to the 3D UI, you may notice a disabled Storage Icon Template, and chances are you have already noticed that the actual backpack widgets are nowhere to be found while in the editor. That’s because the backpack gets created dynamically via a script on the Backpack game object — UIItemStorage.

              By selecting that game object and examining the script, you will notice that you can specify the maximum number of items, rows, and columns in addition to the template game object it will use to create the backpack’s cells. Now, it’s not limited to being a backpack — Item Storage can be anything — a store item list, a chest in the game, a vault… even another player’s inventory. In addition to the creation of the backpack, this script has several useful functions you can use in your code:

              UIItemStorage.GetItem(slot) gives you the item in the specified slot, or ‘null’ if none.

              UIItemStorage.Replace(slot, game item) lets you replace an item at the specified slot with another one, returning the item it replaced.

              If you want to remove an item from the container, simply pass ‘null’ as the second parameter. You can destroy the returned item to effectively get rid of it altogether.

              Of course you also can always see what’s in the item container by accessing UIItemStorage.items.

              If you select the disabled Storage Icon Template object, you will notice UIStorageSlot script attached to it, which works with the UIItemStorage class. It’s what allows you to pick up items and notify the storage class that the item has been removed. The script itself is short, but only because it’s derived from UIItemSlot — a generalized script that’s also used by UIEquipmentSlot

               — the script on the 3 inventory icons. In short, all these scripts allow you to do is move items from their respective containers.

               UIEquipmentSlot works directly with InvEquipment class which you can find by selecting the Orc.

               When creating your own custom container, you will want to create an item slot class by deriving from UIItemSlot (use UIEquipmentSlot as an example) and making it work with your custom container.

               Finally, you may inquire — where are the orc’s initial items coming from? The answer? EquipItems script attached to the Orc. It takes item IDs and generates random game items which are then equipped by the inventory equipment system.

               Well, that’s about it!

