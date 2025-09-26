shared.LoaderTitle = "جار تحميل سكربت F4M HUB";
shared.LoaderKeyFrames = {
    [1] = {1, 20},
    [2] = {2, 50},
    [3] = {3, 80},
    [4] = {2, 100}
};
local v2 = {
    LoaderData = {
        Name = shared.LoaderTitle or "A Loader",
        Colors = shared.LoaderColors or {
            Main = Color3.fromRGB(0, 0, 0),
            Topic = Color3.fromRGB(7, 167, 0),
            Title = Color3.fromRGB(7, 167, 0),
            LoaderBackground = Color3.fromRGB(255, 255, 255),
            LoaderSplash = Color3.fromRGB(7, 167, 0)
        }
    },
    Keyframes = shared.LoaderKeyFrames or {
        [1] = {1, 10},
        [2] = {2, 30},
        [3] = {3, 60},
        [4] = {2, 100}
    }
};
local v3 = {
    [1] = "",
    [2] = "",
    [3] = "",
    [4] = ""
};
function TweenObject(v178, v179, v180)
    game.TweenService:Create(v178, TweenInfo.new(v179, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), v180):Play();
end
function CreateObject(v181, v182)
    local v183 = Instance.new(v181);
    local v184;
    for v416, v417 in pairs(v182) do
        if (v416 ~= "Parent") then
            v183[v416] = v417;
        else
            v184 = v417;
        end
    end
    v183.Parent = v184;
    return v183;
end
local function v4(v186, v187)
    local v188 = Instance.new("UICorner");
    v188.CornerRadius = UDim.new(0, v186);
    v188.Parent = v187;
end
local v5 = CreateObject("ScreenGui", {
    Name = "Core",
    Parent = game.CoreGui
});

-- 🔊 إضافة الصوت مع بداية الانترو
local sound = Instance.new("Sound")
sound.SoundId = "rbxassetid://9086208751"
sound.Volume = 1
sound.Looped = false
sound.Parent = v5
sound:Play()

local v6 = CreateObject("Frame", {
    Name = "Main",
    Parent = v5,
    BackgroundColor3 = v2.LoaderData.Colors.Main,
    BorderSizePixel = 0,
    ClipsDescendants = true,
    Position = UDim2.new(0.5, 0, 0.5, 0),
    AnchorPoint = Vector2.new(0.5, 0.5),
    Size = UDim2.new(0, 0, 0, 0)
});
v4(12, v6);
local v7 = CreateObject("ImageLabel", {
    Name = "UserImage",
    Parent = v6,
    BackgroundTransparency = 1,
    Image = "rbxassetid://114402042471909",
    Position = UDim2.new(0, 15, 0, 10),
    Size = UDim2.new(0, 55, 0, 55)
});
v4(25, v7);
local v8 = CreateObject("TextLabel", {
    Name = "UserName",
    Parent = v6,
    BackgroundTransparency = 1,
    Text = "by: Shadow",
    Position = UDim2.new(0, 75, 0, 10),
    Size = UDim2.new(0, 200, 0, 50),
    Font = Enum.Font.GothamBold,
    TextColor3 = v2.LoaderData.Colors.Title,
    TextSize = 14,
    TextXAlignment = Enum.TextXAlignment.Left
});
local v9 = CreateObject("TextLabel", {
    Name = "Top",
    TextTransparency = 1,
    Parent = v6,
    BackgroundColor3 = Color3.fromRGB(255, 255, 255),
    BackgroundTransparency = 1,
    Position = UDim2.new(0, 30, 0, 70),
    Size = UDim2.new(0, 301, 0, 20),
    Font = Enum.Font.Gotham,
    Text = "Loader",
    TextColor3 = v2.LoaderData.Colors.Topic,
    TextSize = 10,
    TextXAlignment = Enum.TextXAlignment.Left
});
local v10 = CreateObject("TextLabel", {
    Name = "Title",
    Parent = v6,
    TextTransparency = 1,
    BackgroundColor3 = Color3.fromRGB(255, 255, 255),
    BackgroundTransparency = 1,
    Position = UDim2.new(0, 30, 0, 90),
    Size = UDim2.new(0, 301, 0, 46),
    Font = Enum.Font.Gotham,
    RichText = true,
    Text = "<b>" .. v2.LoaderData.Name .. "</b>",
    TextColor3 = v2.LoaderData.Colors.Title,
    TextSize = 14,
    TextXAlignment = Enum.TextXAlignment.Left
});
local v11 = CreateObject("Frame", {
    Name = "BG",
    Parent = v6,
    AnchorPoint = Vector2.new(0.5, 0),
    BackgroundTransparency = 1,
    BackgroundColor3 = v2.LoaderData.Colors.LoaderBackground,
    BorderSizePixel = 0,
    Position = UDim2.new(0.5, 0, 0, 70),
    Size = UDim2.new(0.85, 0, 0, 24)});
v4(8, v11);
local v12 = CreateObject("Frame", {
    Name = "Progress",
    Parent = v11,
    BackgroundColor3 = v2.LoaderData.Colors.LoaderSplash,
    BackgroundTransparency = 1,
    BorderSizePixel = 0,
    Size = UDim2.new(0, 0, 0, 24)
});
v4(8, v12);
local v13 = CreateObject("TextLabel", {
    Name = "StepLabel",
    Parent = v6,
    BackgroundTransparency = 1,
    Position = UDim2.new(0.5, 0, 1, -25),
    Size = UDim2.new(1, -20, 0, 20),
    Font = Enum.Font.Gotham,
    Text = "",
    TextColor3 = v2.LoaderData.Colors.Topic,
    TextSize = 14,
    TextXAlignment = Enum.TextXAlignment.Center,
    AnchorPoint = Vector2.new(0.5, 0.5)
});
function UpdateStepText(v191)
    v13.Text = v3[v191] or "" ;
