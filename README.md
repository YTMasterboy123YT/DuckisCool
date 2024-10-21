local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")
local rockPart = muscleKingMountain:FindFirstChild("Rock")

local originalPosition = rockPart.Position
local isOn = false

-- Function to toggle the Rock's position
function toggleRock()
    isOn = not isOn
    if isOn then
        rockPart.Position = character.RightHand.Position + Vector3.new(0, 0, -2)
        print("Rock teleported to you.")
    else
        rockPart.Position = originalPosition
        print("Rock returned to original position.")
    end
end

-- Example of how to call the function
toggleRock()  -- Call this to teleport the rock
