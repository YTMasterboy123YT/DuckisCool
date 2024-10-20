local player = game.Players.LocalPlayer
local lift = workspace.machinesFolder["Muscle King Lift"]

if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
    local playerPosition = player.Character.HumanoidRootPart.Position
    lift.CFrame = CFrame.new(playerPosition + Vector3.new(5, 0, 0)) -- Adjust the Vector3 values as needed
end
