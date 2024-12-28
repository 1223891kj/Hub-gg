-- Configurações do Hub
local hubName = "GG Hub"
local backgroundColor = Color3.fromRGB(0, 0, 0) -- Preto
local optionColor = Color3.fromRGB(255, 0, 0) -- Vermelho
local playerNameColor = Color3.fromRGB(255, 255, 0) -- Amarelo

-- Função para criar o Hub
function createHub()
    local screenGui = Instance.new("ScreenGui")
    local frame = Instance.new("Frame")
    local title = Instance.new("TextLabel")
    local showPlayersButton = Instance.new("TextButton")
    local espButton = Instance.new("TextButton")
    local updateButton = Instance.new("TextButton")
    local toggleButton = Instance.new("TextButton")

    screenGui.Name = hubName
    screenGui.Parent = game.CoreGui

    frame.BackgroundColor3 = backgroundColor
    frame.Size = UDim2.new(0, 300, 0, 400)
    frame.Position = UDim2.new(0.5, -150, 0.5, -200)
    frame.Parent = screenGui

    title.Text = hubName
    title.Size = UDim2.new(1, 0, 0, 50)
    title.TextColor3 = optionColor
    title.Parent = frame

    showPlayersButton.Text = "Ver Jogadores"
    showPlayersButton.Size = UDim2.new(1, 0, 0, 50)
    showPlayersButton.Position = UDim2.new(0, 0, 0, 50)
    showPlayersButton.TextColor3 = optionColor
    showPlayersButton.Parent = frame

    espButton.Text = "ESP"
    espButton.Size = UDim2.new(1, 0, 0, 50)
    espButton.Position = UDim2.new(0, 0, 0, 100)
    espButton.TextColor3 = optionColor
    espButton.Parent = frame

    updateButton.Text = "Atualizar Lista"
    updateButton.Size = UDim2.new(1, 0, 0, 50)
    updateButton.Position = UDim2.new(0, 0, 0, 150)
    updateButton.TextColor3 = optionColor
    updateButton.Parent = frame

    toggleButton.Size = UDim2.new(0, 50, 0, 50)
    toggleButton.Position = UDim2.new(0, 0, 0, 200)
    toggleButton.BackgroundColor3 = optionColor
    toggleButton.Parent = frame

    -- Função para mostrar jogadores
    showPlayersButton.MouseButton1Click:Connect(function()
        for _, player in pairs(game.Players:GetPlayers()) do
            print(player.Name)
        end
    end)

    -- Função para ESP
    espButton.MouseButton1Click:Connect(function()
        for _, player in pairs(game.Players:GetPlayers()) do
            if player ~= game.Players.LocalPlayer then
                local espBox = Instance.new("BoxHandleAdornment")
                espBox.Adornee = player.Character
                espBox.Size = Vector3.new(4, 6, 4)
                espBox.Color3 = playerNameColor
                espBox.AlwaysOnTop = true
                espBox.Parent = player.Character
            end
        end
    end)

    -- Função para atualizar a lista de jogadores
    updateButton.MouseButton1Click:Connect(function()
        for _, player in pairs(game.Players:GetPlayers()) do
            print("Atualizando: " .. player.Name)
        end
    end)

    -- Função para abrir/fechar o Hub
    toggleButton.MouseButton1Click:Connect(function()
        frame.Visible = not frame.Visible
    end)
end

createHub()

-- Função para ajustar o FOV
function setFOV(value)
    game.Workspace.CurrentCamera.FieldOfView = value
end

setFOV(120) -- Ajuste o valor conforme necessário