end
function UpdatePercentage(v193, v194)
    TweenObject(v12, 0.5, {
        Size = UDim2.new(v193 / 100, 0, 0, 24)
    });
    UpdateStepText(v194);
end
TweenObject(v6, 0.25, {Size = UDim2.new(0, 346, 0, 121)});
wait();
TweenObject(v9, 0.5, {TextTransparency = 0});
TweenObject(v10, 0.5, {TextTransparency = 0});
TweenObject(v11, 0.5, {BackgroundTransparency = 0});
TweenObject(v12, 0.5, {BackgroundTransparency = 0});
for v195, v196 in pairs(v2.Keyframes) do
    wait(v196[1]);
    UpdatePercentage(v196[2], v195);
end
UpdatePercentage(100, 4);
TweenObject(v9, 0.5, {TextTransparency = 1});
TweenObject(v10, 0.5, {TextTransparency = 1});
TweenObject(v11, 0.5, {BackgroundTransparency = 1});
TweenObject(v12, 0.5, {BackgroundTransparency = 1});
wait(0.5);
TweenObject(v6, 0.25, {Size = UDim2.new(0, 0, 0, 0)});
wait(0.25);
v5:Destroy();

-- إشعار أول
game.StarterGui:SetCore("SendNotification", {
    Title = "F4M",
    Text = "تم تفعيل سكربت F4M",
    Duration = 3,
    Icon = "rbxassetid://114402042471909"
})

-- إشعار ثاني
game.StarterGui:SetCore("SendNotification", {
    Title = "F4M",
    Text = "استمتع!",
    Duration = 3,
    Icon = "rbxassetid://114402042471909"
})

local args = {
    "RolePlayName",
    "سكربت المطور محمد V1.1"
}
game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1RPNam1eTex1t"):FireServer(unpack(args))

-- تغيير لون الاسم (أحمر غامق)
local args = {
    "PickingRPNameColor",
    Color3.fromRGB(150, 0, 0) -- 🔴 أحمر غامق
}
game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1RPNam1eColo1r"):FireServer(unpack(args))

-- تغيير البايو
local args = {
    "RolePlayBio",
    "بحث سكربت: F4M"
}
game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1RPNam1eTex1t"):FireServer(unpack(args))

-- تغيير لون البايو (أسود غامق)
local args = {
    "PickingRPBioColor",
    Color3.fromRGB(20, 20, 20) -- ⚫ أسود غامق
}
game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1RPNam1eColo1r"):FireServer(unpack(args))


local Libary = loadstring(game:HttpGet("https://raw.githubusercontent.com/youssefhesham542/Y2-Hub/main/Redz%20str"))()
workspace.FallenPartsDestroyHeight = -math.huge

local Window = Libary:MakeWindow({
    Title = "سكربت المطور محمد قائد كلان:  F4M",
    SubTitle = "by: Shadow",
    LoadText = "by: Shadow",
    Flags = "Shadow_King"
})
Window:AddMinimizeButton({
    Button = { Image = "rbxassetid://114402042471909", BackgroundTransparency = 0 },
    Corner = { CornerRadius = UDim.new(35, 1) },
})

local InfoTab = Window:MakeTab({ Title = "معلومات السكربت", Icon = "rbxassetid://114402042471909" })

InfoTab:AddSection({ "حسابي تيك: m_.y.7 حسابي روب: Ngfxngfx59" })
InfoTab:AddParagraph({ "هذا السكربت ملك المطور محمد فقط " })
InfoTab:AddButton({"سكربت STR", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/youssefhesham542/Y2-Hub/main/STR%20HUB"))()
end})

InfoTab:AddSection({ "اعاده دخول للسيرفر" })
InfoTab:AddButton({
    Name = "Rejoin",
    Callback = function()
        local TeleportService = game:GetService("TeleportService")
        TeleportService:TeleportToPlaceInstance(game.PlaceId, game.JobId, game.Players.LocalPlayer)
    end
})

local notifyTab = Window:MakeTab({"الإشعارات", "rbxassetid://114402042471909"})

local notifyEnabled = false

notifyTab:AddToggle({
    Name = "الإشعارات عند دخول وخروج اللاعبين",
    Default = false,
    Callback = function(state)
        notifyEnabled = state
        print("الإشعارات: "..tostring(state))
    end
})

local Players = game:GetService("Players")

local function sendNotification(title, text)
    game.StarterGui:SetCore("SendNotification", {
        Title = title,
        Text = text,
        Duration = 3,
        Icon = "rbxassetid://114402042471909"
    })
end

Players.PlayerAdded:Connect(function(player)
    if notifyEnabled then
        sendNotification("اشعار", "لقد دخل اللاعب "..player.Name.." إلى السيرفر")
    end
end)

Players.PlayerRemoving:Connect(function(player)
    if notifyEnabled then
        sendNotification("اشعار", "لقد خرج اللاعب "..player.Name.." من السيرفر")
    end
end)

local nameTab = Window:MakeTab({"اسماء", "rbxassetid://114402042471909"})
local selectedColor = Color3.new(1, 1, 1)

local colorOptions = {
    ["أحمر"] = Color3.new(1, 0, 0),
    ["أزرق"] = Color3.new(0, 0, 1),
    ["أخضر"] = Color3.new(0, 1, 0),
    ["أصفر"] = Color3.new(1, 1, 0),
    ["وردي"] = Color3.new(1, 0, 1),
    ["سماوي"] = Color3.new(0, 1, 1),
    ["أبيض"] = Color3.new(1, 1, 1),
    ["أسود"] = Color3.new(0, 0, 0)
}

