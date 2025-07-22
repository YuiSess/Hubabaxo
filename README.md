local Players = game:GetService("Players")
local player = Players.LocalPlayer

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "RedzHubMockup"
ScreenGui.Parent = player:WaitForChild("PlayerGui")

local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 500, 0, 550)
mainFrame.Position = UDim2.new(0, 20, 0, 20)
mainFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
mainFrame.BorderSizePixel = 0
mainFrame.Parent = ScreenGui

-- Título superior
local title = Instance.new("TextLabel")
title.Text = "redz Hub : Blox Fruits"
title.Size = UDim2.new(1, -40, 0, 40)
title.Position = UDim2.new(0, 20, 0, 10)
title.BackgroundTransparency = 1
title.TextColor3 = Color3.fromRGB(220, 220, 220)
title.Font = Enum.Font.GothamBold
title.TextSize = 24
title.TextXAlignment = Enum.TextXAlignment.Left
title.Parent = mainFrame

local subtitle = Instance.new("TextLabel")
subtitle.Text = "by real_redz"
subtitle.Size = UDim2.new(1, -40, 0, 15)
subtitle.Position = UDim2.new(0, 20, 0, 50)
subtitle.BackgroundTransparency = 1
subtitle.TextColor3 = Color3.fromRGB(140, 140, 140)
subtitle.Font = Enum.Font.Gotham
subtitle.TextSize = 12
subtitle.TextXAlignment = Enum.TextXAlignment.Left
subtitle.Parent = mainFrame

-- Container geral: lado esquerdo menu + lado direito conteúdo
local container = Instance.new("Frame")
container.Size = UDim2.new(1, -40, 1, -80)
container.Position = UDim2.new(0, 20, 0, 70)
container.BackgroundTransparency = 1
container.Parent = mainFrame

-- Menu lateral
local menu = Instance.new("Frame")
menu.Size = UDim2.new(0, 140, 1, 0)
menu.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
menu.BorderSizePixel = 0
menu.Parent = container

local UIListLayoutMenu = Instance.new("UIListLayout")
UIListLayoutMenu.Padding = UDim.new(0, 6)
UIListLayoutMenu.FillDirection = Enum.FillDirection.Vertical
UIListLayoutMenu.SortOrder = Enum.SortOrder.LayoutOrder
UIListLayoutMenu.Parent = menu

-- Função para criar botões do menu lateral
local function criarBotaoMenu(text)
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(1, 0, 0, 36)
    btn.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
    btn.BorderSizePixel = 0
    btn.Text = text
    btn.TextColor3 = Color3.fromRGB(180, 180, 180)
    btn.Font = Enum.Font.GothamSemibold
    btn.TextSize = 16
    btn.AutoButtonColor = false
    btn.Parent = menu

    -- Hover effect
    btn.MouseEnter:Connect(function()
        btn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    end)
    btn.MouseLeave:Connect(function()
        btn.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
    end)

    return btn
end

local abas = {
    "Discord",
    "Farmar",
    "Missões/Itens",
    "Fruta/Raid",
    "Hop",
    "Stats",
    "Teleporte",
    "Status",
    "Visual",
    "Loja",
    "Diversos",
}

local botoesMenu = {}

for i, nome in ipairs(abas) do
    botoesMenu[nome] = criarBotaoMenu(nome)
end

-- Conteúdo da aba "Farmar"
local farmarFrame = Instance.new("Frame")
farmarFrame.Size = UDim2.new(1, -150, 1, 0)
farmarFrame.Position = UDim2.new(0, 150, 0, 0)
farmarFrame.BackgroundTransparency = 1
farmarFrame.Parent = container
farmarFrame.Visible = true

-- Título Farmar
local farmarTitle = Instance.new("TextLabel")
farmarTitle.Text = "Farmar"
farmarTitle.Size = UDim2.new(1, 0, 0, 28)
farmarTitle.BackgroundTransparency = 1
farmarTitle.TextColor3 = Color3.fromRGB(230, 230, 230)
farmarTitle.Font = Enum.Font.GothamBold
farmarTitle.TextSize = 20
farmarTitle.TextXAlignment = Enum.TextXAlignment.Left
farmarTitle.Parent = farmarFrame

