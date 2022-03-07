# QBus-ESX
Convertion QBus to ESX ( Guide )

--------------------------------------------------------------------------------------------------
#Get Shared Object
 ```lua
QBCore = nil 

Citizen.CreateThread(function()
	while QBCore == nil do
		TriggerEvent('QBCore:GetObject', function(obj) QBCore = obj end)
		Citizen.Wait(30) -- Saniye Bekletme
	end
end)
```
For news QBus versions ↓ - For older QBus versions ↑, if not working try the two codes ...
```lua
local QBCore = exports['qb-core']:GetCoreObject()
```

↑ QBUS

↓ ESX
```lua
ESX = nil

Citizen.CreateThread(function()
  while ESX == nil do
    TriggerEvent('esx:getSharedObject', function(obj) ESX = obj end)
    Citizen.Wait(30)-- Saniye Bekletme
  end
end)
```

--------------------------------------------------------------------------------------------------

The Player's Input Part is required when entering the game, that is, it is the server file.
This event is triggered when the player connects to the server
#
```lua
RegisterNetEvent('QBCore:Client:OnPlayerLoaded')
AddEventHandler('QBCore:Client:OnPlayerLoaded',
```
↑ QBUS

↓ ESX
```lua
RegisterNetEvent('esx:playerLoaded')
AddEventHandler('esx:playerLoaded',
```

--------------------------------------------------------------------------------------------------

#Server File, Job Part is Occupation Part:
```lua
RegisterNetEvent('QBCore:Client:OnJobUptade')
AddEventHandler('QBCore:Client:OnJobUptade', 
```
↑ QBUS

↓ ESX
```lua
RegisterNetEvent('esx:setJob')
AddEventHandler('esx:setJob',
```

--------------------------------------------------------------------------------------------------

Event when player die:
#
```lua
RegisterNetEvent('QBCore:Client:OnPlayerUnload')
AddEventHandler('QBCore:Client:OnPlayerUnload',
```
# ↑ QBUS

# ↓ ESX
```lua
RegisterNetEvent('esx:onPlayerDeath')
AddEventHandler('esx:onPlayerDeath',
```

--------------------------------------------------------------------------------------------------

This function gets the nearest player client id and distance to the player:
#
```lua
QBCore.Functions.GetClosestPlayer()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.Game.GetClosestPlayer()
```

--------------------------------------------------------------------------------------------------

