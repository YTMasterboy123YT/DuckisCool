local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Button for Punching Left Hand
local leftPunchButton = Instance.new("TextButton")
leftPunchButton.Size = UDim2.new(0, 200, 0, 50)
leftPunchButton.Position = UDim2.new(0.5, -100, 0.5, -25)
leftPunchButton.Text = "Punch Left"
leftPunchButton.Parent = screenGui

-- Button for Punching Right Hand
local rightPunchButton = Instance.new("TextButton")
rightPunchButton.Size = UDim2.new(0, 200, 0, 50)
rightPunchButton.Position = UDim2.new(0.5, -100, 0.6, -25)
rightPunchButton.Text = "Punch Right"
rightPunchButton.Parent = screenGui

local player = game.Players.LocalPlayer

-- Event for Left Punch
leftPunchButton.MouseButton1Click:Connect(function()
    player.muscleEvent:FireServer("punch", "leftHand")
end)

-- Event for Right Punch
rightPunchButton.MouseButton1Click:Connect(function()
    player.muscleEvent:FireServer("punch", "rightHand")
end)
