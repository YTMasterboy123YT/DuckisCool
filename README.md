local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")

while true do
    if muscleKingMountain then
        local clone = muscleKingMountain:Clone()
        clone.Parent = game.Workspace

        -- Set the CFrame to your character's position
        local characterPosition = character.PrimaryPart.Position
        clone:SetPrimaryPartCFrame(CFrame.new(characterPosition.x, characterPosition.y, characterPosition.z))
    else
        print("Muscle King Mountain not found!")
    end

    wait(1)
end