Adding 3D Text, Cilent File. Example : 
![image](https://user-images.githubusercontent.com/71574610/156451517-fb13d4b5-b4ac-488a-813b-010edef28fa0.png)
#
```lua
QBCore.Functions.DrawText3D(1, 1, 1, 'Example')
```
# ↑ QBUS

# ↓ ESX
```lua
DrawText3D(1, 1, 1, 'Example') -- (You need to open the function below)
ESX.Game.Utils.DrawText3D(1, 1, 1, 'Example') -- ESX doesn't need it, it already exists, the function
```

--------------------------------------------------------------------------------------------------
Open and Close Menu Default. Example : 
![image](https://user-images.githubusercontent.com/71574610/156451674-ea55dbab-d870-4ec1-a8aa-93ea4f45c037.png)

```lua
QBCore.UI.Menu.Open
QBCore.UI.Menu.CloseAll() -- (menu default scripti kurmanız gerekmektedir.)
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.UI.Menu.Open
ESX.UI.Menu.CloseAll()
```

--------------------------------------------------------------------------------------------------

Bildirim Scripti Örnek : https://dosya.turkmmo.com/2020/09/36521_efa54848705a4069cbedfc2770e50cf1.png
```lua
QBCore.Functions.Notify("Araç kitlendi.", "error")
```
# ↑ QBUS

# ↓ ESX
```lua
TriggerEvent('Notification',"Örnek.")
```

--------------------------------------------------------------------------------------------------

Enventer İtem Kısmı.
```lua
xPlayer.Functions.GetItemByName 
```
# ↑ QBUS

# ↓ ESX
```lua
xPlayer.getInventoryItem
```
--------------------------------------------------------------------------------------------------

Enventer İtem Kısmı.
```lua
xPlayer.Functions.GetItemByName 
```
# ↑ QBUS

# ↓ ESX
```lua
xPlayer.getInventoryItem
```

--------------------------------------------------------------------------------------------------

Job Başlangıç kod.
```lua
RegisterNetEvent('QBCore:Client:OnJobUpdate')
AddEventHandler('QBCore:Client:OnJobUpdate', function(job)
    PlayerData.job = job
end)
```
# ↑ QBUS

# ↓ ESX
```lua
RegisterNetEvent('esx:setJob')
AddEventHandler('esx:setJob', function(job)
    PlayerData.job = job
end)
```

--------------------------------------------------------------------------------------------------

Para Ver Para Al Kısmı
```lua
Player.Functions.AddMoney('bank', amount, "Bank depost") -- banka
Player.Functions.RemoveMoney('cash', amount, "Bank depost") -- üstündeki para
```
# ↑ QBUS

# ↓ ESX
```lua
xPlayer.removeAccountMoney('bank', amount) --para kaldırma
xPlayer.addMoney(amount) -- para ekleme
```

--------------------------------------------------------------------------------------------------

Para Kısmı Data.
```lua
Player.PlayerData.money["bank"]
```
# ↑ QBUS

# ↓ ESX
```lua
xPlayer.getAccount('bank').money
```

--------------------------------------------------------------------------------------------------

Envanter İtem Silme Kısmı.
```lua
xPlayer.Functions.RemoveItem 
```
# ↑ QBUS

# ↓ ESX
```lua
xPlayer.removeInventoryItem 
```

--------------------------------------------------------------------------------------------------

Envanter İtem Ekleme Kısmı.
```lua
xPlayer.Functions.AddItem
```
# ↑ QBUS

# ↓ ESX
```lua
xPlayer.addInventoryItem
```

--------------------------------------------------------------------------------------------------

Karakter Kımsı Oyuncunun İd Si Gibi Birşey.
```lua
QBCore.Functions.GetPlayer(src)
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.GetPlayerFromId(src)
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetPlayerByCitizenId(src)
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.GetPlayerFromIdentifier(src)
```

--------------------------------------------------------------------------------------------------

Bu işlev, tüm sondaki beyaz boşlukları kaldırarak bir metni kırpar. Genellikle `GetVehicleNumberPlateText()` yerlileri dezenfekte ederken kullanılır.
#örnek
```lua
QBCore.Functions.MathTrim(GetVehicleNumberPlateText(vehicle))
````
#standart
```lua
QBCore.Functions.MathTrim 
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.Math.Trim(value)
```

--------------------------------------------------------------------------------------------------

Nill buşta bilinmiyor güncelencek
# ÖRNEK
```lua
QBCore.Functions.MathRound(GetVehicleBodyHealth(vehicle), 1),
```
#standart
```lua
QBCore.Functions.MathRound()
```
# ↑ QBUS

# ↓ ESX
# ÖRNEK
```lua
local deger - 5.444

print ('deger:' .. değer) - 5.444 -- döndürür
print ('deger yuvarlandı:' .. ESX.Math.Round(deger)) -- 5 döndürür
print ('deger yuvarlandı:' .. ESX.Math.Round(deger, 1)) -- 5,4 döndürür
```
#standart
```lua
ESX.Math.Round(değer, numaraOndalıkBasamaklar)
```

--------------------------------------------------------------------------------------------------

Araba Spawn Kısmı Konumu Vsb Şeyler.
```lua
QBCore.Functions.SpawnVehicle()
QBCore.Functions.DeleteVehicle()
QBCore.Functions.GetVehicleProperties()
QBCore.Functions.GetClosestVehicle()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.Game.SpawnVehicle()
ESX.Game.DeleteVehicle()
ESX.Game.GetVehicleProperties()
ESX.Game.GetClosestVehicle()
```
--(Eğer ESX.Game olan neredeyse her şey QBCore.Functions olarak aynı şekildedir.)

--------------------------------------------------------------------------------------------------

Oyuncu Kendi Karakterin.
```lua
QBCore.Functions.GetPlayerData()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.GetPlayerData()
```

--------------------------------------------------------------------------------------------------

İtem Oluşturma.
```lua
QBCore.Functions.CreateUseableItem()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.RegisterUsableItem()
```

--------------------------------------------------------------------------------------------------

Banka Para Kaldırma.
```lua
Player.Functions.RemoveMoney()
```
# ↑ QBUS

# ↓ ESX
```lua
xPlayer.removeMoney(money)
```

--------------------------------------------------------------------------------------------------

Dosya'lar İle Alakalı.
```lua
QBCore.Functions.CreateCallback()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.RegisterServerCallback()
```

--------------------------------------------------------------------------------------------------

Dosya'lar İle Alakalı.
```lua
QBCore.Functions.TriggerCallback()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.TriggerServerCallback()
```

--------------------------------------------------------------------------------------------------

qb'de cid esx'de identifier kullanılıyor olayı çözmeniz için ufak bir kod bloğu bıraktım.
```lua
QBCore.Functions.CreateCallback('system:fetchStatus', function(source, cb)
    local Player = QBCore.Functions.GetPlayer(source)

     if Player then
           exports['ghmattimysql']:execute('SELECT skills FROM players WHERE citizenid = @citizenid', {
               ['@citizenid'] = Player.PlayerData.citizenid
          }, function(status)
              if status ~= nil then
                   cb(json.decode(status))
              else
                   cb(nil)
              end
          end)
     else
          cb()
     end
end)
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.RegisterServerCallback("system:fetchStatus", function(source, cb)
    local src = source
    local user = ESX.GetPlayerFromId(src)


    local fetch = [[
         SELECT
              skills
         FROM
              users
         WHERE
              identifier = @identifier
    ]]

    MySQL.Async.fetchScalar(fetch, {
         ["@identifier"] = user.identifier

    }, function(status)

         if status ~= nil then
              cb(json.decode(status))
         else
              cb(nil)
         end

    end)
end)
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Shared.Items
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.GetItems()
```
--------------------------------------------------------------------------------------------------

Sql bağlama kısmı
```lua
QBCore.Functions.ExecuteSql()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.ExecuteSql() --(ghmattimysql)
MySQL.Async.execute()
```

--------------------------------------------------------------------------------------------------


RegisterCommand - yani chat komut kısmı.
```lua
QBCore.Commands.Add()
```
# ↑ QBUS

# ↓ ESX
```lua
RegisterCommand 
```
-- (RegisterCommand qbcore'da da çalışır.)

--------------------------------------------------------------------------------------------------

Karakter Kısmı Dır Data Sına Bağlama.
```lua
local Player = QBCore.Functions.GetPlayer(source)
['@citizenid'] = Player.PlayerData.citizenid -- çekme Player
```
# ↑ QBUS

# ↓ ESX
```lua
local user = ESX.GetPlayerFromId(src)
["@identifier"] = user.identifier -- çekme user
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Shared.Trim()
QBCore.Shared.GroupDigits()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.Math.Trim()
ESX.Math.GroupDigits()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetClosestObject()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.Game.GetClosestObject()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetVehicleInDirection()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.Game.GetVehicleInDirection()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetPeds()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.Game.GetPeds()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetObjects()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.Game.GetObjects()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetClosestPed()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.Game.GetClosestPed()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.SpawnObject()
```
# ↑ QBUS

# ↓ ESX
```lua
ESX.Game.SpawnObject()
```

--------------------------------------------------------------------------------------------------
