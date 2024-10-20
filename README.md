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
            
            -- Find the primary part of the model (if set)
            local primaryPart = clone.PrimaryPart or clone:FindFirstChildWhichIsA("Part")

            if primaryPart then
                -- Set the new position near the right hand
                primaryPart.CFrame = rightHand.CFrame * CFrame.new(0, 0, -2) -- Adjust the offset as needed
            else
                print("No primary part found in Muscle King Lift model!")
            end
        end
    else
        print("Muscle King Lift not found!")
    end
    
    wait(1) -- Wait for a second before repeating
end