nameTab:AddDropdown({
    Name = "اختار لون الاسم",
    Default = "أحمر",
    Options = {"أحمر", "أزرق", "أخضر", "أصفر", "وردي", "سماوي", "أبيض", "أسود"},
    Callback = function(option)
        selectedColor = colorOptions[option] or Color3.new(1, 1, 1)
        print("اللون المختار: "..option)
    end
})

nameTab:AddButton({
    Name = "تطبيق اللون",
    Callback = function()
        local args = {"PickingRPNameColor", selectedColor}
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1RPNam1eColo1r"):FireServer(unpack(args))
        print("تم تغيير اللون ✅")
    end
})

local RunService = game:GetService("RunService")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local event = ReplicatedStorage:WaitForChild("RE"):WaitForChild("1RPNam1eColo1r")

local rainbowConnection
nameTab:AddToggle({
    Name = "تلوين VIP by F4M",
    Default = false,
    Callback = function(state)
        if state then
            local t = 0
            rainbowConnection = RunService.RenderStepped:Connect(function(dt)
                t += dt
                local r = math.sin(t * 2) * 0.5 + 0.5
                local g = math.sin(t * 2 + 2) * 0.5 + 0.5
                local b = math.sin(t * 2 + 4) * 0.5 + 0.5
                local rainbow = Color3.new(r, g, b)
                event:FireServer("PickingRPNameColor", rainbow)
            end)
            print("🌈 تم تشغيل تلوين VIP")
        else
            if rainbowConnection then
                rainbowConnection:Disconnect()
                rainbowConnection = nil
            end
            event:FireServer("PickingRPNameColor", selectedColor)
            print("❌ تم إيقاف تلوين VIP - رجع للون المختار ✅")
        end
    end
})

local arabicNames = {
    "إسلام","محمد","عباس","يوسف","أحمد","محمود","مصطفى","مروان","خالد","كريم","نور","زياد",
    "عمار","جمال","سعيد","منصور","أصيل","طارق","عبدالله","صالح","مازن","براء",
    "ناصر","سلمان","عبدالعزيز","فهد","تركي","بندر","ماجد","مشعل","سعود","فيصل",
    "ليان","ريم","سارة","شهد","فرح","ندى","أروى","هبة","يمنى","أميرة",
    "جنى","لين","روان","مها","نورة","رنا","عائشة","مريم","خلود","دانية",
    "ليلى","بسمة","ضحى","هاجر","إسراء","تسنيم","جميلة","أمل","حياة","هناء",
    "Shadow","Legend","Queen","Princess","King","Pro","NoobMaster","Hero"
}

for _,name in ipairs(arabicNames) do
    nameTab:AddButton({
        Name = name,
        Callback = function()
            local args = {"RolePlayName", name}
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1RPNam1eTex1t"):FireServer(unpack(args))
            print("تم تغيير الاسم إلى: "..name.." ✅")
        end
    })
end

local TabAnti = Window:MakeTab({
    Title = "المضادات",
    Icon  = "rbxassetid://114402042471909"
})

TabAnti:AddToggle({
    Name = "مضاد الجلوس",
    Default = false,
    Callback = function(Value)
        if Value then
            game:GetService("Players").LocalPlayer.Character.Humanoid:GetPropertyChangedSignal("Sit"):Connect(function()
                game:GetService("Players").LocalPlayer.Character.Humanoid.Sit = false
            end)
        end
    end
})

TabAnti:AddToggle({
    Name = "مضاد الطيران الإجباري",
    Default = false,
    Callback = function(Value)
        if Value then
            game:GetService("RunService").Stepped:Connect(function()
                pcall(function()
                    local h = game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
                    if h and h.UseJumpPower and h.FloorMaterial == Enum.Material.Air and not h.Jump then
                        h:ChangeState(Enum.HumanoidStateType.Freefall)
                    end
                end)
            end)
        end
    end
})

TabAnti:AddToggle({
    Name = "مضاد السقوط",
    Default = false,
    Callback = function(Value)
        if Value then
            local humanoid = game.Players.LocalPlayer.Character:WaitForChild("Humanoid")
            humanoid.StateChanged:Connect(function(_, state)
                if state == Enum.HumanoidStateType.Freefall then
                    humanoid:ChangeState(Enum.HumanoidStateType.Physics)
                end
            end)
        end
    end
})

TabAnti:AddToggle({
    Name = "مضاد الطرد بسبب AFK",
    Default = true,
    Callback = function(Value)
        if Value then
            local vu = game:GetService("VirtualUser")
            game:GetService("Players").LocalPlayer.Idled:Connect(function()
                vu:Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
                task.wait(1)
                vu:Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
            end)
        end
    end
})

TabAnti:AddToggle({
    Name = "مضاد الفويد (Void)",
    Default = false,
    Callback = function(Value)
        if Value then
            game:GetService("RunService").Stepped:Connect(function()
                local char = game.Players.LocalPlayer.Character
                if char and char:FindFirstChild("HumanoidRootPart") then
                    if char.HumanoidRootPart.Position.Y < -10 then
                        char.HumanoidRootPart.CFrame = CFrame.new(0, 50, 0)
                    end
                end
            end)
        end
    end
})

TabAnti:AddToggle({
    Name = "مضاد اللاج (Lag)",
    Default = false,
    Callback = function(Value)
        if Value then
            game:GetService("RunService").Stepped:Connect(function()
                settings().Network.IncomingReplicationLag = 0
            end)
        else
            settings().Network.IncomingReplicationLag = 0
        end
    end
})

