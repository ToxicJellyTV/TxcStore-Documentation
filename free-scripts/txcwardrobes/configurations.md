---
description: Here you can find all configs of the script.
---

# Configurations

## config.lua

{% code overflow="wrap" %}
```lua
--[[
 ██████╗ ██████╗ ███╗   ██╗███████╗██╗ ██████╗ 
██╔════╝██╔═══██╗████╗  ██║██╔════╝██║██╔════╝ 
██║     ██║   ██║██╔██╗ ██║█████╗  ██║██║  ███╗
██║     ██║   ██║██║╚██╗██║██╔══╝  ██║██║   ██║
╚██████╗╚██████╔╝██║ ╚████║██║     ██║╚██████╔╝
 ╚═════╝ ╚═════╝ ╚═╝  ╚═══╝╚═╝     ╚═╝ ╚═════╝                                    
--]]

Config = {}

Config.DevMode = false -- only activate this if you're editing the config
Config.Locale = 'en' -- choose your locales (If you've created new locales for other languages, let me know via Discord)
Config.Framework = 'esx' -- you can choose between 'esx' and 'new_esx' (v1.9 and above)

Config.Notify = 'esx' -- choose the notification that is displayed when you change your outfit (available options: 'none', 'esx', 'ox', 'okok', 'qs' and 'custom')
Config.TextUI = 'esx' -- the text that is displayed when you enter a zone to change your outfit (available options: 'none', 'esx', 'ox', 'okok' and 'custom')

Config.Key = 38 -- the key with which you can open the wardrobe (default: E)
Config.Blips = true -- if true blips are displayed
Config.Marker = true -- if true markers are displayed
Config.OxTarget = false -- if true you can use ox_target to interact with the wardrobe (disables the key above)

Config.PointDistance = 1.5 -- this changes the interaction distance of the wardrobe
Config.MarkerDistance = 10.0 -- this changes the draw distance of markers
Config.TargetDistance = 2.0 -- this changes the interaction distance of target

Config.Menu = 'oxcontext' -- choose the menu that is displayed when you change your outfit 'oxmenu' or 'oxcontext'
Config.MenuPosition = 'top-right' -- choose between 'top-left', 'top-right', 'bottom-left' and 'bottom-right' ! ONLY FOR OXMENU !
Config.DisplayNoOutfitsFound = true -- If true, the menu will show 'No Outfits found' if no saved outfits were found

Config.UpdateIntervall = 2000 -- time in ms in which the job and grade are updated

Config.SavedComponents = { -- choose which components of the clothes can be stored in the wardrobe
    -- general
    'torso_1',        'torso_2',
    'tshirt_1',       'tshirt_2',
    'arms',           'arms_2',
    'pants_1',        'pants_2',
    'shoes_1',        'shoes_2',
    -- accessory
    'glasses_1',      'glasses_2',
    'bracelets_1',    'bracelets_2',
    'chain_1',        'chain_2',
    'decals_1',       'decals_2',
    'watches_1',      'watches_2',
    -- headgear
    'helmet_1',       'helmet_2',
    'mask_1',         'mask_2',
    -- other
    'bproof_1',       'bproof_2',
    'bags_1',         'bags_2',
}
```
{% endcode %}

## wardrobes.lua

````lua
--[[
██╗    ██╗ █████╗ ██████╗ ██████╗ ██████╗  ██████╗ ██████╗ ███████╗███████╗
██║    ██║██╔══██╗██╔══██╗██╔══██╗██╔══██╗██╔═══██╗██╔══██╗██╔════╝██╔════╝
██║ █╗ ██║███████║██████╔╝██║  ██║██████╔╝██║   ██║██████╔╝█████╗  ███████╗
██║███╗██║██╔══██║██╔══██╗██║  ██║██╔══██╗██║   ██║██╔══██╗██╔══╝  ╚════██║
╚███╔███╔╝██║  ██║██║  ██║██████╔╝██║  ██║╚██████╔╝██████╔╝███████╗███████║
 ╚══╝╚══╝ ╚═╝  ╚═╝╚═╝  ╚═╝╚═════╝ ╚═╝  ╚═╝ ╚═════╝ ╚═════╝ ╚══════╝╚══════╝                                                                  
--]]