-- Função para criar seção com toggle
local function criarOpcaoToggle(parent, nome, desc, yPos)
    local container = Instance.new("Frame")
    container.Size = UDim2.new(1, 0, 0, 55)
    container.Position = UDim2.new(0, 0, 0, yPos)
    container.BackgroundTransparency = 1
    container.Parent = parent

    local labelNome = Instance.new("TextLabel")
    labelNome.Text = nome
    labelNome.Position = UDim2.new(0, 0, 0, 0)
    labelNome.Size = UDim2.new(1, -70, 0, 22)
    labelNome.BackgroundTransparency = 1
    labelNome.Font = Enum.Font.GothamSemibold
    labelNome.TextSize = 16
    labelNome.TextColor3 = Color3.fromRGB(220, 220, 220)
    labelNome.TextXAlignment = Enum.TextXAlignment.Left
    labelNome.Parent = container

    local labelDesc = Instance.new("TextLabel")
    labelDesc.Text = desc
    labelDesc.Position = UDim2.new(0, 0, 0, 22)
    labelDesc.Size = UDim2.new(1, -70, 0, 30)
    labelDesc.BackgroundTransparency = 1
    labelDesc.Font = Enum.Font.Gotham
    labelDesc.TextSize = 12
    labelDesc.TextColor3 = Color3.fromRGB(160, 160, 160)
    labelDesc.TextXAlignment = Enum.TextXAlignment.Left
    labelDesc.TextWrapped = true
    labelDesc.Parent = container

    -- Toggle button
    local toggleBtn = Instance.new("Frame")
    toggleBtn.Size = UDim2.new(0, 40, 0, 20)
    toggleBtn.Position = UDim2.new(1, -45, 0, 15)
    toggleBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    toggleBtn.BorderSizePixel = 0
    toggleBtn.Parent = container
    toggleBtn.AnchorPoint = Vector2.new(0, 0)

    local circle = Instance.new("Frame")
    circle.Size = UDim2.new(0, 18, 0, 18)
    circle.Position = UDim2.new(0, 1, 0, 1)
    circle.BackgroundColor3 = Color3.fromRGB(180, 180, 180)
    circle.BorderSizePixel = 0
    circle.Parent = toggleBtn
    circle.AnchorPoint = Vector2.new(0, 0)
    circle.Name = "Circle"

    local toggled = false
    toggleBtn.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            toggled = not toggled
            if toggled then
                circle:TweenPosition(UDim2.new(1, -19, 0, 1), "Out", "Quad", 0.2, true)
                toggleBtn.BackgroundColor3 = Color3.fromRGB(80, 200, 120)
            else
                circle:TweenPosition(UDim2.new(0, 1, 0, 1), "Out", "Quad", 0.2, true)
                toggleBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
            end
        end
    end)

    return toggleBtn
end