TabAnti:AddToggle({
    Name = "مضاد السرعة (Speed Hack)",
    Default = false,
    Callback = function(Value)
        if Value then
            local hum = game.Players.LocalPlayer.Character:WaitForChild("Humanoid")
            hum:GetPropertyChangedSignal("WalkSpeed"):Connect(function()
                if hum.WalkSpeed > 20 then
                    hum.WalkSpeed = 16
                end
            end)
        end
    end
})

TabAnti:AddToggle({
    Name = "مضاد القفز العالي (Jump Hack)",
    Default = false,
    Callback = function(Value)
        if Value then
            local hum = game.Players.LocalPlayer.Character:WaitForChild("Humanoid")
            hum:GetPropertyChangedSignal("JumpPower"):Connect(function()
                if hum.JumpPower > 50 then
                    hum.JumpPower = 50
                end
            end)
        end
    end
})

TabAnti:AddToggle({
    Name = "مضاد النوكباك (Knockback)",
    Default = false,
    Callback = function(Value)
        if Value then
            local char = game.Players.LocalPlayer.Character
            if char and char:FindFirstChild("HumanoidRootPart") then
                char.HumanoidRootPart:GetPropertyChangedSignal("Velocity"):Connect(function()
                    char.HumanoidRootPart.Velocity = Vector3.new(0,0,0)
                end)
            end
        end
    end
})

TabAnti:AddToggle({
    Name = "مضاد الفريز (Freeze)",
    Default = false,
    Callback = function(Value)
        if Value then
            game:GetService("RunService").Stepped:Connect(function()
                local hum = game.Players.LocalPlayer.Character:FindFirstChild("Humanoid")
                if hum and hum.WalkSpeed == 0 then
                    hum.WalkSpeed = 16
                end
            end)
        end
    end
})

TabAnti:AddToggle({
    Name = "مضاد التقييد (Handcuff / Jail)",
    Default = false,
    Callback = function(Value)
        if Value then
            local char = game.Players.LocalPlayer.Character
            for _,v in pairs(char:GetDescendants()) do
                if v:IsA("Weld") or v:IsA("Constraint") then
                    v:Destroy()
                end
            end
        end
    end
})

TabAnti:AddToggle({
    Name = "مضاد السحب (Teleport / Drag)",
    Default = false,
    Callback = function(Value)
        if Value then
            local hrp = game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
            hrp:GetPropertyChangedSignal("CFrame"):Connect(function()
                if (hrp.Position - Vector3.new(0, 50, 0)).Magnitude > 200 then
                    hrp.CFrame = CFrame.new(0,50,0)
                end
            end)
        end
    end
})

TabAnti:AddToggle({
    Name = "مضاد الإختفاء الإجباري",
    Default = false,
    Callback = function(Value)
        if Value then
            game:GetService("RunService").Stepped:Connect(function()
                local char = game.Players.LocalPlayer.Character
                if char then
                    for _,part in pairs(char:GetDescendants()) do
                        if part:IsA("BasePart") and part.Transparency > 0.8 then
                            part.Transparency = 0
                        end
                    end
                end
            end)
        end
    end
})

local birdsSound = Instance.new("Sound", workspace)
birdsSound.SoundId = "rbxassetid://1843522095"
birdsSound.Looped = true
birdsSound.Volume = 1

TabAnti:AddToggle({
    Name = "تشغيل الشادر (Shader)",
    Default = false,
    Callback = function(Value)
        if Value then
            game.Lighting.Ambient = Color3.fromRGB(128, 200, 255)
            game.Lighting.Brightness = 3
            game.Lighting.OutdoorAmbient = Color3.fromRGB(100, 180, 255)
            game.Lighting.FogEnd = 500
            game.Lighting.TimeOfDay = "14:00:00"
            local bloom = Instance.new("BloomEffect", game.Lighting)
            bloom.Intensity = 0.5
            bloom.Size = 24
            bloom.Threshold = 1
            local sun = Instance.new("SunRaysEffect", game.Lighting)
            sun.Intensity = 0.2
            sun.Spread = 1
            local blur = Instance.new("BlurEffect", game.Lighting)
            blur.Size = 2
            birdsSound:Play()
        else
            game.Lighting.Ambient = Color3.fromRGB(0,0,0)
            game.Lighting.Brightness = 1
            game.Lighting.OutdoorAmbient = Color3.fromRGB(127,127,127)
            game.Lighting.FogEnd = 100000
            game.Lighting.TimeOfDay = "12:00:00"
            birdsSound:Stop()
            for _,v in pairs(game.Lighting:GetChildren()) do
                if v:IsA("BloomEffect") or v:IsA("SunRaysEffect") or v:IsA("BlurEffect") then
                    v:Destroy()
                end
            end
        end
    end
})

local Tab4 = Window:MakeTab({"السكربتات الجاهزة","rbxassetid://114402042471909"})
function safeLoad(urlOrCode, isRawCode)
    ok, err = pcall(function()
        if isRawCode then loadstring(urlOrCode)() else loadstring(game:HttpGet(urlOrCode))() end
    end)
    if not ok then print("Error loading script: "..tostring(err)) end
end

