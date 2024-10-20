local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")

while true do
    if muscleKingMountain then
        local clone = muscleKingMountain:Clone()
        clone.Parent = game.Workspace

        -- Set the CFrame of the PrimaryPart named "Rock"
        if clone.PrimaryPart then
            clone:SetPrimaryPartCFrame(CFrame.new(-8972.83887, 5.49686861, -6124.23877, 
                                                   -0.993763864, -1.41056065e-08, 0.111505143, 
                                                   -6.75961909e-09, 1, 6.6258302e-08, 
                                                   -0.111505143, 6.50913705e-08, -0.993763864))
        else
            print("PrimaryPart 'Rock' not found!")
        end
    else
        print("Muscle King Mountain not found!")
    end

    wait(1)
end
