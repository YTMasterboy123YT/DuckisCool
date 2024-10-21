local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local button = Instance.new("TextButton")
button.Size = UDim2.new(0, 200, 0, 50)
button.Position = UDim2.new(0.5, -100, 0.5, -25)
button.Text = "Teleport Rock"
button.Parent = screenGui

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local muscleKingMountain = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain")
local rockPart = muscleKingMountain:FindFirstChild("Rock")

local originalPosition = rockPart.Position
local originalSize = rockPart.Size
local isOn = false

button.MouseButton1Click:Connect(function()
    isOn = not isOn
    if isOn then
        rockPart.Position = character.RightHand.Position
        rockPart.Size = Vector3.new(0.1, 0, 0.1)
        
        -- Start auto-punching
        while isOn do
            -- Your auto-punch logic here
            -- For example, you could trigger a punch animation or function
            wait(0.5) -- Adjust the wait time as needed
        end
    else
        rockPart.Position = originalPosition
        rockPart.Size = originalSize
    end
end)