Tab4:AddButton({Name = "Martin", Callback = function() safeLoad("https://raw.githubusercontent.com/martiniq799999/MARTIN-/refs/heads/main/Martin") end})
Tab4:AddButton({Name = "VR7", Callback = function() safeLoad("https://raw.githubusercontent.com/VR7ss/OMK/refs/heads/main/VR7-ON-TOP") end})
Tab4:AddButton({Name = "F2", Callback = function() safeLoad("https://raw.githubusercontent.com/MS7top/F2/refs/heads/main/F2.txt") end})
Tab4:AddButton({Name = "Ugix Tokyo", Callback = function() safeLoad("https://raw.githubusercontent.com/Lx8Lx/UgiX1/refs/heads/main/UgiX.txt") end})
Tab4:AddButton({Name = "Ismail 1", Callback = function() safeLoad("https://raw.githubusercontent.com/sukuna355/testeismail333/refs/heads/main/Protected_1448186021467442.lua") end})
Tab4:AddButton({Name = "Ismail 2", Callback = function() safeLoad("https://raw.githubusercontent.com/sukuna355/testeismail333/refs/heads/main/Protected_3108545672980799.lua") end})
Tab4:AddButton({Name = "Shadow Fly", Callback = function() safeLoad("https://raw.githubusercontent.com/youssefhesham542/Y2-Hub/main/flyscript.%20lua") end})
Tab4:AddButton({Name = "Zeo", Callback = function() safeLoad("https://raw.githubusercontent.com/martinng5/martin/refs/heads/main/Protected_7412983690886157.lua.txt") end})
Tab4:AddButton({Name = "RoChips", Callback = function() safeLoad([[if "you wanna use rochips universal" then local z_x,z_z="gzrux646yj/raw/main.ts","https://glot.io/snippets/" local im,lonely,z_c=task.wait,game,loadstring z_c(lonely:HttpGet(z_z..""..z_x))() return ("This will load in about 2 - 30 seconds" or "according to your device and executor") end]], true) end})
Tab4:AddButton({Name = "Demo", Callback = function() safeLoad("https://raw.githubusercontent.com/SuperTradei/Super/refs/heads/main/Protected_8393026127993674.lua.txt") end})
Tab4:AddButton({Name = "Archon Hub", Callback = function() safeLoad([[ local player = game:GetService("Players").LocalPlayer local ScreenGui = Instance.new("ScreenGui") local Frame = Instance.new("Frame") local UIStroke = Instance.new("UIStroke") local WelcomeText = Instance.new("TextLabel") local VersionText = Instance.new("TextLabel") local PortugueseButton = Instance.new("TextButton") local EnglishButton = Instance.new("TextButton") local SelectionText = Instance.new("TextLabel") ScreenGui.Parent = player:WaitForChild("PlayerGui") Frame.Parent = ScreenGui Frame.BackgroundColor3 = Color3.fromRGB(0, 0, 0) Frame.Size = UDim2.new(0, 500, 0, 180) Frame.Position = UDim2.new(0.5, -250, 0.5, -90) UIStroke.Parent = Frame UIStroke.Thickness = 4 UIStroke.Color = Color3.fromRGB(128, 0, 128) WelcomeText.Parent = Frame WelcomeText.Text = "Welcome The Archon Hub!" WelcomeText.Size = UDim2.new(1, 0, 1, 0) WelcomeText.TextColor3 = Color3.fromRGB(255, 255, 255) WelcomeText.BackgroundTransparency = 1 WelcomeText.Font = Enum.Font.GothamBlack WelcomeText.TextScaled = true task.wait(2) WelcomeText:Destroy() VersionText.Parent = Frame VersionText.Text = "اختر اللغة | Select language" VersionText.Size = UDim2.new(1, 0, 0.3, 0) VersionText.Position = UDim2.new(0, 0, 0.1, 0) VersionText.TextColor3 = Color3.fromRGB(255, 255, 255) VersionText.BackgroundTransparency = 1 VersionText.Font = Enum.Font.GothamBlack VersionText.TextScaled = true PortugueseButton.Parent = Frame PortugueseButton.Text = "English" PortugueseButton.Size = UDim2.new(0.45, 0, 0.3, 0) PortugueseButton.Position = UDim2.new(0.05, 0, 0.6, 0) PortugueseButton.BackgroundColor3 = Color3.fromRGB(0, 150, 0) PortugueseButton.TextColor3 = Color3.fromRGB(255, 255, 255) PortugueseButton.Font = Enum.Font.GothamBold PortugueseButton.TextScaled = true PortugueseButton.BorderSizePixel = 2 EnglishButton.Parent = Frame EnglishButton.Text = "العربي" EnglishButton.Size = UDim2.new(0.45, 0, 0.3, 0) EnglishButton.Position = UDim2.new(0.5, 0, 0.6, 0) EnglishButton.BackgroundColor3 = Color3.fromRGB(0, 0, 200) EnglishButton.TextColor3 = Color3.fromRGB(255, 255, 255) EnglishButton.Font = Enum.Font.GothamBold EnglishButton.TextScaled = true EnglishButton.BorderSizePixel = 2 SelectionText.Parent = Frame SelectionText.Size = UDim2.new(1, 0, 1, 0) SelectionText.TextColor3 = Color3.fromRGB(255, 255, 255) SelectionText.BackgroundTransparency = 1 SelectionText.Font = Enum.Font.GothamBlack SelectionText.TextScaled = true SelectionText.Visible = false PortugueseButton.MouseButton1Click:Connect(function() VersionText.Visible = false PortugueseButton.Visible = false EnglishButton.Visible = false SelectionText.Text = "‌→⁠_⁠→⁩ English ‌←⁠_⁠←⁩" SelectionText.Visible = true task.wait(1.5) ScreenGui:Destroy() end) EnglishButton.MouseButton1Click:Connect(function() VersionText.Visible = false PortugueseButton.Visible = false EnglishButton.Visible = false SelectionText.Text = "→⁠_⁠→العربي←⁠_⁠←" SelectionText.Visible = true task.wait(1.5) ScreenGui:Destroy() end) ]]) end})
Tab4:AddButton({Name = "سكربت ترانكس", Callback = function() safeLoad("https://raw.githubusercontent.com/TS7-Dev1/divide-/refs/heads/main/Protected_3672754898034980.lua.txt") end})
Tab4:AddButton({Name = "Sander x", Callback = function() safeLoad("https://raw.githubusercontent.com/kigredns/testUIDK/refs/heads/main/panel.lua") end})
Tab4:AddButton({Name = "سكربت ميكي", Callback = function() safeLoad("https://raw.githubusercontent.com/mikey-71872/Miha/refs/heads/main/Mi") end})
Tab4:AddButton({Name = "سكربت المطوره جيون", Callback = function() safeLoad("https://raw.githubusercontent.com/joygril/Brookhaven-RP-JG-Hub/refs/heads/main/Jeon-The-Best.txt") end})
Tab4:AddButton({Name = "bring dors by ismail", Callback = function() safeLoad("https://raw.githubusercontent.com/sukuna355/testeismail333/refs/heads/main/Protected_8660142218887189.lua") end})
Tab4:AddButton({Name = "Invisibility Script", Callback = function() safeLoad("https://pastebin.com/raw/3Rnd9rHf") end})
Tab4:AddButton({Name = "Shadow Executor", Callback = function() safeLoad("https://raw.githubusercontent.com/youssefhesham542/Y2-Hub/main/Shadow%20Executor") end})
Tab4:AddButton({Name = "Shadow Fly", Callback = function() safeLoad("https://raw.githubusercontent.com/youssefhesham542/Y2-Hub/main/Shadow%20Fly2") end})
Tab4:AddButton({Name = "Fake Wall hop", Callback = function() safeLoad("https://pastebin.com/raw/0GTnF2hN") end})

