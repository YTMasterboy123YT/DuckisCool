local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local punchButton = Instance.new("TextButton")
punchButton.Size = UDim2.new(0, 200, 0, 50)
punchButton.Position = UDim2.new(0.5, -100, 0.5, -25)
punchButton.Text = "Punch Left"
punchButton.Parent = screenGui

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleEvent = player:WaitForChild("muscleEvent")
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")
local rockPart = muscleKingMountain:FindFirstChild("Rock")

-- Remove hoopParticle and rockEmitter
if rockPart then
    local hoopParticle = rockPart:FindFirstChild("hoopParticle")
    if hoopParticle then
        hoopParticle:Destroy()
    end

    local rockEmitter = rockPart:FindFirstChild("rockEmitter")
    if rockEmitter then
        rockEmitter:Destroy()
    end
end

local isLeftHand = true

punchButton.MouseButton1Click:Connect(function()
    if isLeftHand then
        rockPart.Position = character.LeftHand.Position
        muscleEvent:FireServer("punch", "leftHand")
        punchButton.Text = "Punch Right"
    else
        rockPart.Position = character.RightHand.Position
        muscleEvent:FireServer("punch", "rightHand")
        punchButton.Text = "Punch Left"
    end
    isLeftHand = not isLeftHand
end)
