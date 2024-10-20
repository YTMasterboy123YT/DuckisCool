local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")

while true do
    if muscleKingMountain then
        -- Get your position
        local playerPosition = character.PrimaryPart.Position
        
        -- Get the right hand position
        local rightHand = character:FindFirstChild("RightHand")
        
        if rightHand then
            -- Set the new position near the right hand
            muscleKingMountain.CFrame = rightHand.CFrame * CFrame.new(0, 0, -2) -- Adjust the offset as needed
        end
    else
        print("Muscle King Mountain not found!")
    end
    
    wait(1) -- Wait for a second before repeating
end
