---
description: Usage of all of the functions provided by TxcWardrobes
---

# Exports & Functions

## 1. Saving your outfits in the Wardrobe <a href="#saveoutfit" id="saveoutfit"></a>

To save an outfit with another script, this client sided export can be used.

```lua
exports['TxcWardrobes']:saveOutfit(name, outfit)
```

* name: `string`
  * Outfit name
* outfit: `table`
  * All clothing pieces that are saved in this outfit
* notify: `boolean`
  * True, if you want a notify to be send.

### Examples

This is how you would save the currently worn outfit.

```lua
TriggerEvent('skinchanger:getSkin'), function(skin)
    exports['TxcWardrobes']:saveOutfit('TestOutfit', skin)
end
```

This is how the provided table would be saved as an outfit.

```lua
local table = {
    'torso_1' = 1,
    'torso_2' = 1,
}

exports['TxcWardrobes']:saveOutfit('TestOutfit', table)
```

## 2. Opening the Wardrobe <a href="#openwardrobe" id="openwardrobe"></a>

To open the wardrobe externally, this client sided export can be used.

```lua
exports['TxcWardrobes']:openWardrobe(id)
```

* id: `string`
  * The id of the Wardrobe you want to open

### Example

The standard wardrobe is the LSPD wardrobe with the id: `main_wardrobe`, this is how you would access it.

```lua
exports['TxcWardrobes']:openWardrobe('main_wardrobe')
```
