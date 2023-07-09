---
description: Guide for installing for TxcWardrobes.
---

# Installation

{% hint style="warning" %}
Please read the entire guide before contacting support
{% endhint %}

## 1. Before starting <a href="#starting" id="starting"></a>

To get started, you must first download the script from [`Github`](https://github.com/ToxicJellyTV/TxcWardrobes) or from [`TxcStore`](https://www.txcstore.com/).

## 2. Dependencies <a href="#dependencies" id="dependencies"></a>

All dependencies are required for the script to work correctly, if available you can download them from the links below.

<table data-full-width="false"><thead><tr><th width="272" align="center">Script</th><th align="center">Download</th></tr></thead><tbody><tr><td align="center"><strong>ex_extended</strong></td><td align="center">-</td></tr><tr><td align="center">skinchanger</td><td align="center">-</td></tr><tr><td align="center">ox_lib</td><td align="center"><a href="https://github.com/overextended/ox_lib/releases">https://github.com/overextended/ox_lib/releases</a></td></tr><tr><td align="center">oxmysql</td><td align="center"><a href="https://github.com/overextended/ox_lib/releases">https://github.com/overextended/oxmysql/releases</a></td></tr></tbody></table>

## 3. Database installation <a href="#database" id="database"></a>

For outfit saving to work, you need to insert this SQL snippet into your database, otherwise errors are unavoidable.

```sql
CREATE TABLE IF NOT EXISTS `txc_wardrobes` (
    id VARCHAR(50) NOT NULL, 
    job TINYINT(1) NOT NULL DEFAULT 0, 
    outfits LONGTEXT DEFAULT '[]', 
    PRIMARY KEY (id)
)
```

## 4. Configuring <a href="#configurations" id="configurations"></a>

First you need to select the correct ESX Framework in <mark style="color:blue;">`config.lua`</mark> .\
Version 1.9 or higher

```lua
Config.Framework = 'new_esx'
```

Version 1.8 or lower

```lua
Config.Framework = 'esx'
```

Now you can select the Notify, TextUi and the menu.

```lua
Config.Notify = 'esx' -- ('none', 'esx', 'ox', 'okok', 'qs' and 'custom')
Config.TextUI = 'esx' -- ('none', 'esx', 'ox', 'okok' and 'custom')
Config.Menu = 'oxmenu' -- ('oxmenu' and 'oxcontext')
```

You can also chose how you want to display and interact with the wardrobe.

```lua
Config.Key = 38 -- Default: E
Config.Blips = true -- Default: true
Config.Marker = true -- Default: true
Config.OxTarget = false -- Default: false
```

Further options are mostly irrelevant and can be left on the default settings.
