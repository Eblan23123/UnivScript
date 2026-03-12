-- [[ DARK SOUL V1: FINAL STABLE REBUILD ]] --
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local UIS = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local TweenService = game:GetService("TweenService")
local camera = workspace.CurrentCamera
local mouse = player:GetMouse()

local CORRECT_KEY = "DarJKGyvsKfwe-3i"
local KEY_LINK = "https://link-target.net/4164566/kBdEjDTjl7fJ"

_G.WS = 16
_G.JP = 50
_G.ESP = false
_G.AIM = false
_G.INF_JUMP = false

local sg = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
sg.Name = "DS_Final_V4"

-- --- ЛОАДЕР И РЕКЛАМА ---
local loader = Instance.new("Frame", sg)
loader.Size = UDim2.new(0, 350, 0, 250)
loader.Position = UDim2.new(0.5, -175, 0.5, -125)
loader.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
Instance.new("UIStroke", loader).Color = Color3.new(1, 0, 0)
Instance.new("UICorner", loader)

local lTitle = Instance.new("TextLabel", loader)
lTitle.Size = UDim2.new(1, 0, 0, 50)
lTitle.Text = "DARK SOUL V1 | KEY SYSTEM"
lTitle.TextColor3 = Color3.new(1, 0, 0)
lTitle.Font = Enum.Font.GothamBold
lTitle.BackgroundTransparency = 1

local kInput = Instance.new("TextBox", loader)
kInput.Size = UDim2.new(0, 280, 0, 40)
kInput.Position = UDim2.new(0.5, -140, 0, 80)
kInput.PlaceholderText = "Paste Key Here..."
kInput.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
kInput.TextColor3 = Color3.new(1, 1, 1)

local copyBtn = Instance.new("TextButton", loader)
copyBtn.Size = UDim2.new(0, 130, 0, 40)
copyBtn.Position = UDim2.new(0.5, -140, 0, 140)
copyBtn.Text = "COPY LINK"
copyBtn.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
copyBtn.TextColor3 = Color3.new(1, 1, 1)
copyBtn.MouseButton1Click:Connect(function() 
    setclipboard(KEY_LINK) 
    copyBtn.Text = "COPIED!" 
    task.wait(2) 
    copyBtn.Text = "COPY LINK" 
end)

local logBtn = Instance.new("TextButton", loader)
logBtn.Size = UDim2.new(0, 130, 0, 40)
logBtn.Position = UDim2.new(0.5, 10, 0, 140)
logBtn.Text = "LOGIN"
logBtn.BackgroundColor3 = Color3.new(0.7, 0, 0)
logBtn.TextColor3 = Color3.new(1, 1, 1)

-- --- МЕНЮ ---
local main = Instance.new("Frame", sg)
main.Size = UDim2.new(0, 550, 0, 400)
main.Position = UDim2.new(0.5, -275, 0.5, -200)
main.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
main.Visible = false
main.Active = true
main.Draggable = true
Instance.new("UIStroke", main).Color = Color3.new(1, 0, 0)

-- [ SLIDERS ] --
local function createSlider(txt, y, var, min, max)
    local sFrame = Instance.new("Frame", main)
    sFrame.Size = UDim2.new(0, 220, 0, 50)
    sFrame.Position = UDim2.new(0, 15, 0, y)
    sFrame.BackgroundTransparency = 1

    local label = Instance.new("TextLabel", sFrame)
    label.Size = UDim2.new(1, 0, 0, 20)
    label.Text = txt .. ": " .. _G[var]
    label.TextColor3 = Color3.new(1, 1, 1)
    label.BackgroundTransparency = 1
    label.TextXAlignment = Enum.TextXAlignment.Left

    local rail = Instance.new("Frame", sFrame)
    rail.Size = UDim2.new(1, 0, 0, 8)
    rail.Position = UDim2.new(0, 0, 0, 25)
    rail.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    
    local fill = Instance.new("Frame", rail)
    fill.Size = UDim2.new((_G[var] - min) / (max - min), 0, 1, 0)
    fill.BackgroundColor3 = Color3.new(1, 0, 0)
    fill.BorderSizePixel = 0

    local trigger = Instance.new("TextButton", rail)
    trigger.Size = UDim2.new(1, 0, 1, 0)
    trigger.BackgroundTransparency = 1
    trigger.Text = ""

    local dragging = false
    trigger.MouseButton1Down:Connect(function() dragging = true end)
    UIS.InputEnded:Connect(function(i) if i.UserInputType == Enum.UserInputType.MouseButton1 then dragging = false end end)
    
    RunService.RenderStepped:Connect(function()
        if dragging then
            local percent = math.clamp((mouse.X - rail.AbsolutePosition.X) / rail.AbsoluteSize.X, 0, 1)
            fill.Size = UDim2.new(percent, 0, 1, 0)
            _G[var] = math.floor(min + (max - min) * percent)
            label.Text = txt .. ": " .. _G[var]
        end
    end)
end

local function createToggle(txt, y, var)
    local b = Instance.new("TextButton", main)
    b.Size = UDim2.new(0, 220, 0, 40)
    b.Position = UDim2.new(0, 15, 0, y)
    b.Text = txt .. ": OFF"
    b.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
    b.TextColor3 = Color3.new(1, 1, 1)
    Instance.new("UICorner", b)
    b.MouseButton1Click:Connect(function()
        _G[var] = not _G[var]
        b.Text = txt .. (_G[var] and ": ON" or ": OFF")
        b.BackgroundColor3 = _G[var] and Color3.new(0.6, 0, 0) or Color3.fromRGB(25, 25, 25)
    end)
