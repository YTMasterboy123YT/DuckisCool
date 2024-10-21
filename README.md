local button = script.Parent
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")
local rockPart = muscleKingMountain:FindFirstChild("Rock")

local originalPosition = rockPart.Position
local isOn = false

button.Size = UDim2.new(0, 200, 0, 50)
button.Position = UDim2.new(0.5, -100, 0.5, -25)
button.Text = "Teleport Rock"

button.MouseButton1Click:Connect(function()
    isOn = not isOn
    if isOn then
        button.Text = "Return Rock"
        rockPart.Position = character.RightHand.Position + Vector3.new(0, 0, -2)
    else
        button.Text = "Teleport Rock"
        rockPart.Position = originalPosition
    end
end)
