local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")
local originalRock = muscleKingMountain:FindFirstChild("Rock")

if originalRock then
    local clone = originalRock:Clone()
    clone.Name = "Muscle King"
    clone.Parent = game.Workspace

    local rightHand = character:FindFirstChild("RightHand")
    if rightHand then
        clone.CFrame = rightHand.CFrame * CFrame.new(0, 0, -2)
        clone.Size = Vector3.new(2, 1, 1)
    end
end