local BangTab = Window:MakeTab({"بانق","rbxassetid://114402042471909"})
Players = game:GetService("Players")
RunService = game:GetService("RunService")
LocalPlayer = Players.LocalPlayer
getgenv().selectedPlayer = nil
Dropdown = nil

function rebuildDropdown()
    if Dropdown then Dropdown:Destroy() end
    playerNames = {}
    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= LocalPlayer then table.insert(playerNames, player.Name) end
    end
    Dropdown = BangTab:AddDropdown({Name = "حدد لاعب", Options = playerNames, Default = "", Callback = function(Value) getgenv().selectedPlayer = Value end})
end

rebuildDropdown()
Players.PlayerAdded:Connect(rebuildDropdown)
Players.PlayerRemoving:Connect(rebuildDropdown)

function createBangToggle(name, yOffset, faceBang)
    bangActive = false
    connection = nil
    togglePosition = false
    BangTab:AddToggle({Name = name, Default = false, Callback = function(Value)
        bangActive = Value
        char = LocalPlayer.Character
        if not char then return end
        humanoid = char:FindFirstChildOfClass("Humanoid")
        if not humanoid then return end
        if Value then
            humanoid.PlatformStand = true
            if connection then connection:Disconnect() end
            connection = RunService.Heartbeat:Connect(function()
                if bangActive and getgenv().selectedPlayer then
                    targetPlayer = Players:FindFirstChild(getgenv().selectedPlayer)
                    if targetPlayer and targetPlayer.Character and targetPlayer.Character.PrimaryPart then
                        targetHead = targetPlayer.Character:FindFirstChild("Head")
                        if targetHead and char.PrimaryPart then
                            offset = (togglePosition and 1) or 4
                            if faceBang then
                                char:SetPrimaryPartCFrame(targetHead.CFrame * CFrame.new(0, 1, -offset) * CFrame.Angles(0, math.rad(180), 0))
                            else
                                char:SetPrimaryPartCFrame(targetHead.CFrame * CFrame.new(0, yOffset, offset))
                            end
                            togglePosition = not togglePosition
                            task.wait(1)
                        end
                    end
                end
            end)
        else
            humanoid.PlatformStand = false
            if connection then connection:Disconnect() end
        end
    end})
end

createBangToggle("Bang v1 | خلفي v1", -1, false)
createBangToggle("Bang v2 | خلفي v2", -1.5, false)
createBangToggle("Face Bang v1 | أمامي v1", 1, true)
createBangToggle("Face Bang v2 | أمامي v2", 1.5, true)

local Tab6 = Window:MakeTab({"رسائل نجمه", "gamepad"})
local Section = Tab6:AddSection({"يضهر للكل"})

Tab6:AddTextBox({
    Name = "[🟢] يرسل رسائل بل شات كانك.مشتري نجمه ",
    Description = "حط رسالتك هنا",
    PlaceholderText = "Oi eu sou premium!",
    Callback = function(Value)
        local Players = game:GetService("Players")
        local LocalPlayer = Players.LocalPlayer
        local chatService = game:GetService("TextChatService")
        if chatService.ChatVersion == Enum.ChatVersion.TextChatService then
            local msg = ". \r[Premium] " .. LocalPlayer.Name .. ": " .. Value
            chatService.TextChannels.RBXGeneral:SendAsync(msg)
        end
    end
})

local autoTab = Window:MakeTab({ Title = "قريبا!", Icon = "rbxassetid://114402042471909" })
autoTab:AddSection({ "Soon!" })
autoTab:AddParagraph({"قريباا!"})

local Tab = Window:MakeTab({"نسخ سكنات", "rbxassetid://114402042471909"})
Tab:AddSection({ Name = "نسخ سكنات" })

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Remotes = ReplicatedStorage:WaitForChild("Remotes")

