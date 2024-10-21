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
local punchTool = player.Backpack:FindFirstChild("Punch")  -- Replace with your punch tool name

local isPunching = false
local punchLoop

-- Function to equip punch tool
local function equipPunch()
    if punchTool and not character:FindFirstChild(punchTool.Name) then
        punchTool.Parent = character  -- Equip the punch
    end
end

punchButton.MouseButton1Click:Connect(function()
    if not isPunching then
        equipPunch()  -- Equip the punch tool

        -- Teleport the rock to the player's position
        if rockPart then
            rockPart.Position = character.HumanoidRootPart.Position
        end

        -- Start the punch loop
        isPunching = true
        punchButton.Text = "Stop Punching!"
        
        punchLoop = game:GetService("RunService").Heartbeat:Connect(function()
            muscleEvent:FireServer("punch", "leftHand")
            muscleEvent:FireServer("punch", "rightHand")
        end)
    else
        -- Stop the punch loop
        if punchLoop then
            punchLoop:Disconnect()
        end
        isPunching = false
        punchButton.Text = "Start Punching!"
    end
end)
