### Razers Stuff
This is a fork of LegacyFuel that I made for a project. Only real major changes that I made from the original resource was implementing ox_lib notifications and Text UI's which somehow some way optimized the resource significantly (down from around a 0.07 resmon to a (0.00-0.01 inactive and a 0.03 active)


### Changes I made
```
1.) The original LegacyFuel also had an issue where sitting in a vehicle would raise CPU msec's to around a 0.06. That is fixed on this version.
2.) Updated from a resource.lua to a fxmanifest.lua
3.) Switched all 3d texts to ox_lib UI's and notifications (Not working on the ESX config due to the needs of the project)

```

### About
Started off as my first script, and for whatever reason, I decided to release it. As it was pretty badly created, I felt like I should rewrite it and make a better version, so ended up spending a few hours doing so.

### Installation
1) Download the latest version in the "code" tab on GitHub.
2) Drag & drop the folder into your `resources` server folder.
3) Configure the config file to your liking.
4) Add `start LegacyFuel` to your server config.

### Exports
There are currently two (client-sided) exports available, which should help you control the fuel level for vehicles whenever needed.

```
SetFuel(vehicle --[[ Vehicle ]], value --[[ Number: (0-100) ]])
GetFuel(vehicle --[[ Vehicle ]]) -- Returns the vehicle's fuel level.
```

**Example usage:**
```
function SpawnVehicle(modelHash)
    local vehicle = CreateVehicle(modelHash, coords.x, coords.y, coords.z, true, false)

    exports["LegacyFuel"]:SetFuel(vehicle, 100)
end

function StoreVehicleInGarage(vehicle)
    local plate = GetVehicleNumberPlateText(vehicle)
    local fuelLevel = exports["LegacyFuel"]:GetFuel(vehicle)

    TriggerServerEvent('vehiclesStored', plate, fuelLevel)
end
```
