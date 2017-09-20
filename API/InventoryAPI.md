# Inventory
The inventory is used to hold and manage user items.

##### Inherits from: `BaseObject`
##### Requires: `MetaPlayer`

## Fields

| Field         | Type          | Description  |
| --------------|-------------| ------------ |
| className | `String` | The className of the object; typically used to recognize object type. |
| focusedSlot | `Slot` | The slot which currently has the user's mouse hovering over it. |
| slots | `Array<Slot>` | An array containing all of this inventory's slots. |

## Instantiation
Every object has a constructor. The constructor is called via the `Class` object

##### Example:
```lua
local Class = require(game.ReplicatedStorage.Classes.Class);

local Inventory = Class.new('Inventory', param1, param2, ...);
```

#### Parameters

| Parameter | Type | Description  |
| --------------|-------------| ------------ |
| player | `MetaPlayer` | The MetaPlayer object that the inventory belongs to. |
| element | `Rbx<GuiObject>` | The GUI that the inventory should be generated in. Requires a child named "SlotsContainer" |
| size `optional` | `Integer` | The number of slots to generate in `element`. Defaults to `24` |

##### Here's a template for what this might look like:

```lua
local Inventory = Class.new('Inventory', {MetaPlayer player}, {Rbx<GuiObject> element}, {Integer size});
```

##### Examples for what it might actually look like:

```lua
-- Generate an inventory with 24 slots
local Inventory = Class.new('Inventory', metaPlayer, inventoryGui);

-- Generate an inventory with 8 slots
local Inventory = Class.new('Inventory', metaPlayer, inventoryGui, 8);
```

## Events

None.

## Methods

### Inventory:addItem({itemType}, {quantity})
Attempts to add the item with specified quantity to the inventory. 
Tries to fill any unfilled slots that already contain that item.

#### Parameters

| Parameter | Type | Description |
| -------------- | ------------- | ------------ |
| itemType | `String` | The name of the item to add |
| quantity | `Integer` | The quantity of the item to add |

#### Returns

| Type | Description  |
| ------------- | ------------ |
| `Integer` | The quantity that did not fit, returns 0 if it all fit. |

##### Example:
```lua
-- Adds 5000 coins to the inventory.
local leftoverCoins = Inventory:addItem('Coin', 5000);
```

### Inventory:getSlotsByItemType({itemType})
Scans the inventory for slots that contain the specified itemType

#### Parameters

| Parameter | Type | Description |
| -------------- | ------------- | ------------ |
| itemType | `String` | The name of the item to look for |

#### Returns

| Type | Description  |
| ------------- | ------------ |
| `Array<Slot>` | An array of slots that contain the specified item |

##### Example:
```lua
-- Gets all slots containing coins.
local slots = Inventory:getSlotsByItemType('Coin');
```

### Inventory:getEmptySlots()
Scans the inventory for empty slots

#### Parameters

None.

#### Returns

| Type | Description  |
| ------------- | ------------ |
| `Array<Slot>` | An array of empty slots |

##### Example:
```lua
-- Gets all empty slots.
local slot = Inventory:getEmptySlots();
```

### Inventory:removeItem({itemType}, {quantity})
Removes up to the quantity of the itemType specified from any of the slots in the inventory.

#### Parameters

| Parameter | Type | Description |
| -------------- | ------------- | ------------ |
| itemType | `String` | The name of the item to remove |
| quantity | `Integer` | The quantity of the item to remove |

#### Returns

| Type | Description  |
| ------------- | ------------ |
| `Integer` | The quantity left over. Returns 0 if all of the quantity was removed. |

##### Example:
```lua
-- Removes up to 5000 coins from the inventory.
local leftover = Inventory:removeItem('Coin', 5000);
```

### Inventory:removeItem({slot}, {quantity})
Removes the quantity of items from the specified slot

#### Parameters

| Parameter | Type | Description |
| -------------- | ------------- | ------------ |
| slot | `Slot` | The slot to remove items from |
| quantity | `Integer` | The quantity of the item to remove |

#### Returns

| Type | Description  |
| ------------- | ------------ |
| `Integer` | The quantity left over. Returns 0 if all of the quantity was removed. |

##### Example:
```lua
-- Removes up to 5000 coins from SomeSlot.
local leftover = Inventory:removeItem(SomeSlot, 5000);
```

### Inventory:fillSlot({slot})
Attempts to fill the specified slot to max stack by taking from other slots with the same item type.

#### Parameters

| Parameter | Type | Description |
| -------------- | ------------- | ------------ |
| slot | `Slot` | The slot to fill |

#### Returns

| Type | Description  |
| ------------- | ------------ |
| `Integer` | The number of items needed to fill the specified slot to max stack. |

##### Example:
```lua
-- Attempts to fill SomeSlot
local needed = Inventory:fillItem(SomeSlot);
```
