local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")

while true do
    if muscleKingMountain then
        -- Get the right hand position
        local rightHand = character:FindFirstChild("RightHand")
        
        if rightHand then
            -- Clone the rock
            local clone = muscleKingMountain:Clone()
            clone.Parent = game.Workspace
            
            -- Set the new position near the right hand
            clone.CFrame = rightHand.CFrame * CFrame.new(0, 0, -2) -- Adjust the offset as needed
        end
    else
        print("Muscle King Mountain not found!")
    end
    
    wait(1) -- Wait for a second before repeating
end
