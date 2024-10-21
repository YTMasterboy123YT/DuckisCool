-- Create a ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Create a TextButton
local button = Instance.new("TextButton")
button.Size = UDim2.new(0, 200, 0, 50)
button.Position = UDim2.new(0.5, -100, 0.5, -25)
button.Text = "Teleport Rock"
button.Parent = screenGui

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")
local rockPart = muscleKingMountain:FindFirstChild("Rock")

local originalPosition = rockPart.Position
local originalSize = rockPart.Size -- Store the original size
local isOn = false

-- Button click event
button.MouseButton1Click:Connect(function()
    isOn = not isOn
    if isOn then
        rockPart.Position = character.RightHand.Position + Vector3.new(0, 0, -2)
        rockPart.Size = Vector3.new(2, 1, 1) -- Set size when teleporting
        button.Text = "Return Rock"
    else
        rockPart.Position = originalPosition
        rockPart.Size = originalSize -- Reset to original size
        button.Text = "Teleport Rock"
    end
end)