end

createSlider("WalkSpeed", 50, "WS", 16, 500)
createSlider("JumpPower", 110, "JP", 50, 500)
createToggle("ESP Master", 170, "ESP")
createToggle("Rage Aimbot", 220, "AIM")
createToggle("Infinity Jump", 270, "INF_JUMP")

-- --- ТЕЛЕПОРТ (SAFE TWEEN) ---
local tpList = Instance.new("ScrollingFrame", main)
tpList.Size = UDim2.new(0, 280, 0, 310)
tpList.Position = UDim2.new(0, 250, 0, 50)
tpList.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
Instance.new("UIListLayout", tpList).Padding = UDim.new(0, 5)

local function safeTeleport(targetP)
    if targetP.Character and targetP.Character:FindFirstChild("HumanoidRootPart") then
        local targetPos = targetP.Character.HumanoidRootPart.CFrame
        local tween = TweenService:Create(player.Character.HumanoidRootPart, TweenInfo.new(0.5, Enum.EasingStyle.Linear), {CFrame = targetPos})
        tween:Play()
    end
end

local function refreshTP()
    for _, v in pairs(tpList:GetChildren()) do if v:IsA("TextButton") then v:Destroy() end end
    for _, p in pairs(Players:GetPlayers()) do
        if p ~= player then
            local b = Instance.new("TextButton", tpList)
            b.Size = UDim2.new(1, -10, 0, 30)
            b.Text = "SAFE TP: " .. p.DisplayName
            b.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
            b.TextColor3 = Color3.new(1, 1, 1)
            b.MouseButton1Click:Connect(function() safeTeleport(p) end)
        end
    end
end
RunService.Heartbeat:Connect(function() if math.random(1, 100) == 1 then refreshTP() end end)

-- --- ЛОГИКА ESP (FULL INFO) ---
RunService.Heartbeat:Connect(function()
    for _, v in pairs(Players:GetPlayers()) do
        if v ~= player and v.Character and v.Character:FindFirstChild("HumanoidRootPart") then
            local root = v.Character.HumanoidRootPart
            local hum = v.Character:FindFirstChild("Humanoid")
            
            local gui = sg:FindFirstChild("E_"..v.Name) or Instance.new("BillboardGui", sg)
            gui.Name = "E_"..v.Name
            gui.Adornee = root
            gui.Size = UDim2.new(0, 150, 0, 70)
            gui.AlwaysOnTop = true
            gui.StudsOffset = Vector3.new(0, 4, 0)
            gui.Enabled = _G.ESP

            local nameL = gui:FindFirstChild("N") or Instance.new("TextLabel", gui)
            nameL.Name = "N"
            nameL.Size = UDim2.new(1, 0, 0, 20)
            nameL.BackgroundTransparency = 1
            nameL.TextColor3 = Color3.new(1, 1, 1)
            nameL.Font = Enum.Font.GothamBold
            nameL.TextSize = 14
            
            local bar = gui:FindFirstChild("B") or Instance.new("Frame", gui)
            bar.Name = "B"
            bar.Size = UDim2.new(0.8, 0, 0, 6)
            bar.Position = UDim2.new(0.1, 0, 0, 30)
            bar.BackgroundColor3 = Color3.new(0, 0, 0)
            
            local fill = bar:FindFirstChild("F") or Instance.new("Frame", bar)
            fill.Name = "F"
            fill.BorderSizePixel = 0
            
            if _G.ESP and hum then
                local d = math.floor((player.Character.HumanoidRootPart.Position - root.Position).Magnitude)
                nameL.Text = v.DisplayName .. " [" .. d .. "m]"
                fill.Size = UDim2.new(math.clamp(hum.Health / hum.MaxHealth, 0, 1), 0, 1, 0)
                fill.BackgroundColor3 = Color3.new(1, 0, 0):Lerp(Color3.new(0, 1, 0), hum.Health / hum.MaxHealth)
            end
        end
    end
end)

-- РАБОТА ФУНКЦИЙ
RunService.RenderStepped:Connect(function()
    if player.Character and player.Character:FindFirstChild("Humanoid") then
        player.Character.Humanoid.WalkSpeed = _G.WS
        player.Character.Humanoid.JumpPower = _G.JP
        player.Character.Humanoid.UseJumpPower = true
    end
    if _G.AIM and UIS:IsMouseButtonPressed(Enum.UserInputType.MouseButton2) then
        local target = nil local dist = 1000
        for _, v in pairs(Players:GetPlayers()) do
            if v ~= player and v.Character and v.Character:FindFirstChild("Head") then
                local pos, onS = camera:WorldToViewportPoint(v.Character.Head.Position)
                if onS then
                    local m = (Vector2.new(UIS:GetMouseLocation().X, UIS:GetMouseLocation().Y) - Vector2.new(pos.X, pos.Y)).Magnitude
                    if m < dist then dist = m target = v.Character.Head end
                end
            end
        end
        if target then camera.CFrame = CFrame.new(camera.CFrame.Position, target.Position) end
    end
end)

UIS.JumpRequest:Connect(function() if _G.INF_JUMP then player.Character.Humanoid:ChangeState("Jumping") end end)
logBtn.MouseButton1Click:Connect(function() if kInput.Text == CORRECT_KEY then loader:Destroy() main.Visible = true end end)
UIS.InputBegan:Connect(function(i, g) if not g and i.KeyCode == Enum.KeyCode.P then main.Visible = not main.Visible end end)
