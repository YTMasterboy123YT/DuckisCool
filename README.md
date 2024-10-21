local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local punchButton = Instance.new("TextButton")
punchButton.Size = UDim2.new(0, 200, 0, 50)
punchButton.Position = UDim2.new(0.5, -100, 0.5, -25)
punchButton.Text = "Punch Left"
punchButton.Parent = screenGui

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleEvent = player:WaitForChild("muscleEvent")  -- Ensure muscleEvent exists
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")
local rockPart = muscleKingMountain:FindFirstChild("Rock")

local isLeftHand = true  -- Toggle variable for left/right punch

punchButton.MouseButton1Click:Connect(function()
    -- Teleport the rock to the appropriate hand
    if isLeftHand then
        rockPart.Position = character.LeftHand.Position
        muscleEvent:FireServer("punch", "leftHand")  -- Fire punch event for left hand
        punchButton.Text = "Punch Right"  -- Update button text
    else
        rockPart.Position = character.RightHand.Position
        muscleEvent:FireServer("punch", "rightHand")  -- Fire punch event for right hand
        punchButton.Text = "Punch Left"  -- Update button text
    end
    isLeftHand = not isLeftHand  -- Toggle the hand
end)
