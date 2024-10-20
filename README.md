local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local DropdownButton = Instance.new("TextButton")
local DropdownList = Instance.new("Frame")
local Options = {"1", "2", "3"}
local SelectedValues = {}

ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
Frame.Parent = ScreenGui
Frame.Size = UDim2.new(0, 200, 0, 300)
Frame.Position = UDim2.new(0.5, -100, 0.5, -150)

DropdownButton.Parent = Frame
DropdownButton.Size = UDim2.new(1, 0, 0, 50)
DropdownButton.Text = "Select Options"

DropdownList.Parent = Frame
DropdownList.Size = UDim2.new(1, 0, 0, 0)
DropdownList.Position = UDim2.new(0, 0, 0, 50)
DropdownList.Visible = false

for _, option in ipairs(Options) do
    local OptionButton = Instance.new("TextButton")
    OptionButton.Parent = DropdownList
    OptionButton.Size = UDim2.new(1, 0, 0, 40)
    OptionButton.Text = option
    OptionButton.MouseButton1Click:Connect(function()
        if not SelectedValues[option] then
            SelectedValues[option] = true
            print("Selected: " .. option)
        else
            SelectedValues[option] = nil
            print("Deselected: " .. option)
        end
    end)
end

DropdownButton.MouseButton1Click:Connect(function()
    DropdownList.Visible = not DropdownList.Visible
end)