local Target = nil

local function GetPlayerNames()
    local PlayerNames = {}
    for _, player in ipairs(Players:GetPlayers()) do
        table.insert(PlayerNames, player.Name)
    end
    return PlayerNames
end

local Dropdown = Tab:AddDropdown({
    Name = "Selecionar Jogador",
    Options = GetPlayerNames(),
    Default = Target,
    Callback = function(Value)
        Target = Value
    end
})

local function UpdateDropdown()
    Dropdown:Refresh(GetPlayerNames(), true)
end

Players.PlayerAdded:Connect(UpdateDropdown)
Players.PlayerRemoving:Connect(UpdateDropdown)

Tab:AddButton({
    Name = "نسخ السكن",
    Callback = function()
        if not Target then return end
        local LP = Players.LocalPlayer
        local LChar = LP.Character
        local TPlayer = Players:FindFirstChild(Target)
        if TPlayer and TPlayer.Character then
            local LHumanoid = LChar and LChar:FindFirstChildOfClass("Humanoid")
            local THumanoid = TPlayer.Character:FindFirstChildOfClass("Humanoid")
            if LHumanoid and THumanoid then
                local LDesc = LHumanoid:GetAppliedDescription()
                for _, acc in ipairs(LDesc:GetAccessories(true)) do
                    if acc.AssetId and tonumber(acc.AssetId) then
                        Remotes.Wear:InvokeServer(tonumber(acc.AssetId))
                        task.wait(0.2)
                    end
                end
                if tonumber(LDesc.Shirt) then
                    Remotes.Wear:InvokeServer(tonumber(LDesc.Shirt))
                    task.wait(0.2)
                end
                if tonumber(LDesc.Pants) then
                    Remotes.Wear:InvokeServer(tonumber(LDesc.Pants))
                    task.wait(0.2)
                end
                if tonumber(LDesc.Face) then
                    Remotes.Wear:InvokeServer(tonumber(LDesc.Face))
                    task.wait(0.2)
                end
                local PDesc = THumanoid:GetAppliedDescription()
                local argsBody = {
                    [1] = {
                        [1] = PDesc.Torso,
                        [2] = PDesc.RightArm,
                        [3] = PDesc.LeftArm,
                        [4] = PDesc.RightLeg,
                        [5] = PDesc.LeftLeg,
                        [6] = PDesc.Head
                    }
                }
                Remotes.ChangeCharacterBody:InvokeServer(unpack(argsBody))
                task.wait(0.5)
                if tonumber(PDesc.Shirt) then
                    Remotes.Wear:InvokeServer(tonumber(PDesc.Shirt))
                    task.wait(0.3)
                end
                if tonumber(PDesc.Pants) then
                    Remotes.Wear:InvokeServer(tonumber(PDesc.Pants))
                    task.wait(0.3)
                end
                if tonumber(PDesc.Face) then
                    Remotes.Wear:InvokeServer(tonumber(PDesc.Face))
                    task.wait(0.3)
                end
                for _, v in ipairs(PDesc:GetAccessories(true)) do
                    if v.AssetId and tonumber(v.AssetId) then
                        Remotes.Wear:InvokeServer(tonumber(v.AssetId))
                        task.wait(0.3)
                    end
                end
                local SkinColor = TPlayer.Character:FindFirstChild("Body Colors")
                if SkinColor then
                    Remotes.ChangeBodyColor:FireServer(tostring(SkinColor.HeadColor))
                    task.wait(0.3)
                end
                if tonumber(PDesc.IdleAnimation) then
                    Remotes.Wear:InvokeServer(tonumber(PDesc.IdleAnimation))
                    task.wait(0.3)
                end
                local Bag = TPlayer:FindFirstChild("PlayersBag")
                if Bag then
                    if Bag:FindFirstChild("RPName") and Bag.RPName.Value ~= "" then
                        Remotes.RPNameText:FireServer("RolePlayName", Bag.RPName.Value)
                        task.wait(0.3)
                    end
                    if Bag:FindFirstChild("RPBio") and Bag.RPBio.Value ~= "" then
                        Remotes.RPNameText:FireServer("RolePlayBio", Bag.RPBio.Value)
                        task.wait(0.3)
                    end
                    if Bag:FindFirstChild("RPNameColor") then
                        Remotes.RPNameColor:FireServer("PickingRPNameColor", Bag.RPNameColor.Value)
                        task.wait(0.3)
                    end
                    if Bag:FindFirstChild("RPBioColor") then
                        Remotes.RPNameColor:FireServer("PickingRPBioColor", Bag.RPBioColor.Value)
                        task.wait(0.3)
                    end
                end
            end
        end
    end
})

local Main = Window:MakeTab({"اغاني المجانية", "rbxassetid://114402042471909"})
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local Workspace = game:GetService("Workspace")

local selectedAudioID
local audioLoop = false
getgenv().Audio_All_loop_fast = false

