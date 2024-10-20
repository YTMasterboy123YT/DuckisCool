local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")
local rockPart = muscleKingMountain:FindFirstChild("Rock")

while true do
    if rockPart then
        -- Set the CFrame of the Rock part to the RightHand's CFrame
        local rightHand = character:FindFirstChild("RightHand")
        if rightHand then
            rockPart.CFrame = rightHand.CFrame * CFrame.new(0, 0, -2) -- Adjust position relative to RightHand
            rockPart.Size = Vector3.new(141, 123, 149)
        end
    end

    wait(1)
end
