local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleKingLift = game.Workspace.machinesFolder:FindFirstChild("Muscle King Lift")

while true do
    if muscleKingLift then
        -- Get the right hand position
        local rightHand = character:FindFirstChild("RightHand")
        
        if rightHand then
            -- Clone the rock
            local clone = muscleKingLift:Clone()
            clone.Parent = game.Workspace
            
            -- Set the new position near the right hand
            clone.CFrame = rightHand.CFrame * CFrame.new(0, 0, -2) -- Adjust the offset as needed
        end
    else
        print("Muscle King Lift not found!")
    end
    
    wait(1) -- Wait for a second before repeating
end