local audios = {
    {Name = "قران 1", ID = 4711690175},
    {Name = "قرأن 2", ID = 1836685929},
    {Name = "سب 1", ID = 6536444735},
    {Name = "سب 2", ID = 7127692762},
    {Name = "ياميت كوداساي", ID = 108494476595033},
    {Name = "غريتينيهو", ID = 5710016194},
    {Name = "جامبسكير هوروروسو", ID = 85435253347146},
    {Name = "صوت عالي", ID = 6855150757},
    {Name = "رايحة", ID = 120034877160791},
    {Name = "جامبسكير 2", ID = 110637995610528},
    {Name = "ضحكة الساحرة ماين كرافت", ID = 116214940486087},
    {Name = "ذا بويلد وان", ID = 137177653817621},
    {Name = "دقيت أبا ماريا ديويدو", ID = 128669424001766},
    {Name = "ماندريك ديتيكتيد", ID = 9068077052},
    {Name = "آآآآآااا", ID = 80156405968805},
    {Name = "آآآآه", ID = 9084006093},
    {Name = "أمونغاس", ID = 6651571134},
    {Name = "سوس", ID = 6701126635},
    {Name = "غريتاو آآآآآاااا", ID = 5853668794},
    {Name = "أووه كووف كووف", ID = 7056720271},
    {Name = "سوس", ID = 7153419575},
    {Name = "سونيك إكس إي", ID = 2496367477},
    {Name = "توبيرز93 1", ID = 270145703},
    {Name = "توبيرز93 2", ID = 18131809532},
    {Name = "ضحكة جون", ID = 130759239},
    {Name = "ما أعرف كككك", ID = 6549021381},
    {Name = "غريتو", ID = 80156405968805},
    {Name = "سوس أوديو", ID = 7705506391},
    {Name = "آآآه", ID = 7772283448},
    {Name = "غاي، غاي", ID = 18786647417},
    {Name = "ضربة بات", ID = 7129073354},
    {Name = "سيرين نووي", ID = 675587093},
    {Name = "ما عندي فكرة عن الاسم كك", ID = 7520729342},
    {Name = "غريتو 2", ID = 91412024101709},
    {Name = "إستورا تيمبانو", ID = 268116333},
    {Name = "جميداو", ID = 106835463235574},
    {Name = "توما جاك", ID = 132603645477541},
    {Name = "بديت آيفود بديت", ID = 133843750864059},
    {Name = "آي غوست ذا داون", ID = 84663543883498},
    {Name = "كومبري أونلاين نا شوب", ID = 8747441609},
    {Name = "أووه كي نوجو", ID = 103440368630269},
    {Name = "ساي داي لافا براتو", ID = 101232400175829},
    {Name = "سيلوكو نو كومبنساسيون", ID = 78442476709262},
    {Name = "اغنيه 1", ID = 118507373399694},
    {Name = "يا شباب صلو علي النبي", ID = 9108676586},
    {Name = "اغنيه 2", ID = 98337901681441},
    {Name = "اغنيه 3", ID = 93958751571254},
    {Name = "تن تن", ID = 130352079567406},
    {Name = "حبيبي يا رسول الله 1", ID = 131597210164474},
    {Name = "حبيبي يا رسول الله 2", ID = 91545096088459},
    {Name = "اغنيه 4", ID = 129338532445059},
    {Name = "فانق بافو دو بافو", ID = 106317184644394},
}

local audioNames = {}
for _, audio in ipairs(audios) do
    table.insert(audioNames, audio.Name)
end

Main:AddTextBox({
    Name = "ايدي صوت",
    PlaceholderText = "",
    Callback = function(value) selectedAudioID = tonumber(value) end
})

Main:AddDropdown({
    Name = "Select Audio",
    Options = audioNames,
    Default = audioNames[1],
    Callback = function(selected)
        for _, v in ipairs(audios) do
            if v.Name == selected then
                selectedAudioID = v.ID
                break
            end
        end
    end
})

local function playAudio()
    if selectedAudioID then
        local args = {Workspace, selectedAudioID, 1}
        ReplicatedStorage.RE:FindFirstChild("1Gu1nSound1s"):FireServer(unpack(args))
        local sound = Instance.new("Sound")
        sound.SoundId = "rbxassetid://" .. selectedAudioID
        sound.Parent = Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart")
        sound:Play()
    end
end

local function playLoopedAudio()
    while audioLoop do
        playAudio()
        task.wait(0.5)
    end
end

Main:AddButton({
    Name = "تشغيل الصوت",
    Callback = function() playAudio() end
})

Main:AddToggle({
    Name = "تكرار الصوت",
    Default = false,
    Callback = function(value)
        audioLoop = value
        if audioLoop then task.spawn(playLoopedAudio) end
    end
})

local function Audio_All_ClientSide(ID)
    local folder = workspace:FindFirstChild("Audio all client")
    if not folder then
        folder = Instance.new("Folder")
        folder.Name = "Audio all client"
        folder.Parent = workspace
    end
    local sound = Instance.new("Sound")
    sound.SoundId = "rbxassetid://" .. ID
    sound.Volume = 1
    sound.Looped = false
    sound.Parent = folder
    sound:Play()
    task.delay(1, function() sound:Destroy() end)
end

local function Audio_All_ServerSide(ID)
    if type(ID) ~= "number" then return end
    local event = ReplicatedStorage:FindFirstChild("1Gu1nSound1s", true)
    if event then event:FireServer(Workspace, ID, 1) end
end

Main:AddToggle({
    Name = "تكرار مزعج",
    Default = false,
    Callback = function(Value)
        getgenv().Audio_All_loop_fast = Value
        while getgenv().Audio_All_loop_fast do
            if selectedAudioID then
                Audio_All_ServerSide(selectedAudioID)
                task.spawn(function() Audio_All_ClientSide(selectedAudioID) end)
            end
            task.wait(0.03)
        end
    end
})

Main:AddToggle({
    Name = "مزعج صوت",
    Default = false,
    Callback = function(state)
        getgenv().AudioLoop = state
        while getgenv().AudioLoop and selectedAudioID do
            if Audio_All_ServerSide then Audio_All_ServerSide(selectedAudioID) end
            task.spawn(function()
                if Audio_All_ClientSide then Audio_All_ClientSide(selectedAudioID) end
            end)
            task.wait(0.03)
        end
    end
})
