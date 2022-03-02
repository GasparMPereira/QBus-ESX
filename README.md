# QBus-ESX
Convertion QBus to ESX ( Guide )

--------------------------------------------------------------------------------------------------
Fundação Qbus e fundação ESX.
 ```lua
QBCore = nil 

Citizen.CreateThread(function()
	while QBCore == nil do
		TriggerEvent('QBCore:GetObject', function(obj) QBCore = obj end)
		Citizen.Wait(30) -- Saniye Bekletme
	end
end)
```
Para os novos na parte inferior - para a versão antiga na parte superior, se não funcionar, tente os dois ...
```lua
local QBCore = exports['qb-core']:GetCoreObject()
```

# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
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

Beyler Bu kısım Yoktu eklendi.
Anlamı:
Oyuncu Giriş Kısmı İlik Oyuna Girerken Lazım, Yani Server Dosyasıdır.
Bu olay, oyuncu sunucuya bağlandığında tetiklenir
```lua
RegisterNetEvent('QBCore:Client:OnPlayerLoaded')
AddEventHandler('QBCore:Client:OnPlayerLoaded',
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
RegisterNetEvent('esx:playerLoaded')
AddEventHandler('esx:playerLoaded',
```

--------------------------------------------------------------------------------------------------

Server Dosyası, Job Kısmı Meslek Kısmıdır.
```lua
RegisterNetEvent('QBCore:Client:OnJobUptade')
AddEventHandler('QBCore:Client:OnJobUptade', 
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
RegisterNetEvent('esx:setJob')
AddEventHandler('esx:setJob',
```

--------------------------------------------------------------------------------------------------

Burdan Kontrol Edebilrsiniz.
https://esx-framework.github.io/es_extended/common/events/onplayerdeath/#example-client-side-usage
```lua
RegisterNetEvent('QBCore:Client:OnPlayerUnload')
AddEventHandler('QBCore:Client:OnPlayerUnload',
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
RegisterNetEvent('esx:onPlayerDeath')
AddEventHandler('esx:onPlayerDeath',
```

--------------------------------------------------------------------------------------------------

Beyler Bu kısım Yoktu eklendi.
Anlamı:
Bu işlev, en yakın oyuncu istemci kimliğini ve oynatıcıya olan mesafeyi alır.
```lua
QBCore.Functions.GetClosestPlayer()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.Game.GetClosestPlayer()
```

--------------------------------------------------------------------------------------------------

3D li Yazı Ekleme, Cilent Dosyası. Örnek : https://media.discordapp.net/attachments/623207764314816562/812096508786507806/resim_1.png
```lua
QBCore.Functions.DrawText3D(1, 1, 1, 'Örnek')
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
DrawText3D(1, 1, 1, 'Örnek') -- (aşağısına function açmanız gerekmektedir.)
ESX.Game.Utils.DrawText3D(1, 1, 1, 'Örnek') -- ESX bunda gerek yok zaten var, fonksiyona.
```

--------------------------------------------------------------------------------------------------

Menu Aç Kapat ESX & QBCore De Ki Menüler Örnekler : https://prnt.sc/u4f7s5
```lua
QBCore.UI.Menu.Open
QBCore.UI.Menu.CloseAll() -- (menu default scripti kurmanız gerekmektedir.)
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.UI.Menu.Open
ESX.UI.Menu.CloseAll()
```

--------------------------------------------------------------------------------------------------

Bildirim Scripti Örnek : https://dosya.turkmmo.com/2020/09/36521_efa54848705a4069cbedfc2770e50cf1.png
```lua
QBCore.Functions.Notify("Araç kitlendi.", "error")
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
TriggerEvent('Notification',"Örnek.")
```

--------------------------------------------------------------------------------------------------

Enventer İtem Kısmı.
```lua
xPlayer.Functions.GetItemByName 
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
xPlayer.getInventoryItem
```
--------------------------------------------------------------------------------------------------

Enventer İtem Kısmı.
```lua
xPlayer.Functions.GetItemByName 
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
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
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
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
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
xPlayer.removeAccountMoney('bank', amount) --para kaldırma
xPlayer.addMoney(amount) -- para ekleme
```

--------------------------------------------------------------------------------------------------

Para Kısmı Data.
```lua
Player.PlayerData.money["bank"]
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
xPlayer.getAccount('bank').money
```

--------------------------------------------------------------------------------------------------

Envanter İtem Silme Kısmı.
```lua
xPlayer.Functions.RemoveItem 
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
xPlayer.removeInventoryItem 
```

--------------------------------------------------------------------------------------------------

Envanter İtem Ekleme Kısmı.
```lua
xPlayer.Functions.AddItem
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
xPlayer.addInventoryItem
```

--------------------------------------------------------------------------------------------------

Karakter Kımsı Oyuncunun İd Si Gibi Birşey.
```lua
QBCore.Functions.GetPlayer(src)
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.GetPlayerFromId(src)
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetPlayerByCitizenId(src)
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
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
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
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
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
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
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
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
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.GetPlayerData()
```

--------------------------------------------------------------------------------------------------

İtem Oluşturma.
```lua
QBCore.Functions.CreateUseableItem()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.RegisterUsableItem()
```

--------------------------------------------------------------------------------------------------

Banka Para Kaldırma.
```lua
Player.Functions.RemoveMoney()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
xPlayer.removeMoney(money)
```

--------------------------------------------------------------------------------------------------

Dosya'lar İle Alakalı.
```lua
QBCore.Functions.CreateCallback()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.RegisterServerCallback()
```

--------------------------------------------------------------------------------------------------

Dosya'lar İle Alakalı.
```lua
QBCore.Functions.TriggerCallback()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
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
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
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
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.GetItems()
```
--------------------------------------------------------------------------------------------------

Sql bağlama kısmı
```lua
QBCore.Functions.ExecuteSql()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.ExecuteSql() --(ghmattimysql)
MySQL.Async.execute()
```

--------------------------------------------------------------------------------------------------


RegisterCommand - yani chat komut kısmı.
```lua
QBCore.Commands.Add()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
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
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
local user = ESX.GetPlayerFromId(src)
["@identifier"] = user.identifier -- çekme user
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Shared.Trim()
QBCore.Shared.GroupDigits()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.Math.Trim()
ESX.Math.GroupDigits()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetClosestObject()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.Game.GetClosestObject()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetVehicleInDirection()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.Game.GetVehicleInDirection()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetPeds()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.Game.GetPeds()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetObjects()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.Game.GetObjects()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetClosestPed()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.Game.GetClosestPed()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.SpawnObject()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.Game.SpawnObject()
```

--------------------------------------------------------------------------------------------------
