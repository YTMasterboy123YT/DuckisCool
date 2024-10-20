local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")

while true do
    if muscleKingMountain then
        local clone = muscleKingMountain:Clone()
        clone.Parent = game.Workspace

        local rockPart = clone:FindFirstChild("Rock")
        if rockPart then
            rockPart.CFrame = CFrame.new(-8972, 27, -6061) * CFrame.Angles(0, math.rad(180), 0)
            rockPart.Size = Vector3.new(141, 123, 149)
        end
    end

    wait(1)
end
