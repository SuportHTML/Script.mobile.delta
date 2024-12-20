-- Criação da Interface Gráfica
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local OpenCloseButton = Instance.new("TextButton")
local Title = Instance.new("TextLabel")
local EspButton = Instance.new("TextButton")
local TerremotoButton = Instance.new("TextButton")
local CreatorLabel = Instance.new("TextLabel")

-- Propriedades da Interface
ScreenGui.Name = "Hub"
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 40)
MainFrame.Size = UDim2.new(0, 300, 0, 400)
MainFrame.Position = UDim2.new(0.5, -150, 0.5, -200)
MainFrame.Visible = true

OpenCloseButton.Name = "OpenCloseButton"
OpenCloseButton.Parent = ScreenGui
OpenCloseButton.Text = "Abrir/Fechar"
OpenCloseButton.Position = UDim2.new(0, 10, 0, 10)
OpenCloseButton.Size = UDim2.new(0, 100, 0, 40)
OpenCloseButton.BackgroundColor3 = Color3.fromRGB(20, 20, 80)
OpenCloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)

Title.Name = "Title"
Title.Parent = MainFrame
Title.Text = "Hub - Menu"
Title.Font = Enum.Font.SourceSansBold
Title.TextSize = 24
Title.Size = UDim2.new(1, 0, 0, 50)
Title.BackgroundTransparency = 1
Title.TextColor3 = Color3.fromRGB(255, 255, 255)

EspButton.Name = "EspButton"
EspButton.Parent = MainFrame
EspButton.Text = "ESP (Ver jogadores pelas paredes)"
EspButton.Size = UDim2.new(0, 250, 0, 50)
EspButton.Position = UDim2.new(0.5, -125, 0, 100)
EspButton.BackgroundColor3 = Color3.fromRGB(20, 20, 80)
EspButton.TextColor3 = Color3.fromRGB(255, 255, 255)

TerremotoButton.Name = "TerremotoButton"
TerremotoButton.Parent = MainFrame
TerremotoButton.Text = "Terremoto (Somente executor)"
TerremotoButton.Size = UDim2.new(0, 250, 0, 50)
TerremotoButton.Position = UDim2.new(0.5, -125, 0, 170)
TerremotoButton.BackgroundColor3 = Color3.fromRGB(20, 20, 80)
TerremotoButton.TextColor3 = Color3.fromRGB(255, 255, 255)

CreatorLabel.Name = "CreatorLabel"
CreatorLabel.Parent = MainFrame
CreatorLabel.Text = "Criador: Ismael Sampaio Custódio"
CreatorLabel.Size = UDim2.new(1, 0, 0, 30)
CreatorLabel.Position = UDim2.new(0, 0, 1, -40)
CreatorLabel.BackgroundTransparency = 1
CreatorLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
CreatorLabel.Font = Enum.Font.SourceSans
CreatorLabel.TextSize = 18

-- Função de Abrir/Fechar
local isFrameVisible = true
OpenCloseButton.MouseButton1Click:Connect(function()
    isFrameVisible = not isFrameVisible
    MainFrame.Visible = isFrameVisible
end)

-- Função do Botão ESP
EspButton.MouseButton1Click:Connect(function()
    for _, player in pairs(game.Players:GetPlayers()) do
        if player ~= game.Players.LocalPlayer then
            local highlight = Instance.new("Highlight")
            highlight.Parent = player.Character
            highlight.FillColor = Color3.new(1, 0, 0)
        end
    end
end)

-- Função do Botão Terremoto
TerremotoButton.MouseButton1Click:Connect(function()
    local character = game.Players.LocalPlayer.Character
    if character then
        local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
        if humanoidRootPart then
            for i = 1, 10 do
                humanoidRootPart.Position = humanoidRootPart.Position + Vector3.new(0, math.random(-2, 2), 0)
                wait(0.1)
            end
        end
    end
end)
