# ps-housing

ps-housing is a resource that opens up a world of creative possibilities for housing. Its user-friendly interface lets you decorate any location to your heart's content. The best part? Not only is it completely free, but it's also reliable and functional, unlike many other housing systems available. Dive in and start transforming spaces with ps-housing today!

ps-housing owes its existence to the exceptional coding expertise of [Xirvin#0985](https://github.com/ImXirvin). His application of top-tier coding practices has been instrumental in creating this script. We at Project Sloth are thrilled that he has joined our team and utilized our platform to deliver this incredible, much-anticipated resource. Our sincere appreciation goes out to [Xirvin#0985](https://github.com/ImXirvin) for his outstanding contribution!

# Preview [ps-housing](https://github.com/Project-Sloth/ps-housing)
![image](https://github.com/Project-Sloth/ps-housing/assets/82112471/07b7f8c6-38ea-4f8c-95b6-9bd6bafbbd09)
![image](https://github.com/Project-Sloth/ps-housing/assets/82112471/163ae847-5a44-48cb-89f5-e0c1e7b59383)
![image](https://github.com/Project-Sloth/ps-housing/assets/82112471/655d9bb6-6c6d-4676-b4e0-f4368f3325a9)
![image](https://github.com/Project-Sloth/ps-housing/assets/82112471/fc632975-c2f6-41fb-89cd-a984679f1a41)

# Preview [ps-realtor](https://github.com/Project-Sloth/ps-realtor)
![image](https://github.com/Project-Sloth/ps-realtor/assets/82112471/24e4018a-cb97-42b0-81df-3b0236c7e2dc)
![image](https://github.com/Project-Sloth/ps-realtor/assets/82112471/4d8ece54-ace1-4ffc-b8fb-90274bc94e72)
![image](https://github.com/Project-Sloth/ps-realtor/assets/82112471/188d259c-4c0f-4c91-905c-bf9b826cc518)
![image](https://github.com/Project-Sloth/ps-realtor/assets/82112471/9e033984-45f2-449d-ba6c-bb8742ac08bd)
![image](https://github.com/Project-Sloth/ps-realtor/assets/82112471/0dd078b8-a941-4316-b9e1-26c696023139)

# Usage
- Players can decorate their houses and apartments with a full selection of furniture and decorations (included a wide variety of custom housing props)
- Provides support for housing and apartments and is a full replacement for qb-apartments and qb-housing
  - When a player first spawns after enabling ps-housing, they will have to choose an apartment. Once they spawn in the stashitems from their previous qb-apartment will be migrated to their new apartment stash.
- Allows players to purchase and list houses for sale through `ps-realtor` and the realtor job
- Houses come with personal garages
- Houses and apartments come with personal wardrobes and stashes
- Players can share keys to their houses and apartments with other players
  
## Creating a new property for sale
Players must have the realtor job to create new properties. Additionally if the realtor has a high enough grade level, they can also help players move to new apartments.
All properties must be manually configured for sale by the realtor job, giving you full control over all aspects of properties, and bringing another avenue of roleplay to your server.

- Pick the location where you want to create a new property
- Use `/housing` to open the housing menu
- Click on create new property
- Fill out the details of the property (name, price, description, which shell to use, etc)
- Choose the door location (this is where the person will enter the house)
    - Ensure that you place it up against a wall, since players will use target to enter the house
- Choose the garage location 
    - This point is used both for storing vehicles, as well as the location where the vehicle will spawn when taken out of the garage
- Realtors can edit the details of the property by clicking on the property in the housing menu
- Players can see the properties for sale through the /housing menu as well

## Furnish and decorate a property
Once inside the property, the player can furnish and decorate the property to their liking. They can also invite other players to their property, and give them access to the property. Open the furniture store by pressing `Z`. 

This will open a furniture store complete with all of the props. Select an item from the catalog and place it into the property. You can use the placement gizmo to position the item to your liking as well as use the UI tools for fine tune control over the placement. Once you are happy with the positioning, make sure you press `Add to Cart` before moving on. Continue to add as many items as you want to your cart. Once you are done, go to the `Checkout` and purchase the items. 

> Note: The place on ground button sometimes does not work properly depending on where the native detects the ground to be.

## Dynamic Doors

Dynamic Doors will turn placed doors into actual working doors, Instead of them being static. (See videos below)

### Preview

https://github.com/complexza/ps-housing/assets/74205343/72cfc135-2f78-42b3-a540-45f02567b6d7

https://github.com/complexza/ps-housing/assets/74205343/0ff26e7f-1341-45fc-8fc6-d65421dec0b2

### Setup
- You will need to set the `Config.DynamicDoors = true`
- You will have to add this convar into your server.cfg `setr game_enableDynamicDoorCreation "true"`

> Note: The convar has to be in your server.cfg in order for the doors to be dynamic!

### Shell Support
* [K4MB1](https://github.com/Project-Sloth/ps-housing/wiki/K4MB1-Shells-Support-&-Offsets)

# Important

* Players need to place their [stash](https://github.com/Project-Sloth/ps-housing/blob/7efd2009050b9a20969877cf69b284352a9309bf/shared/config.lua#LL426C96-L426C96) and [wardrobe](https://github.com/Project-Sloth/ps-housing/blob/7efd2009050b9a20969877cf69b284352a9309bf/shared/config.lua#L427) or else they wont have one. Check [Config](https://github.com/Project-Sloth/ps-housing/blob/7efd2009050b9a20969877cf69b284352a9309bf/shared/config.lua#L422) for more information.

* This entire README is meant for compatibility with default QBCore scripts. If you have different scripts, you'll need to adjust them for compatibility yourself. Refrain from asking us how to circumvent paid scripts that can't be adjusted for ps-housing support. Instead, request their support for ps-housing - this script is fully open source for that reason. Any inquiries related to this be ignored. 

# Installation
## Kamaryn has created an amazing setup video located [here.](https://www.youtube.com/watch?v=6YKkl20BevE)

## PAY ATTENTION TO EACH STEP. DO NOT SKIP ANY. 

### 1. Find the following events in `qb-multicharacter` and change in server/main.lua event to: 

`qb-multicharacter > server > main.lua`
```lua
RegisterNetEvent('qb-multicharacter:server:loadUserData', function(cData)
    local src = source
    if QBCore.Player.Login(src, cData.citizenid) then
        local Player = QBCore.Functions.GetPlayer(src)
        local Name = Player.PlayerData.charinfo.firstname .. " " .. Player.PlayerData.charinfo.lastname
        repeat
            Wait(10)
        until hasDonePreloading[src]
        print('[' .. GetPlayerName(src) .. '] - ^2' .. Name .. '^7 (Citizen ID: ' .. cData.citizenid .. ') has succesfully loaded!')
        QBCore.Commands.Refresh(src)
        if Config.SkipSelection then
            local coords = json.decode(cData.position)
            TriggerClientEvent('qb-multicharacter:client:spawnLastLocation', src, coords, cData)
        else
            TriggerClientEvent('ps-housing:client:setupSpawnUI', src, cData)
        end
        TriggerEvent("qb-log:server:CreateLog", "joinleave", "Loaded", "green", "**" .. GetPlayerName(src) .. "** - " .. Name .. " (<@" .. (QBCore.Functions.GetIdentifier(src, 'discord'):gsub("discord:", "") or "unknown") .. "> | ||" .. (QBCore.Functions.GetIdentifier(src, 'ip') or 'undefined') .. "|| | " .. (QBCore.Functions.GetIdentifier(src, 'license') or 'undefined') .. " | " .. cData.citizenid .. " | " .. src .. ") loaded..")
    end
end)
```

`qb-multicharacter > server > main.lua`
```lua
RegisterNetEvent('qb-multicharacter:server:createCharacter', function(data)
    local src = source
    local newData = {}
    newData.cid = data.cid
    newData.charinfo = data
    if QBCore.Player.Login(src, false, newData) then
        repeat
            Wait(10)
        until hasDonePreloading[src]
        print('^2[qb-core]^7 '..GetPlayerName(src)..' has succesfully loaded!')
        QBCore.Commands.Refresh(src)
        TriggerClientEvent("qb-multicharacter:client:closeNUI", src)
        newData.citizenid = QBCore.Functions.GetPlayer(src).PlayerData.citizenid
        TriggerClientEvent('ps-housing:client:setupSpawnUI', src, newData)
        GiveStarterItems(src)
    end
end)

```
### 2. Find the following event in `qb-multicharacter` and change in client/main.lua event to: 
`qb-multicharacter > client > main.lua`

```lua
RegisterNetEvent('qb-multicharacter:client:spawnLastLocation', function(coords, cData)
    local result = lib.callback.await('ps-housing:cb:GetOwnedApartment', source, cData.citizenid)
    if result then
        TriggerEvent("apartments:client:SetHomeBlip", result.type)
    end
    local ped = PlayerPedId()
    SetEntityCoords(ped, coords.x, coords.y, coords.z)
    SetEntityHeading(ped, coords.w)
    FreezeEntityPosition(ped, false)
    SetEntityVisible(ped, true)
    local PlayerData = QBCore.Functions.GetPlayerData()
    local insideMeta = PlayerData.metadata["inside"]
    DoScreenFadeOut(500)
    if insideMeta.propertyId then
        TriggerServerEvent('ps-housing:server:enterProperty', tostring(insideMeta.propertyId))
    else
        SetEntityCoords(ped, coords.x, coords.y, coords.z)
        SetEntityHeading(ped, coords.w)
        FreezeEntityPosition(ped, false)
        SetEntityVisible(ped, true)
    end
    TriggerServerEvent('QBCore:Server:OnPlayerLoaded')
    TriggerEvent('QBCore:Client:OnPlayerLoaded')
    Wait(2000)
    DoScreenFadeIn(250)
end)
```


### 3. Find the following events in `qb-spawn` and change in client/client.lua event to: 

`qb-spawn > client.lua > line 51 > 'qb-spawn:client:setupSpawns' event`
```lua
RegisterNetEvent('qb-spawn:client:setupSpawns', function(cData, new, apps)
    if not new then
        QBCore.Functions.TriggerCallback('qb-spawn:server:getOwnedHouses', function(houses)
            local myHouses = {}
            if houses ~= nil then
                for i = 1, (#houses), 1 do
                    local house = houses[i]

                    myHouses[#myHouses+1] = {
                        house = house,
                        label = (house.apartment or house.street) .. " " .. house.property_id,
                    }
                end
            end

            Wait(500)
            SendNUIMessage({
                action = "setupLocations",
                locations = QB.Spawns,
                houses = myHouses,
                isNew = new
            })
        end, cData.citizenid)
    elseif new then
        SendNUIMessage({
            action = "setupAppartements",
            locations = apps,
            isNew = new
        })
    end
end)
```

`qb-spawn > client.lua > line 134 > 'chooseAppa' NUI Callback`
```lua
RegisterNUICallback('chooseAppa', function(data, cb)
    local ped = PlayerPedId()
    local appaYeet = data.appType
    SetDisplay(false)
    DoScreenFadeOut(500)
    Wait(100)
    FreezeEntityPosition(ped, false)
    RenderScriptCams(false, true, 0, true, true)
    SetCamActive(cam, false)
    DestroyCam(cam, true)
    SetCamActive(cam2, false)
    DestroyCam(cam2, true)
    SetEntityVisible(ped, true)
    Wait(500)
    TriggerServerEvent('QBCore:Server:OnPlayerLoaded')
    TriggerEvent('QBCore:Client:OnPlayerLoaded')
    Wait(100)
    TriggerServerEvent("ps-housing:server:createNewApartment", appaYeet)
    cb('ok')
end)
```

`qb-spawn > client > client.lua > line 169 'spawnplayer' NUI Callback`
```lua
RegisterNUICallback('spawnplayer', function(data, cb)
    local location = tostring(data.spawnloc)
    local type = tostring(data.typeLoc)
    local ped = PlayerPedId()
    local PlayerData = QBCore.Functions.GetPlayerData()
    local insideMeta = PlayerData.metadata["inside"]
    if type == "current" then
        PreSpawnPlayer()
        QBCore.Functions.GetPlayerData(function(pd)
            ped = PlayerPedId()
            SetEntityCoords(ped, pd.position.x, pd.position.y, pd.position.z)
            SetEntityHeading(ped, pd.position.a)
            FreezeEntityPosition(ped, false)
        end)
        TriggerServerEvent('QBCore:Server:OnPlayerLoaded')
        TriggerEvent('QBCore:Client:OnPlayerLoaded')
        if insideMeta.property_id ~= nil then
            local property_id = insideMeta.property_id
            TriggerServerEvent('ps-housing:server:enterProperty', tostring(property_id))
        end
        PostSpawnPlayer()
    elseif type == "house" then
        PreSpawnPlayer()
        TriggerServerEvent('QBCore:Server:OnPlayerLoaded')
        TriggerEvent('QBCore:Client:OnPlayerLoaded')
        local property_id = data.spawnloc.property_id
        TriggerServerEvent('ps-housing:server:enterProperty', tostring(property_id))
        PostSpawnPlayer()
    elseif type == "normal" then
        local pos = QB.Spawns[location].coords
        PreSpawnPlayer()
        SetEntityCoords(ped, pos.x, pos.y, pos.z)
        TriggerServerEvent('QBCore:Server:OnPlayerLoaded')
        TriggerEvent('QBCore:Client:OnPlayerLoaded')
        TriggerServerEvent('ps-housing:server:resetMetaData')
        SetEntityCoords(ped, pos.x, pos.y, pos.z)
        SetEntityHeading(ped, pos.w)
        PostSpawnPlayer()
    end
    cb('ok')
end)
```

`qb-spawn > server.lua > line 3`
```lua
QBCore.Functions.CreateCallback('qb-spawn:server:getOwnedHouses', function(_, cb, cid)
    if cid ~= nil then
        local houses = MySQL.query.await('SELECT * FROM properties WHERE owner_citizenid = ?', {cid})
        if houses[1] ~= nil then
            cb(houses)
        else
            cb({})
        end
    else
        cb({})
    end
end)
```

### 4. Find the following events in `qb-garages` and change: 
`qb-garages > server > main.lua > around line 120` on event `qb-garage:server:checkOwnership`

Replace 
```lua
local hasHouseKey = exports['qb-houses']:hasKey(result[1].license, result[1].citizenid, house)
```
With
```lua
local hasHouseKey = exports['ps-housing']:IsOwner(src, house)
```

`qb-garages > client > main.lua > around line 451` add under event `qb-garages:client:addHouseGarage`
```lua
RegisterNetEvent('qb-garages:client:removeHouseGarage', function(house)
    Config.HouseGarages[house] = nil
end)
```

### For qb-garages v2: 
`qb-garages > server > main.lua > around line 118` on event `qb-garages:server:canDeposit`

Replace 
```lua
if type == 'house' and not exports['qb-houses']:hasKey(Player.PlayerData.license, Player.PlayerData.citizenid, Config.HouseGarages[garage].label) then
```
With
```lua
if type == 'house' and not exports['ps-housing']:IsOwner(source, garage) then
```

`qb-garages > client > main.lua > around line 392` add under event `qb-garages:client:addHouseGarage`
```lua
RegisterNetEvent('qb-garages:client:removeHouseGarage', function(house)
    Config.Garages[house] = nil
end)
```

### 5. Run the `properties.sql` file, but be cautious. If a table named `properties` already exists in your database, this operation will drop it, resulting in the loss of all its data.

### 6. Delete default [qb-apartments](https://github.com/qbcore-framework/qb-apartments)

### 7. Delete default [qb-houses](https://github.com/qbcore-framework/qb-houses)

### 8. Delete `qb-apartments/config.lua` references in `qb-spawn`, `qb-multicharacter` and `qb-phone` fxmanifest.lua (and any other scripts that may reference it).

### 9. Ensure ps-realtor above ps-housing.

### 10. In your server.cfg, add `ensure ox_lib` above all other resources

### 11. Install the dependencies below.

# Dependencies
1. [ps-realtor](https://github.com/Project-Sloth/ps-realtor)
2. [fivem-freecam](https://github.com/Deltanic/fivem-freecam)
3. [ox_lib](https://github.com/overextended/ox_lib/releases) - Use the latest release. If you do not use the latest release, MAKE SURE TO BUILD THE UI. Find their docs [here](https://overextended.dev/ox_lib#building-the-ui) on how to build the UI.
4. [ox_target](https://github.com/overextended/ox_target) or [qb-target](https://github.com/qbcore-framework/qb-target) - Change in [Config](https://github.com/Project-Sloth/ps-housing/blob/3c0f197b6d639f13235598393c84aac8d23d5f7a/shared/config.lua#L8), default is qb-target.

## For reference your server.cfg should be ensured like below:
* We highly recommend making a folder named [ps-housing] and add `ps-realtor`, `fivem-freecam`, `ox_lib`, `ps-core`, `ps-housing` inside the folder.
  
```
ensure ox_lib
ensure ps-housing
ensure ps-realtor
ensure fivem-freecam
```
## End of Installation 

# Migrating houses and apartments from qb-houses and qb-apartments

1. From a client run the `migratehouses` command to automatically convert all houses from qb-houses. It will print a message to the console once complete.
   **The `migratehouses` command MUST be run from a client in order to retrieve street and region data for each house**

2. From a client or server console run the `migrateapartments` command to automatically convert all apartments from qb-apartments. It will print a message to the console once complete.

## Resolving the "Foreign key constraint is incorrectly formed" Issue

If you come across an error such as `Foreign key constraint is incorrectly formed` while importing the `properties.sql` into your database, follow these steps to fix it.

1. Open your database in HeidiSQL.
2. Right-click on your database name and select "Edit."
3. Locate the database collation setting take a note of it. 
4. You will need to format the `properties.sql` file to match your database collation.
5. Ensure that the collation of your `citizenid` column in your `players` table is `utf8mb4_general_ci` and not `utf8mb4_unicode_ci`

If your database collation is set to `utf8mb4_general_ci`, modify the last line of the `properties.sql` file using VSCode or in HeidiSQL's query tab to the following:

```sql
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
```
This adjustment ensures that `properties.sql` file's character set and collation match that of your database, effectively resolving the issue.

## Item Limits System

1. Choose an item you want to limit under `Config.Furniture` in under `shared/config.lua`
2. Add `["max"] = 3` or the number of your choice to the item (see example below)
```lua
{ ["object"] = "v_res_r_figcat", ["price"] = 300, ["max"] = 2, ["label"] = "Fig Cat" },
```

## Logs System Setup

1. Go to `qb-smallresources/server/logs.lua` and add this:
```lua
    ['pshousing'] = 'yourdiscordwebhookhere',
```
2. Create a webhook for the channel you want the logs to show up in.
3. Replace the placeholder with your webhook link.

> This system only supports qb-core for now.

## Adding New Shells
* Follow the [ps-housing wiki](https://github.com/Project-Sloth/ps-housing/wiki) information.

# Notes
- If a player is in their apartment/house and an admin does a "Bring to me" function, they will not see the player nor will the player see anyone else. This is because the player is still in their own unique routing bucket. **Workaround**: To fix this, the player must go back into their apartment and leave on their own. 
    - Likewise, if an admin tries to "Go to" or "Spectate" a player that is in their apartment/house, the admin will not be able to see the apartment or player because it is in a different routing bucket.
# Credits
* [Xirvin](https://github.com/ImXirvin)
* [BackSH00TER](https://github.com/backsh00ter)
* [Byte Labs Project](https://github.com/Byte-Labs-Project)
* [Project Sloth Team](https://discord.gg/projectsloth)
* [K4MB1](https://www.k4mb1maps.com/)
* [Candrex](https://github.com/CandrexDev)

# Renewed qb-phone compatibility


# Add this to qb-phone
## Add  into fxmanifest.lua:shared_scripts
```lua
'ox_lib/init.lua',
```
## HTML
```lua
                    <div class="houses-app">
                        
                        <div class="house-container">
                            <div class="tabs">
                                <button class="tab active">Owned</button>
                                <button class="tab">Shared</button>
                            </div>
                            <div id="owned" class="tab-content">
                                <p class="no-properties-message" style="display: none;">You don't own any property...</p>
                                <div class="property-card">
                                    <div class="property-header">
                                        <h3 class="property-address">123 Main St, City</h3>
                                        <i class="fas fa-home property-icon"></i>
                                    </div>
                                    <div class="property-info">
                                        <i class="fas fa-box info-icon" title="Shell"></i>
                                        <i class="fas fa-user-friends users-icon" title="3 Users"></i>
                                        <i class="fas fa-car info-icon" title="Garage"></i>
                                    </div>
                                    <div class="owner-options">
                                        <div class="add-user-section">
                                            <button class="add-access-btn"><i class="fas fa-plus"></i></button>
                                            <div class="user-input-section" style="display: none;">
                                                <input type="text" class="user-input" placeholder="Add User">
                                            </div>
                                        </div>
                                        <ul class="access-list">
                                            <li>
                                                <i class="fas fa-user user-icon"></i>
                                                <span>John Doe</span>
                                                <i class="fas fa-times remove-icon"></i>
                                            </li>
                                        </ul>
                                    </div>
                                </div>
                            </div>
                            <div id="shared" class="tab-content" style="display: none;">
                                <p class="no-properties-message" style="display: none;">You don't have the keys to someone else's property</p>
                                <div class="property-card">
                                    <div class="property-header">
                                        <h3 class="property-address">456 Elm St, City</h3>
                                        <i class="fas fa-building property-icon"></i>
                                    </div>
                                    <div class="property-info">
                                        <i class="fas fa-box info-icon" title="Shell"></i>
                                        <i class="fas fa-user-friends users-icon" title="3 Users"></i>
                                        <i class="fas fa-car info-icon" title="Garage"></i>
                                    </div>
                                    <div class="owner-options">
                                        <div class="add-user-section">
                                            <button class="add-access-btn"><i class="fas fa-plus"></i></button>
                                            <div class="user-input-section" style="display: none;">
                                                <input type="text" class="user-input" placeholder="Add User">
                                            </div>
                                        </div>
                                        <ul class="access-list">
                                            <li>
                                                <i class="fas fa-user user-icon"></i>
                                                <span>John Doe</span>
                                                <i class="fas fa-times remove-icon"></i>
                                            </li>
                                        </ul>
                                    </div>
                                </div>
                            </div>            
                        </div>
                        
                    </div>
```
## houses.js
```js
let house;
let propertyId;

$(document).on('click', '.tab', function() {
    $('.tab-content').hide();
    $('.tab').removeClass('active');
    $(this).addClass('active');
    if ($(this).text() === 'Owned') {
        $('#owned').show();
    } else if ($(this).text() === 'Shared') {
        $('#shared').show();
    }
});

$(document).on('click', '.property-card', function(e){
    e.stopPropagation();
    var ownerOptions = $(this).find(".owner-options");
    ownerOptions.toggle();
    var HouseData = $(this).data('HouseData');
    if (HouseData && HouseData.propertyId) {
        propertyId = HouseData.propertyId;
    } else {
        console.error("HouseData not found or doesn't have a propertyId:", HouseData);
        return;
    }
    if (HouseData.numAccessNum > 0 && HouseData.has_access) {
        var sharedContainer = [];
        var self = this;
        $.post("https://qb-phone/GetPlayersWithAccess", JSON.stringify({
            propertyId: propertyId,
        }), function(playersWithAccess){
            if (playersWithAccess.length === 0) {
                $(self).find(".access-list").html('<li>No shared players.</li>');
            } else {
                $.each(playersWithAccess, function(index, sharedPlayer){
                    if (!sharedPlayer.citizenid) {
                        console.error("sharedPlayer doesn't have a citizenid property:", sharedPlayer);
                        return;
                    }
                    var playerName = sharedPlayer.name;
                    var sharedItem = '<li data-playerId=\'' + JSON.stringify(sharedPlayer) + '\'><i class="fas fa-user user-icon"></i><span>' + playerName + '</span><i class="fas fa-times remove-icon"></i></li>';
                    sharedContainer.push(sharedItem);
                });
                $(self).find(".access-list").html(sharedContainer.join(''));
            }
        });
    }
});

function ConfirmationFrame() {
    $('.spinner-input-frame').css("display", "flex");
    setTimeout(function () {
        $('.spinner-input-frame').css("display", "none");
        $('.checkmark-input-frame').css("display", "flex");
        setTimeout(function () {
            $('.checkmark-input-frame').css("display", "none");
        }, 2000)
    }, 1000)
}

function closeApp() {
    QB.Phone.Animations.TopSlideUp('.phone-application-container', 400, -160);
    QB.Phone.Animations.TopSlideUp('.'+QB.Phone.Data.currentApplication+"-app", 400, -160);
    setTimeout(function(){
        QB.Phone.Functions.ToggleApp(QB.Phone.Data.currentApplication, "none");
    }, 400)
    QB.Phone.Functions.HeaderTextColor("white", 300);
    QB.Phone.Data.currentApplication = null;
}

$(document).on('click', '.remove-icon', function(e){
    e.stopPropagation();
    
    var listItem = $(this).closest('li');
    var playerIdDataString = listItem.attr('data-playerId');
    
    if (playerIdDataString) {
        var playerIdData = JSON.parse(playerIdDataString);
    }

    if (!playerIdData || !playerIdData.citizenid) {
        console.error("playerId data attribute not found or doesn't have a citizenid property:", playerIdData);
        return;
    }

    var playerId = playerIdData.citizenid;
    var houseData = $(this).closest('.property-card').data('HouseData');

    $.post("https://qb-phone/KickPlayer", JSON.stringify({
        propertyId: houseData.propertyId,
        playerId: playerId,
    }));

    setTimeout(function(){
        ConfirmationFrame()
    }, 150);

    closeApp()
});


$(document).on('click', '.property-icon', function(e){
    e.stopPropagation();
    var houseData = $(this).closest('.property-card').data('HouseData');
    $.post("https://qb-phone/gpsProperty", JSON.stringify({
        house: houseData,
    }));
});

$(document).on('click', '.add-access-btn', function(e){
    e.stopPropagation();
    var userInputSection = $(this).siblings('.user-input-section');
    if (userInputSection.is(":visible")) {
        var stateid = userInputSection.find('.user-input').val();
        if (stateid !== "") {
            var houseData = $(this).closest('.property-card').data('HouseData');
            $.post("https://qb-phone/GiveKeys", JSON.stringify({
                propertyId: houseData.propertyId,
                hasAccess: houseData.has_access,
                id: stateid,
            }));
            userInputSection.find('.user-input').val('');
            userInputSection.hide();
            setTimeout(function(){
                ConfirmationFrame()
            }, 150);
            closeApp();
        } else {
            userInputSection.hide();
        }
    } else {
        userInputSection.show();
    }
});

$(document).on('click', '.user-input', function(e){
    e.stopPropagation();
});

SetupPlayerHouses = function (Houses) {
    $("#owned").html('<p class="no-properties-message">You don\'t own any property...</p>');
    $("#shared").html('<p class="no-properties-message">You don\'t have the keys to someone else\'s property</p>');
    if (Houses != null) {
        $.each(Houses, function (i, house) {
            var Element = '<div class="property-card" id="house-' + i + '">';
            Element += '<div class="property-header">';
            Element += '<h3 class="property-address">' + house.houseName + '</h3>';
            Element += '<i class="fas ' + house.houseIcon + ' property-icon" data-toggle="tooltip" data-placement="top" title="Owner: ' + house.fullname + '<br>Click to set GPS"></i>';
            Element += '</div>';
            Element += '<div class="property-info">';
            Element += '<i class="fas fa-box info-icon" data-toggle="tooltip" data-placement="top" title="' + house.shellName + '"></i>';
            Element += '<i class="fas fa-user-friends users-icon" data-toggle="tooltip" data-placement="top" title="' + house.numAccess + '"></i>';
            Element += '<i class="fas fa-car info-icon" data-toggle="tooltip" data-placement="top" title="' + house.garageStatus + '"></i>';
            Element += '</div>';
            if (house.has_access) {
                Element += '<div class="owner-options" style="display: none;">';
                Element += '<div class="add-user-section">';
                Element += '<button class="add-access-btn"><i class="fas fa-plus" data-toggle="tooltip" data-placement="top" title="Add player by ID"></i></button>';
                Element += '<div class="user-input-section" style="display: none;">';
                Element += '<input type="text" class="user-input" placeholder="STATE ID NOT CITIZEN!">';
                Element += '</div>';
                Element += '</div>';
                Element += '<ul class="access-list">';
                Element += '</ul>';
                Element += '</div>';
            }
            Element += '</div>';
            if (house.has_access) {
                $("#owned").append(Element);
            } else {
                $("#shared").append(Element);
            }
            $("#house-" + i).data('HouseData', house);
        });

        if ($("#owned .property-card").length === 0) {
            console.log("Showing owned no-properties-message");
            $("#owned .no-properties-message").show();
        } else {
            console.log("Hiding owned no-properties-message");
            $("#owned .no-properties-message").hide();
        }
            
        if ($("#shared .property-card").length === 0) {
            console.log("Showing shared no-properties-message");
            $("#shared .no-properties-message").show();
        } else {
            console.log("Hiding shared no-properties-message");
            $("#shared .no-properties-message").hide();
        }


        $('[data-toggle="tooltip"]').tooltip({ html: true });
    }
};
```

## client/houses.lua
```lua
-- NUI Callback

RegisterNUICallback('SetupHouses', function(_, cb)
    lib.callback('ps-housing:server:GetPlayerProperties', false, function(Houses)
        cb(Houses)
    end)
end)

RegisterNUICallback('gpsProperty', function(data, cb)
    local house = data.house
    local property = house.propertyId

    exports['ps-housing']:HouseTrack(property)

    --TriggerServerEvent('setPlayerWaypoint', property)

    TriggerEvent('qb-phone:client:CustomNotification', "PROPERTIES", "GPS Marker Set!", "fas fa-car", "#e84118", 5000)

    cb("ok")
end)

RegisterNUICallback('GiveKeys', function(data, cb)
    TriggerServerEvent('qb-phone:server:giveKeys', data)
    cb("ok")
end)

RegisterNUICallback('KickPlayer', function(data, cb)
    TriggerServerEvent("ps-housing:server:removeAccess", data.propertyId, data.playerId)
    cb("ok")
end)

RegisterNetEvent('qb-phone:client:giveKeys', function(property, toplayer)
    TriggerServerEvent("ps-housing:server:addAccess", property, toplayer)
end)

RegisterNUICallback('GetPlayersWithAccess', function(data, cb)
    local propertyId = data.propertyId
    local playersWithAccess = lib.callback.await("ps-housing:cb:getPlayersWithAccess", source, propertyId)
    cb(playersWithAccess)
end)
```

## server/houses.lua
```lua
RegisterNetEvent('qb-phone:server:giveKeys', function(data)
    local src = source
    local Player = QBCore.Functions.GetPlayer(src)
    local toplayer = tonumber(data.id)
    local OtherAsshole = QBCore.Functions.GetPlayer(toplayer)
    local property = tonumber(data.propertyId)

    if data.hasAccess == false then 
        TriggerClientEvent("QBCore:Notify", src, 'You are not an owner!', "error")
        return 
    end
    if not OtherAsshole then TriggerClientEvent("QBCore:Notify", src, 'State ID does not exist!', "error") return false end
    if not data.propertyId then return end
    if Player.PlayerData.citizenid == OtherAsshole.PlayerData.citizenid then return TriggerClientEvent("QBCore:Notify", src, 'You cannot give keys to yourself!', "error") end

    TriggerClientEvent("qb-phone:client:giveKeys", src, property, toplayer)
    TriggerClientEvent("QBCore:Notify", src, 'Done!', "success")
end)

```

## add this to qb-phone/html/app.js
```js
                } else if (PressedApplication == "houses") {
                    $.post('https://qb-phone/SetupHouses', JSON.stringify({}), function(Houses){
                        SetupPlayerHouses(Houses);
                    });
```
## replace qb-phone/html/css/houses.css with this
```css
@import url('https://fonts.googleapis.com/css?family=Lato&display=swap');

.houses-app {
    display: none;
    height: 100%;
    width: 100%;
    background: #242833;
    overflow: hidden;
}

.house-container {
    padding-top: 4vh !important;
    padding: 1vh;
}

.tabs {
    display: flex;
    justify-content: center;
    margin-bottom: 1vh;
}

.tab {
    background-color: #1c2028;
    color: #fff;
    border: none;
    padding: 0.625vh 1.25vh;
    margin: 0 0.3125vh;
    cursor: pointer;
    border-radius: 0.3125vh;
    transition: background-color 0.3s;
}

.tab:hover {
    background-color: rgba(0, 0, 0, 0.7);
    transform: translateY(-0.1875vh);
    box-shadow: 0 0.25vh 0.5vh rgba(0, 0, 0, 0.1);
}

.tab.active {
    background-color: rgba(0, 0, 0, 0.7);
    box-shadow: 0 0.25vh 0.5vh rgba(0, 0, 0, 0.2);
}

.property-card {
    max-width: 25vw;
    background-color: #1c2028;
    border-radius: 1.25vh;
    box-shadow: 0 0.25vh 0.5vh rgba(0, 0, 0, 0.1);
    margin: 1.25vh auto;
    padding: 1.25vh;
    color: white;
    transition: transform 0.3s;
    cursor: pointer;
}

.property-card:hover {
    transform: translateY(-0.3125vh);
}

.property-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 0.125vh solid white;
    padding-bottom: 0.625vh;
}

.property-address {
    color: white;
    margin: 0;
    font-size: 1.25vh;
}

.property-icon, .info-icon, .remove-icon, .users-icon {
    font-size: 1.5vh;
    margin-left: 0.625vh;
    color: white;
}

.property-icon:hover, .info-icon:hover, .remove-icon:hover, .users-icon:hover {
    transform: scale(1.2);
    transition: transform 0.3s;
}

.property-info {
    display: flex;
    align-items: center;
    margin-top: 0.625vh;
    justify-content: space-between;
}

.owner-options {
    display: none;
    margin-top: 1.25vh;
}

.add-access-btn {
    background-color: white;
    color: #1c2028;
    border: none;
    border-radius: 3vh;
    width: 3vh; 
    height: 3vh;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: background-color 0.3s;
    margin-bottom: 1vh;
}


.add-access-btn:hover {
    transform: scale(1.2);
    transition: transform 0.3s;
}

.user-input-section {
    display: flex;
    align-items: center;
    gap: 0.625vh;
}

.user-input {
    flex: 1;
    padding: 0.625vh;
    border: 0.0625vh solid #e0e0e0;
    border-radius: 0.3125vh;
    font-size: 1vh;
}

.add-user-section {
    display: flex;
    align-items: center;
    gap: 0.625vh;
}

.access-list li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 0.0625vh solid #e0e0e0;
    padding: 0.3125vh 0;
}

.user-icon {
    margin-right: 0.625vh;
    color: white;
}

.remove-icon {
    margin-left: 0.625vh;
}

.tooltip-inner {
    white-space: pre-wrap;
}

.no-properties-message {
    color: #e0e0e0;
    font-size: 1.125vh;
    text-align: center;
    padding: 1.25vh;
    margin: 1.25vh auto;
    max-width: 25vw;
    background-color: rgba(255, 255, 255, 0.05);
    border-radius: 0.625vh;
    transition: background-color 0.3s;
}

.no-properties-message:hover {
    background-color: rgba(255, 255, 255, 0.1);
}
```
**or replace it with this, if you want light mode:**
```css
@import url('https://fonts.googleapis.com/css?family=Lato&display=swap');

.houses-app {
    display: none;
    height: 100%;
    width: 100%;
    background: #242833;
    overflow: hidden;
}

.house-container {
    padding-top: 4vh !important;
    padding: 1vh;
}

.tabs {
    display: flex;
    justify-content: center;
    margin-bottom: 1vh;
}

.tab {
    background-color: #007BFF;
    color: #fff;
    border: none;
    padding: 0.625vh 1.25vh;
    margin: 0 0.3125vh;
    cursor: pointer;
    border-radius: 0.3125vh;
    transition: background-color 0.3s;
}

.tab:hover {
    background-color: #0056b3;
    transform: translateY(-0.1875vh);
    box-shadow: 0 0.25vh 0.5vh rgba(0, 0, 0, 0.1);
}

.tab.active {
    background-color: #0056b3;
    box-shadow: 0 0.25vh 0.5vh rgba(0, 0, 0, 0.2);
}

.property-card {
    max-width: 25vw;
    background-color: #fff;
    border-radius: 1.25vh;
    box-shadow: 0 0.25vh 0.5vh rgba(0, 0, 0, 0.1);
    margin: 1.25vh auto;
    padding: 1.25vh;
    color: #333;
    transition: transform 0.3s;
    cursor: pointer;
}

.property-card:hover {
    transform: translateY(-0.3125vh);
}

.property-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 0.125vh solid #007BFF;
    padding-bottom: 0.625vh;
}

.property-address {
    color: #007BFF;
    margin: 0;
    font-size: 1.25vh;
}

.property-icon, .info-icon, .remove-icon, .users-icon {
    font-size: 1.5vh;
    margin-left: 0.625vh;
    color: #007BFF;
}

.property-icon:hover, .info-icon:hover, .remove-icon:hover, .users-icon:hover {
    transform: scale(1.2);
    transition: transform 0.3s;
}

.property-info {
    display: flex;
    align-items: center;
    margin-top: 0.625vh;
    justify-content: space-between;
}

.owner-options {
    display: none;
    margin-top: 1.25vh;
}

.add-access-btn {
    background-color: #007BFF;
    color: #fff;
    border: none;
    border-radius: 3vh;
    width: 3vh; 
    height: 3vh;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: background-color 0.3s;
    margin-bottom: 1vh;
}


.add-access-btn:hover {
    background-color: #0056b3;
}

.user-input-section {
    display: flex;
    align-items: center;
    gap: 0.625vh;
}

.user-input {
    flex: 1;
    padding: 0.625vh;
    border: 0.0625vh solid #e0e0e0;
    border-radius: 0.3125vh;
    font-size: 1vh;
}

.add-user-section {
    display: flex;
    align-items: center;
    gap: 0.625vh;
}

.access-list li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 0.0625vh solid #e0e0e0;
    padding: 0.3125vh 0;
}

.user-icon {
    margin-right: 0.625vh;
    color: #007BFF;
}

.remove-icon {
    margin-left: 0.625vh;
}

.tooltip-inner {
    white-space: pre-wrap;
}

.no-properties-message {
    color: #e0e0e0;
    font-size: 1.125vh;
    text-align: center;
    padding: 1.25vh;
    margin: 1.25vh auto;
    max-width: 25vw;
    background-color: rgba(255, 255, 255, 0.05);
    border-radius: 0.625vh;
    transition: background-color 0.3s;
}

.no-properties-message:hover {
    background-color: rgba(255, 255, 255, 0.1);
}

```
# Add this to ps-housing
## client/client.lua
```lua
function HouseTrack(propertyId)
    local coords

    if PropertiesTable[propertyId].propertyData.apartment ~= nil then
        local getConfigName = PropertiesTable[propertyId].propertyData.apartment
        coords = Config.Apartments[getConfigName].door
    else
        coords = PropertiesTable[propertyId].propertyData.door_data
    end

    SetNewWaypoint(coords.x, coords.y)
end

exports("HouseTrack", HouseTrack)
```

## server/server.lua
```lua
lib.callback.register("ps-housing:server:GetPlayerProperties", function(source)
    local Player = QBCore.Functions.GetPlayer(source)
    local Properties = {}
    local citizenid = Player.PlayerData.citizenid

    while dbloaded == false do
        Wait(2000)
    end

    for _, v in pairs(PropertiesTable) do
        local propertyData = v.propertyData

        while not propertyData do
            Wait(500)
        end

        local checkAccess = lib.table.contains(propertyData.has_access, citizenid)
        if propertyData.owner == citizenid or checkAccess then
            local fullName = ""
            local Haccess = false
            local streeto

            if propertyData.street == nil and propertyData.apartment ~= nil then
                streeto = propertyData.apartment
            elseif propertyData.street ~= nil then
                streeto = propertyData.street
            else
                streeto = "Something is broken"
            end

            local HouseName = streeto .. " " .. propertyData.property_id
            local checkNum = #propertyData.has_access
            local numAccess = "Shared with: " .. #propertyData.has_access .. " friends"
            
            local getName = QBCore.Functions.GetPlayerByCitizenId(propertyData.owner) or QBCore.Functions.GetOfflinePlayerByCitizenId(propertyData.owner)
            local playerData = getName.PlayerData
            if playerData then
                fullName = playerData.charinfo.firstname .. " " .. playerData.charinfo.lastname
            end

            if propertyData.owner == citizenid then
                if checkNum < 1 then
                    numAccess = "Not shared"
                elseif checkNum == 1 then
                    numAccess = "Shared with: " .. #propertyData.has_access .. " friend"
                else
                    numAccess = "Shared with: " .. #propertyData.has_access .. " friends"
                end
                Haccess = true
            else
                numAccess = "It's not your property"
                Haccess = false
            end

            Properties[#Properties + 1] = {
                fullname = fullName,
                houseName = HouseName,
                shellName = propertyData.shell,
                propertyId = propertyData.property_id,
                has_access = Haccess,
                numAccess = numAccess,
                houseIcon = propertyData.apartment and "fa-home" or "fa-building",
                numAccessNum = #propertyData.has_access,
                garageStatus = propertyData.garage_data.x and "Have garage" or "Doesn't have garage"
            }
            print("garage_data: ", propertyData.garage_data.x)
        end
    end
    return Properties
end)
```
