local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")

if muscleKingMountain then
    -- Get your position
    local playerPosition = character.PrimaryPart.Position

    -- Teleport the rock to your position
    muscleKingMountain.CFrame = CFrame.new(playerPosition) * CFrame.Angles(0, math.rad(180), 0) -- Optional rotation
else
    print("Muscle King Mountain not found!")
end
