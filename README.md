-- GUI Loader made by Henry1887

local ScreenGui = Instance.new("ScreenGui")
local Main = Instance.new("ImageLabel")
local Welcome = Instance.new("Frame")
local line1 = Instance.new("TextLabel")
local title = Instance.new("TextLabel")
local line2 = Instance.new("TextLabel")
local line3 = Instance.new("TextLabel")
local line4 = Instance.new("TextLabel")
local line5 = Instance.new("TextLabel")
local line6 = Instance.new("TextLabel")

-- Properties:

ScreenGui.Parent = game.CoreGui

Main.Name = "Main"
Main.Parent = ScreenGui
Main.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Main.BackgroundTransparency = 1
Main.Position = UDim2.new(0.0899, 0, 0.1622, 0)
Main.Size = UDim2.new(0, 266, 0, 217)
Main.Image = "rbxassetid://3570695787"
Main.ImageColor3 = Color3.fromRGB(0, 0, 0)
Main.ImageTransparency = 0.3
Main.ScaleType = Enum.ScaleType.Slice
Main.SliceCenter = Rect.new(100, 100, 100, 100)
Main.SliceScale = 0.06

Welcome.Name = "Welcome"
Welcome.Parent = Main
Welcome.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Welcome.BackgroundTransparency = 1
Welcome.Size = UDim2.new(0, 266, 0, 217)

-- Configure TextLabels
line1.Name = "line1"
line1.Parent = Welcome
line1.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
line1.BackgroundTransparency = 1
line1.Position = UDim2.new(0.0225, 0, 0.1244, 0)
line1.Size = UDim2.new(0, 260, 0, 17)
line1.Font = Enum.Font.Ubuntu
line1.TextColor3 = Color3.fromRGB(0, 255, 0)
line1.TextSize = 10
line1.TextXAlignment = Enum.TextXAlignment.Left

title.Name = "title"
title.Parent = Welcome
title.BackgroundColor3 = Color3.fromRGB(62, 62, 62)
title.BorderSizePixel = 0
title.Size = UDim2.new(0, 266, 0, 17)
title.Font = Enum.Font.Ubuntu
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.TextSize = 10

line2.Name = "line2"
line2.Parent = Welcome
line2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
line2.BackgroundTransparency = 1
line2.Position = UDim2.new(0.0225, 0, 0.2028, 0)
line2.Size = UDim2.new(0, 260, 0, 17)
line2.Font = Enum.Font.Ubuntu
line2.TextColor3 = Color3.fromRGB(0, 255, 0)
line2.TextSize = 10
line2.TextXAlignment = Enum.TextXAlignment.Left

line3.Name = "line3"
line3.Parent = Welcome
line3.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
line3.BackgroundTransparency = 1
line3.Position = UDim2.new(0.0225, 0, 0.2811, 0)
line3.Size = UDim2.new(0, 260, 0, 17)
line3.Font = Enum.Font.Ubuntu
line3.TextColor3 = Color3.fromRGB(0, 255, 0)
line3.TextSize = 10
line3.TextXAlignment = Enum.TextXAlignment.Left

line4.Name = "line4"
line4.Parent = Welcome
line4.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
line4.BackgroundTransparency = 1
line4.Position = UDim2.new(0.0225, 0, 0.3594, 0)
line4.Size = UDim2.new(0, 260, 0, 17)
line4.Font = Enum.Font.Ubuntu
line4.TextColor3 = Color3.fromRGB(0, 255, 0)
line4.TextSize = 10
line4.TextXAlignment = Enum.TextXAlignment.Left

line5.Name = "line5"
line5.Parent = Welcome
line5.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
line5.BackgroundTransparency = 1
line5.Position = UDim2.new(0.0225, 0, 0.4378, 0)
line5.Size = UDim2.new(0, 260, 0, 17)
line5.Font = Enum.Font.Ubuntu
line5.TextColor3 = Color3.fromRGB(0, 255, 0)
line5.TextSize = 10
line5.TextXAlignment = Enum.TextXAlignment.Left

line6.Name = "line6"
line6.Parent = Welcome
line6.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
line6.BackgroundTransparency = 1
line6.Position = UDim2.new(0.0225, 0, 0.5161, 0)
line6.Size = UDim2.new(0, 260, 0, 17)
line6.Font = Enum.Font.Ubuntu
line6.TextColor3 = Color3.fromRGB(0, 255, 0)
line6.TextSize = 10
line6.TextXAlignment = Enum.TextXAlignment.Left

-- Show the welcome screen and load the main GUI
local function showWelcomeScreen()
    Main.Visible = true
    local name = game.Players.LocalPlayer.Name
    title.Text = name .. "@ubuntu:~/"

    line1.Text = name .. "@ubuntu:~$ |"
    wait(1)
    line1.Text = name .. "@ubuntu:~$ echo Welcome|"
    wait(1)
    line1.Text = name .. "@ubuntu:~$ echo Welcome!"
    wait(0.1)
    
    line2.Visible = true
    wait(0.1)
    
    line3.Visible = true
    line3.Text = name .. "@ubuntu:~$ ./load_gui"
    wait(3)
    
    line4.Visible = true
    wait(2)

    line5.Visible = true
    wait(2)

    line6.Visible = true
    wait(1)

    line6.Text = "GUI loaded, closing shell in 3..."
    wait(1)
    line6.Text = "GUI loaded, closing shell in 2..."
    wait(1)
    line6.Text = "GUI loaded, closing shell in 1..."
    wait(1)
    line6.Text = "GUI loaded, closing shell in 0..."
    
    Main.Visible = false
end

showWelcomeScreen()

-- GUI Script Start
local function createMainGui()
    -- Here you can create your main GUI elements
end

createMainGui()

-- Dragging functionality
local function dragMainUI()
    local UserInputService = game:GetService("UserInputService")
    local runService = game:GetService("RunService")
    local dragging, dragInput, dragStart, startPos

    Main.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            dragging = true
            dragStart = input.Position
            startPos = Main.Position

            input.Changed:Connect(function()
                if input.UserInputState == Enum.UserInputState.End then
                    dragging = false
                end
            end)
        end
    end)

    runService.Heartbeat:Connect(function()
        if dragging then
            local delta = UserInputService:GetMouseLocation() - dragStart
            Main.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
        end
    end)
end

dragMainUI()
