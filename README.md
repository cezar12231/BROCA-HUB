local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/jensonhirst/Orion/main/source')))()

local Window = OrionLib:MakeWindow({Name = "Broca Hub | Ajustado por Cezar", HidePremium = false, SaveConfig = false, IntroText = "Broca Hub"})

local MainTab = Window:MakeTab({
    Name = "Funções",
    Icon = "rbxassetid://4483345998",
    PremiumOnly = false
})

-- Função para esperar menos tempo para rodar mais rápido
local function waitFast()
    task.wait(0.1) -- tempo menor entre as ações, cuidado para não travar o jogo/ser detectado
end

MainTab:AddToggle({
    Name = "Broca Infinita",
    Default = false,
    Callback = function(Value)
        _G.InfBroca = Value
        spawn(function()
            while _G.InfBroca do
                local args = {[1] = 11}
                local success, err = pcall(function()
                    game:GetService("ReplicatedStorage").Packages.Knit.Services.GiftService.RF.ClaimGift:InvokeServer(unpack(args))
                end)
                if not success then
                    warn("Erro ao tentar Broca Infinita:", err)
                end
                waitFast()
            end
        end)
    end
})

MainTab:AddToggle({
    Name = "Dinheiro Infinito",
    Default = false,
    Callback = function(Value)
        _G.InfMoney = Value
        spawn(function()
            while _G.InfMoney do
                local args = {[1] = 10}
                local success, err = pcall(function()
                    game:GetService("ReplicatedStorage").Packages.Knit.Services.GiftService.RF.ClaimGift:InvokeServer(unpack(args))
                end)
                if not success then
                    warn("Erro ao tentar Dinheiro Infinito:", err)
                end
                waitFast()
            end
        end)
    end
})

MainTab:AddToggle({
    Name = "Auto Comprar Torre",
    Default = false,
    Callback = function(Value)
        _G.AutoTorre = Value
        spawn(function()
            while _G.AutoTorre do
                local args = {
                    [1] = {
                        ["kind"] = "purchase",
                        ["what"] = "1LevelTower"
                    }
                }
                local success, err = pcall(function()
                    game:GetService("ReplicatedStorage").Packages.Knit.Services.TowerService.RE.remote:FireServer(unpack(args))
                end)
                if not success then
                    warn("Erro ao tentar Auto Torre:", err)
                end
                waitFast()
            end
        end)
    end
})

MainTab:AddButton({
    Name = "Pegar 5 Pets OP",
    Callback = function()
        spawn(function()
            for i = 1, 5 do
                local args = {[1] = 12}
                local success, err = pcall(function()
                    game:GetService("ReplicatedStorage").Packages.Knit.Services.GiftService.RF.ClaimGift:InvokeServer(unpack(args))
                end)
                if not success then
                    warn("Erro ao pegar Pet OP:", err)
                end
                waitFast()
            end
        end)
    end
})

OrionLib:MakeNotification({
    Name = "Créditos",
    Content = "Script ajustado por Cezar. Todos os textos traduzidos para português.",
    Time = 5
})