Wardrobes = {
    ['main_wardrobe'] = {
        label = 'LSPD Garderobe', -- the title of the wardrobe menu
        job = 'police', -- the job that is allowed to open the wardrobe ('none' for everyone)```lua
        grade = 0, -- the grade (and above) is allowed to open the wardrobe (0 for everyone)
        type = 'both', -- choose between private (only saved outfits), society (only society outfits) and both
        coords = vec3(456.4519, -989.0461, 30.6896),
        polyzones = { -- if you use ox_target this is required
            { -- it is also possible for multiple zones to access the same wardrobe
                coords = vec3(457.66, -987.51, 31.09),
                size = vec3(5.4, 0.5, 1.95),
                rotation = 180
            }
        },
        marker = { -- if you want a marker this is required
            type = 20,
            size = { x = 0.9, y = 0.9, z = 0.9 },
            color = { r = 0, g = 144, b = 255, a = 100 },
        },
        blip = { -- if you want a blip this is required
            sprite = 73,
            scale = 0.8,
            color = 29,
            pos = vector3(456.4519, -989.0461, 30.6896),
            dp = 4
        },
        options = { 
            {
                label = 'Uniform', -- the name of the outfit
                desc = 'The regular uniform of a patrol officer.', -- optional description of the outfit
                icon = 'fa-user-tie', -- choose the font awesome icon
                armor = 0, -- if you want to set the player armor (max is 100)
                outfits = {
                    [0] = { -- if you have job grade-dependent uniforms, enter the respective grade (otherwise 0)
                        male = { -- check skinchanger client main.lua for matching elements
                            tshirt_1 = 58,    tshirt_2 = 0,
                            torso_1 = 55,     torso_2 = 0,
                            decals_1 = 0,     decals_2 = 0,
                            arms = 0,
                            pants_1 = 35,     pants_2 = 0,
                            shoes_1 = 25,     shoes_2 = 0,
                            helmet_1 = 46,    helmet_2 = 0,
                            chain_1 = 0,      chain_2 = 0,
                        }, -- leave out parts that you don't want to change
                        female = {
                            tshirt_1 = 35,  tshirt_2 = 0,
                            torso_1 = 48,   torso_2 = 0,
                            decals_1 = 0,   decals_2 = 0,
                            arms = 14,
                            pants_1 = 34,   pants_2 = 0,
                            shoes_1 = 27,   shoes_2 = 0,
                            helmet_1 = 45,  helmet_2 = 0,
                            chain_1 = 0,    chain_2 = 0,
                        }
                    }
                }
            }
        }
    }
}
````

## locales.lua

```lua
--[[
██╗      ██████╗  ██████╗ █████╗ ██╗     ███████╗███████╗
██║     ██╔═══██╗██╔════╝██╔══██╗██║     ██╔════╝██╔════╝
██║     ██║   ██║██║     ███████║██║     █████╗  ███████╗
██║     ██║   ██║██║     ██╔══██║██║     ██╔══╝  ╚════██║
███████╗╚██████╔╝╚██████╗██║  ██║███████╗███████╗███████║
╚══════╝ ╚═════╝  ╚═════╝╚═╝  ╚═╝╚══════╝╚══════╝╚══════╝                                                
--]]

Locales = {
    ['en'] = {
        ['title'] = 'Wardrobe',

        -- interactions
        ['open_key'] = '[E] - ',
        ['open_wardrobe'] = 'Open wardrobe',

        -- main menu
        ['saved_outfits'] = 'Saved outfits',
        ['saved_outfits_desc'] = 'Manage your saved outfits.',
        ['society_outfits'] = 'Society outfits',
        ['society_outfits_desc'] = "Check out your socities's preconfigured outfits.",
        
        -- manage private outfits
        ['save_outfit'] = 'Save',
        ['put_on_outfit'] = 'Wear',
        ['rename_outfit'] = 'Rename',
        ['delete_outfit'] = 'Delete',
        
        ['save_outfit_title'] = 'Save Outfit',
        ['save_outfit_desc'] = 'Save the outfit that you are currently wearing',
        ['rename_outfit_title'] = 'Rename Outfit',
        ['manage_outfit_desc'] = 'Wear, delete or rename a saved outfit',

        -- input
        ['input_placeholder'] = 'Abc',
        ['input_outfit_name'] = 'Outfit Name',
        ['input_outfit_desc'] = 'Input a name for your Outfit',

        -- civilian
        ['civilian_outfit'] = 'Civilian Outfit',
        ['civilian_desc'] = "You've put your normal clothes back on.",

        -- wearing
        ['civilian_notify'] = "You've put on your normal clothes.",
        ['outfit_notify'] = "You've put on {outfit}.",

        -- success
        ['outfit_save_success'] = 'Outfit saved succesfully.',
        ['outfit_rename_success'] = 'Outfit succesfully renamed to {name}.',
        ['outfit_delete_success'] = 'Outfit succesfully deleted.',

        -- errors
        ['already_wearing'] = 'You are already wearing this outfit.',
        ['no_saved_clothes'] = 'No outfits found',
        ['no_saved_clothes_desc'] = 'You have not yet saved any outfits.',
    },

    ['de'] = {
        ['title'] = 'Kleiderschrank',

        -- interactions
        ['open_key'] = '[E] - ',
        ['open_wardrobe'] = 'Öffne Kleiderschrank',

        -- main menu
        ['saved_outfits'] = 'Gespeicherte Kleidung',
        ['saved_outfits_desc'] = 'Verwalte deine gespeicherten Outfits.',
        ['society_outfits'] = 'Firmenkleidung',
        ['society_outfits_desc'] = 'Siehe dir die vorkonfigurierte Kleidung deines Unternehmens an.',
        
        -- manage private outfits
        ['save_outfit'] = 'Speichern',
        ['put_on_outfit'] = 'Anziehen',
        ['rename_outfit'] = 'Umbenennen',
        ['delete_outfit'] = 'Löschen',
        
        ['save_outfit_title'] = 'Speichere Kleidung',
        ['save_outfit_desc'] = 'Speichere deine aktuell getragene Kleidung.',
        ['rename_outfit_title'] = 'Umbenenne Kleidung',
        ['manage_outfit_desc'] = 'Trage, lösche oder benenne deine gespeicherte Kleidung um.',

        -- input
        ['input_placeholder'] = 'Abc',
        ['input_outfit_name'] = 'Kleidungsname',
        ['input_outfit_desc'] = 'Gebe einen Namen für die Kleidung ein.',

        -- civilian
        ['civilian_outfit'] = 'Zivilkleidung',
        ['civilian_desc'] = 'Ziehe wieder deine private Kleidung an.',

        -- wearing
        ['civilian_notify'] = 'Du hast deine private Kleidung angezogen.',
        ['outfit_notify'] = 'Du hast {outfit} angezogen.',

        -- success
        ['outfit_save_success'] = 'Kleidung erfolgreich gespeichert.',
        ['outfit_rename_success'] = 'Kleidung erfolgreich zu {name} umbenannt.',
        ['outfit_delete_success'] = 'Kleidung erfolgreich gelöscht.',

        -- errors
        ['already_wearing'] = 'Du hast diese Kleidung bereits an.',
        ['no_saved_clothes'] = 'Keine Kleidung gefunden',
        ['no_saved_clothes_desc'] = 'Du hast bisher keine Kleidung gespeichert.',
    },
}
```

## custom.lua

```lua
--[[
 ██████╗██╗   ██╗███████╗████████╗ ██████╗ ███╗   ███╗
██╔════╝██║   ██║██╔════╝╚══██╔══╝██╔═══██╗████╗ ████║
██║     ██║   ██║███████╗   ██║   ██║   ██║██╔████╔██║
██║     ██║   ██║╚════██║   ██║   ██║   ██║██║╚██╔╝██║
╚██████╗╚██████╔╝███████║   ██║   ╚██████╔╝██║ ╚═╝ ██║
 ╚═════╝ ╚═════╝ ╚══════╝   ╚═╝    ╚═════╝ ╚═╝     ╚═╝                                          
--]]

-- If you don't know what you're doing, don't edit this part of the config

Config.CustomNotify = function(text, subtext, type)
    -- type = can be 'error' or 'success'

    if Config.Notify == 'none' then
        return
    end

    -- if you have a custom notify
    if Config.Notify == 'custom' then
        -- your code
    end

    -- qs notify
    if Config.Notify == 'qs' then
        exports['qs-notify']:Alert(subtext, 1500, type)
    end

    -- okok notify
    if Config.Notify == 'okok' then
        exports['okokNotify']:Alert(text, subtext, 1500, type, false)
    end

    -- ox_lib
    if Config.Notify == 'ox' then
        lib.notify({
            title = text,
            description = subtext,
            position = 'top',
            type = type
        })
    end

    -- default esx
    if Config.Notify == 'esx' then
        ESX.ShowNotification(subtext)
    end
end

Config.CustomShowTextUI = function(text)
    -- if you have a custom text ui
    if Config.TextUI == 'custom' then
        -- your code
    end

    -- okok textui
    if Config.Notify == 'okok' then
        exports['okokTextUI']:Open(text, 'lightblue', 'right')
    end

    -- ox_lib
    if Config.TextUI == 'ox' then
        lib.showTextUI(text, {
            position = "right-center",
            icon = 'fa-shirt',
        })
    end

    -- default esx
    if Config.TextUI == 'esx' then
        ESX.ShowNotification(text)
    end
end

Config.CustomHideTextUI = function()
    -- if you have a custom text ui
    if Config.TextUI == 'custom' then
        -- your code
    end

    -- okok textui
    if Config.Notify == 'okok' then
        exports['okokTextUI']:Close()
    end

    -- ox_lib
    if Config.TextUI == 'ox' then
        lib.hideTextUI()
    end
end

Config.CustomLocale = function(text, toReplace, replaceWith)
    local current = Config.Locale
    local fallback = 'en'

    local locale = Locales[current] or Locales[fallback]
    local string = locale[text] or Locales[fallback][text]
    
    if toReplace and replaceWith then
        string = replaceSubstring(string, toReplace, replaceWith)
    end

    return string
end
```