-- Função para criar seção com dropdown simples
local function criarDropdown(parent, nome, desc, yPos, options)
    local container = Instance.new("Frame")
    container.Size = UDim2.new(1, 0, 0, 55)
    container.Position = UDim2.new(0, 0, 0, yPos)
    container.BackgroundTransparency = 1
    container.Parent = parent

    local labelNome = Instance.new("TextLabel")
    labelNome.Text = nome
    labelNome.Position = UDim2.new(0, 0, 0, 0)
    labelNome.Size = UDim2.new(1, -120, 0, 22)
    labelNome.BackgroundTransparency = 1
    labelNome.Font = Enum.Font.GothamSemibold
    labelNome.TextSize = 16
    labelNome.TextColor3 = Color3.fromRGB(220, 220, 220)
    labelNome.TextXAlignment = Enum.TextXAlignment.Left
    labelNome.Parent = container

    local labelDesc = Instance.new("TextLabel")
    labelDesc.Text = desc
    labelDesc.Position = UDim2.new(0, 0, 0, 22)
    labelDesc.Size = UDim2.new(1, -120, 0, 30)
    labelDesc.BackgroundTransparency = 1
    labelDesc.Font = Enum.Font.Gotham
    labelDesc.TextSize = 12
    labelDesc.TextColor3 = Color3.fromRGB(160, 160, 160)
    labelDesc.TextXAlignment = Enum.TextXAlignment.Left
    labelDesc.TextWrapped = true
    labelDesc.Parent = container

    local dropdown = Instance.new("TextButton")
    dropdown.Size = UDim2.new(0, 110, 0, 28)
    dropdown.Position = UDim2.new(1, -110, 0, 13)
    dropdown.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
    dropdown.BorderSizePixel = 0
    dropdown.TextColor3 = Color3.fromRGB(200, 200, 200)
    dropdown.Font = Enum.Font.Gotham
    dropdown.TextSize = 14
    dropdown.Text = options[1]
    dropdown.Parent = container

    local open = false
    local optionsFrame = Instance.new("Frame")
    optionsFrame.Size = UDim2.new(0, 110, 0, #options * 25)
    optionsFrame.Position = UDim2.new(1, -110, 0, 41)
    optionsFrame.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
    optionsFrame.BorderSizePixel = 0
    optionsFrame.Visible = false
    optionsFrame.Parent = container

    local UIListLayoutOptions = Instance.new("UIListLayout")
    UIListLayoutOptions.Padding = UDim.new(0, 2)
    UIListLayoutOptions.FillDirection = Enum.FillDirection.Vertical
    UIListLayoutOptions.SortOrder = Enum.SortOrder.LayoutOrder
    UIListLayoutOptions.Parent = optionsFrame

    for _, option in ipairs(options) do
        local optionBtn = Instance.new("TextButton")
        optionBtn.Size = UDim2.new(1, 0, 0, 22)
        optionBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
        optionBtn.BorderSizePixel = 0
        optionBtn.TextColor3 = Color3.fromRGB(220, 220, 220)
        optionBtn.Font = Enum.Font.Gotham
        optionBtn.TextSize = 14
        optionBtn.Text = option
        optionBtn.Parent = optionsFrame

        optionBtn.MouseButton1Click:Connect(function()
            dropdown.Text = option
            optionsFrame.Visible = false
            open = false
        end)
    end

    dropdown.MouseButton1Click:Connect(function()
        open = not open
        optionsFrame.Visible = open
    end)

    return dropdown
end

-- Adicionar as opções na aba Farmar conforme a imagem

local yOffset = 40

-- Selecionar Ferramenta (dropdown)
criarDropdown(farmarFrame, "Selecionar Ferramenta", "Escolha a ferramenta que deseja usar", yOffset, {"Melee", "Sword", "Gun"})
yOffset = yOffset + 65

-- Tamanho da UI (dropdown)
criarDropdown(farmarFrame, "Tamanho da UI", "Ajuste o tamanho da interface de usuário", yOffset, {"Small", "Medium", "Large"})
yOffset = yOffset + 65

-- Seção Farmar (título)
local farmarSubTitle = Instance.new("TextLabel")
farmarSubTitle.Text = "Farmar"
farmarSubTitle.Size = UDim2.new(1, 0, 0, 20)
farmarSubTitle.Position = UDim2.new(0, 0, 0, yOffset)
farmarSubTitle.BackgroundTransparency = 1
farmarSubTitle.Font = Enum.Font.GothamBold
farmarSubTitle.TextSize = 16
farmarSubTitle.TextColor3 = Color3.fromRGB(240, 240, 240)
farmarSubTitle.TextXAlignment = Enum.TextXAlignment.Left
farmarSubTitle.Parent = farmarFrame
yOffset = yOffset + 30

-- Level Automático (toggle)
criarOpcaoToggle(farmarFrame, "Level Automático", "Farma niveis automaticamente", yOffset)
yOffset = yOffset + 55

-- Farmar Inimigos Próximos (toggle)
criarOpcaoToggle(farmarFrame, "Farmar Inimigos Próximos", "Mata inimigos próximos automaticamente", yOffset)
yOffset = yOffset + 55

-- Seção Baús
local bausTitle = Instance.new("TextLabel")
bausTitle.Text = "Baús"
bausTitle.Size = UDim2.new(1, 0, 0, 20)
bausTitle.Position = UDim2.new(0, 0, 0, yOffset)
bausTitle.BackgroundTransparency = 1
bausTitle.Font = Enum.Font.GothamBold
bausTitle.TextSize = 16
bausTitle.TextColor3 = Color3.fromRGB(240, 240, 240)
bausTitle.TextXAlignment = Enum.TextXAlignment.Left
bausTitle.Parent = farmarFrame
yOffset = yOffset + 30

-- Auto Baús [Tween] (toggle)
criarOpcaoToggle(farmarFrame, "Auto Baús [Tween]", "Coleta cofres automaticamente usando Tween", yOffset)
yOffset = yOffset + 55

-- Seção Chefes
local chefesTitle = Instance.new("TextLabel")
chefesTitle.Text = "Chefes"
chefesTitle.Size = UDim2.new(1, 0, 0, 20)
chefesTitle.Position = UDim2.new(0, 0, 0, yOffset)
chefesTitle.BackgroundTransparency = 1
chefesTitle.Font = Enum.Font.GothamBold
chefesTitle.TextSize = 16
chefesTitle.TextColor3 = Color3.fromRGB(240, 240, 240)
chefesTitle.TextXAlignment = Enum.TextXAlignment.Left
chefesTitle.Parent = farmarFrame
yOffset = yOffset + 30

-- Atualizar Lista de Bosses (botão)
local atualizarBossesBtn = Instance.new("TextButton")
atualizarBossesBtn.Text = "Atualizar Lista de Bosses"
atualizarBossesBtn.Size = UDim2.new(0.6, 0, 0, 36)
atualizarBossesBtn.Position = UDim2.new(0, 0, 0, yOffset)
atualizarBossesBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
atualizarBossesBtn.BorderSizePixel = 0
atualizarBossesBtn.TextColor3 = Color3.fromRGB(220, 220, 220)
atualizarBossesBtn.Font = Enum.Font.GothamBold
atualizarBossesBtn.TextSize = 16
atualizarBossesBtn.Parent = farmarFrame
yOffset = yOffset + 46

-- Lista de Bosses (dropdown)
criarDropdown(farmarFrame, "Lista de Bosses", "Seleciona um boss para atacar", yOffset, {"nil", "Boss1", "Boss2", "Boss3"})
yOffset = yOffset + 65

-- Matar Boss Selecionado (toggle)
criarOpcaoToggle(farmarFrame, "Matar Boss Selecionado", "Ataca automaticamente o boss selecionado", yOffset)
yOffset = yOffset + 55

-- Esconder todas abas menos "Farmar"
for nome, botao in pairs(botoesMenu) do
    if nome ~= "Farmar" then
        botao.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
        botao.TextColor3 = Color3.fromRGB(100, 100, 100)
        botao.AutoButtonColor = false
        botao.Active = false
    else
        botao.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
        botao.TextColor3 = Color3.fromRGB(255, 168, 0)
    end
end
