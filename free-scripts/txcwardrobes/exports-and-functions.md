---
description: Benutzung von den bereitgestellten Funktionen von TxcWardrobe.
---

# Exports & Functions

## 1. Speichern eines Outfits in der Wardrobe <a href="#saveoutfit" id="saveoutfit"></a>

Um ein Outfit über z.B. ein anderes Skript zu speichern, kann client seitig folgender export genutzt werden:

```lua
exports['TxcWardrobes']:saveOutfit(name, outfit)
```

* name: `string`
  * Name worunter das Outfit gespeichert werden soll.
* outfit: `table`
  * Alle Kleidungsstücke, welche gespeichert werden sollen.

### Beispiele

Hiermit würde dann die aktuell getragene Kleidung gespeichert werden.

```lua
TriggerEvent('skinchanger:getSkin'), function(skin)
    exports['TxcWardrobes']:saveOutfit('TestOutfit', skin)
end
```

Hiermit würde das angegebene table als Outfit gespeichert werden.

```lua
local table = {
    'torso_1' = 1,
    'torso_2' = 1,
}

exports['TxcWardrobes']:saveOutfit('TestOutfit', table)
```

## 2. Öffnen der Wardrobe <a href="#openwardrobe" id="openwardrobe"></a>

Um die Wardrobe extern öffnen zu können, kann folgender export client seitig verwendet werden:

```lua
exports['TxcWardrobes']:openWardrobe(id)
```

* id: `string`
  * Die ID der Wardrobe, welche geöffnet werden soll.

### Beispiel

Standardmäßig gibt es die LSPD Wardrobe mit der ID: `main_wardrobe`, so würde es dann aussehen, wenn man die aufrufen möchte.

```lua
exports['TxcWardrobes']:openWardrobe('main_wardrobe')
```
