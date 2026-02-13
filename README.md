local p = game.Players.LocalPlayer
local UIS = game:GetService("UserInputService")
local Tween = game:GetService("TweenService")

local phone = p.PlayerGui:WaitForChild("PhoneGUI"):WaitForChild("Phone")

local startY
local unlocked = false

phone.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        startY = input.Position.Y
    end
end)

phone.InputEnded:Connect(function(input)
    if unlocked then return end
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        if startY and startY - input.Position.Y > 80 then
            unlocked = true
            Tween:Create(phone,TweenInfo.new(0.3),{
            BackgroundColor3 = Color3.fromRGB(25,25,25)
            }):Play()
        end
    end
end)
