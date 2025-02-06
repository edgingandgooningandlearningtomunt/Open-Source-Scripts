--[[
I DID NOT MAKE THIS ORIGINAL POST HERE https://scriptblox.com/script/Universal-Script-Rizzler-Bypasser-28663 Ria Executor: https://discord.gg/8mmt6PMCum
]]

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local TextChatService = game:GetService("TextChatService")
local UserInputService = game:GetService("UserInputService")

local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local TextBox = Instance.new("TextBox")
local Button = Instance.new("TextButton")
local UICorner = Instance.new("UICorner")
local ButtonCorner = Instance.new("UICorner")

ScreenGui.Parent = Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.Name = "Rizzler Bypasser"

Frame.Parent = ScreenGui
Frame.Size = UDim2.new(0, 320, 0, 180)
Frame.Position = UDim2.new(0.5, -160, 0.5, -90)
Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Frame.BorderSizePixel = 0
Frame.Active = true 

UICorner.Parent = Frame
UICorner.CornerRadius = UDim.new(0, 10) 

Title.Parent = Frame
Title.Size = UDim2.new(1, 0, 0, 30)
Title.Position = UDim2.new(0, 0, 0, 0)
Title.BackgroundTransparency = 1
Title.Text = "Rizzler Bypass"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.Font = Enum.Font.GothamBold
Title.TextSize = 18

TextBox.Parent = Frame
TextBox.Size = UDim2.new(0, 300, 0, 50)
TextBox.Position = UDim2.new(0, 10, 0, 40)
TextBox.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
TextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
TextBox.PlaceholderText = "Enter text..."
TextBox.Font = Enum.Font.Gotham
TextBox.TextSize = 16
TextBox.Text = "I rape niggers"
TextBox.ClearTextOnFocus = false 

Button.Parent = Frame
Button.Size = UDim2.new(0, 300, 0, 40)
Button.Position = UDim2.new(0, 10, 0, 100)
Button.BackgroundColor3 = Color3.fromRGB(50, 100, 255)
Button.TextColor3 = Color3.fromRGB(255, 255, 255)
Button.Text = "Bypass"
Button.Font = Enum.Font.GothamBold
Button.TextSize = 18

ButtonCorner.Parent = Button
ButtonCorner.CornerRadius = UDim.new(0, 8)

local dragging, dragInput, startPos, startMousePos

Frame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = true
        startMousePos = input.Position
        startPos = Frame.Position
        input.Changed:Connect(function()
            if input.UserInputState == Enum.UserInputState.End then
                dragging = false
            end
        end)
    end
end)

Frame.InputChanged:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement then
        dragInput = input
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if input == dragInput and dragging then
        local delta = input.Position - startMousePos
        Frame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
end)

local function getRandomSymbol()
    local symbols = {"<", ".", ".-"}
    return symbols[math.random(#symbols)]
end

local function convertText(text)
    local converted = ""
    for i = 1, #text do
        local char = text:sub(i, i)
        if char == " " then
            converted = converted .. ".+.+"
        else
            converted = converted .. char .. getRandomSymbol()
        end
    end
    return converted
end

local function sendMessage()
    local message = convertText(TextBox.Text)
    TextBox.Text = ""

    if TextChatService.ChatVersion == Enum.ChatVersion.TextChatService then
        
        local chatChannel = TextChatService.TextChannels:FindFirstChild("RBXGeneral")
        if chatChannel then
            chatChannel:SendAsync(message)
        end
    else
        local chatEvent = ReplicatedStorage:FindFirstChild("DefaultChatSystemChatEvents")
        if chatEvent then
            local sayMessageRequest = chatEvent:FindFirstChild("SayMessageRequest")
            if sayMessageRequest then
                sayMessageRequest:FireServer(message, "All")
            end
        end
    end
end

Button.MouseButton1Click:Connect(sendMessage)
