local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local punchButton = Instance.new("TextButton")
punchButton.Size = UDim2.new(0, 200, 0, 50)
punchButton.Position = UDim2.new(0.5, -100, 0.5, -25)
punchButton.Text = "Start Punching!"
punchButton.Parent = screenGui

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleEvent = player:WaitForChild("muscleEvent")
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")
local rockPart = muscleKingMountain:FindFirstChild("Rock")
local punchTool = player.Backpack:FindFirstChild("Punch")

local isPunching = false
local punchLoop

local function equipPunch()
    if punchTool and not character:FindFirstChild(punchTool.Name) then
        punchTool.Parent = character
    end
end

local function setToolCooldowns()
    local tools = {
        {name = "Punch", type = "attackTime"},
        {name = "Ground Slam", type = "attackTime"},
        {name = "Stomp", type = "attackTime"},
        {name = "Handstands", type = "repTime"},
        {name = "Pushups", type = "repTime"},
        {name = "Weight", type = "repTime"},
        {name = "Situps", type = "repTime"}
    }
    
    for _, toolInfo in pairs(tools) do
        local tool = player.Backpack:FindFirstChild(toolInfo.name)
        if tool then
            local cooldown = tool:FindFirstChild(toolInfo.type)
            if cooldown then
                cooldown.Value = 0.1
            end
        end
    end
end

punchButton.MouseButton1Click:Connect(function()
    if not isPunching then
        equipPunch()

        if rockPart then
            rockPart.Size = Vector3.new(0.1, 0.1, 0.1)
            rockPart.Position = character.RightHand.Position
        end

        setToolCooldowns()

        isPunching = true
        punchButton.Text = "Stop Punching!"
        
        punchLoop = game:GetService("RunService").Heartbeat:Connect(function()
            muscleEvent:FireServer("punch", "leftHand")
            muscleEvent:FireServer("punch", "rightHand")
        end)
    else
        if punchLoop then
            punchLoop:Disconnect()
        end
        isPunching = false
        punchButton.Text = "Start Punching!"
    end
end)
