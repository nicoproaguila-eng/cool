-- NICO HUB PRO UI 👻

local player = game.Players.LocalPlayer
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")

local KEY = "NicoPizza"

local gui = Instance.new("ScreenGui", game.CoreGui)

-- ===== PLAYER =====
local char, humanoid, root

local function updateChar()
	char = player.Character or player.CharacterAdded:Wait()
	humanoid = char:WaitForChild("Humanoid")
	root = char:WaitForChild("HumanoidRootPart")
end

updateChar()
player.CharacterAdded:Connect(updateChar)

-- ===== TEXTO =====
local function floatingText(text)
	local label = Instance.new("TextLabel", gui)
	label.Size = UDim2.new(0,400,0,50)
	label.Position = UDim2.new(0.5,-200,0,50)
	label.BackgroundTransparency = 1
	label.Text = text
	label.TextColor3 = Color3.fromRGB(255,255,255)
	label.Font = Enum.Font.GothamBold
	label.TextSize = 28
	label.TextTransparency = 1

	TweenService:Create(label, TweenInfo.new(0.3), {TextTransparency = 0}):Play()
	task.wait(2)
	TweenService:Create(label, TweenInfo.new(0.3), {TextTransparency = 1}):Play()
	task.wait(0.3)
	label:Destroy()
end

floatingText("👻 Nico Hub Loaded")

-- ===== KEY UI =====
local keyFrame = Instance.new("Frame", gui)
keyFrame.Size = UDim2.new(0,320,0,200)
keyFrame.Position = UDim2.new(0.5,-160,0.5,-100)
keyFrame.BackgroundColor3 = Color3.fromRGB(25,25,25)
Instance.new("UICorner", keyFrame)

local keyTitle = Instance.new("TextLabel", keyFrame)
keyTitle.Size = UDim2.new(1,0,0,40)
keyTitle.Text = "🔐 Nico Hub - Key"
keyTitle.BackgroundTransparency = 1
keyTitle.TextColor3 = Color3.new(1,1,1)
keyTitle.Font = Enum.Font.GothamBold

local input = Instance.new("TextBox", keyFrame)
input.Size = UDim2.new(0.8,0,0,40)
input.Position = UDim2.new(0.1,0,0.4,0)
input.PlaceholderText = "Enter key..."
input.BackgroundColor3 = Color3.fromRGB(35,35,35)
input.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", input)

local check = Instance.new("TextButton", keyFrame)
check.Size = UDim2.new(0.6,0,0,40)
check.Position = UDim2.new(0.2,0,0.7,0)
check.Text = "ENTER"
check.BackgroundColor3 = Color3.fromRGB(0,170,255)
check.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", check)

-- ===== HUB UI =====
local hub = Instance.new("Frame", gui)
hub.Size = UDim2.new(0,330,0,380)
hub.Position = UDim2.new(0.5,-165,0.5,-190)
hub.BackgroundColor3 = Color3.fromRGB(20,20,20)
hub.Visible = false
Instance.new("UICorner", hub)

-- HEADER
local header = Instance.new("TextLabel", hub)
header.Size = UDim2.new(1,0,0,45)
header.Text = "👻 Nico Hub"
header.BackgroundTransparency = 1
header.TextColor3 = Color3.new(1,1,1)
header.Font = Enum.Font.GothamBold
header.TextSize = 20

-- LINEA DECORATIVA
local line = Instance.new("Frame", hub)
line.Size = UDim2.new(0.9,0,0,2)
line.Position = UDim2.new(0.05,0,0,45)
line.BackgroundColor3 = Color3.fromRGB(0,170,255)

-- TOGGLE
local toggle = Instance.new("TextButton", gui)
toggle.Size = UDim2.new(0,130,0,35)
toggle.Position = UDim2.new(0,10,0.5,-20)
toggle.Text = "👻 Nico Hub"
toggle.Visible = false
toggle.BackgroundColor3 = Color3.fromRGB(30,30,30)
toggle.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", toggle)

toggle.MouseButton1Click:Connect(function()
	hub.Visible = not hub.Visible
end)

-- BOTONES PRO
local function createButton(text, y)
	local b = Instance.new("TextButton", hub)
	b.Size = UDim2.new(0.85,0,0,40)
	b.Position = UDim2.new(0.075,0,0,y)
	b.Text = text
	b.BackgroundColor3 = Color3.fromRGB(35,35,35)
	b.TextColor3 = Color3.new(1,1,1)
	b.Font = Enum.Font.Gotham
	Instance.new("UICorner", b)

	b.MouseEnter:Connect(function()
		TweenService:Create(b, TweenInfo.new(0.2), {
			BackgroundColor3 = Color3.fromRGB(0,170,255)
		}):Play()
	end)

	b.MouseLeave:Connect(function()
		TweenService:Create(b, TweenInfo.new(0.2), {
			BackgroundColor3 = Color3.fromRGB(35,35,35)
		}):Play()
	end)

	return b
end

-- ===== FUNCIONES =====

-- FLY
local flyBtn = createButton("Fly OFF", 70)
local flying = false
local flyConn

flyBtn.MouseButton1Click:Connect(function()
	flying = not flying
	flyBtn.Text = flying and "Fly ON" or "Fly OFF"

	if flying then
		flyConn = RunService.RenderStepped:Connect(function()
			if root then
				root.Velocity = workspace.CurrentCamera.CFrame.LookVector * 60
			end
		end)
	else
		if flyConn then flyConn:Disconnect() end
	end
end)

-- SPEED
local speed = 16
local speedBtn = createButton("Speed: 16", 120)

speedBtn.MouseButton1Click:Connect(function()
	speed += 10
	if speed > 200 then speed = 16 end
	humanoid.WalkSpeed = speed
	speedBtn.Text = "Speed: "..speed
end)

-- JUMP
local jump = 7
local jumpBtn = createButton("Jump: 7", 170)

jumpBtn.MouseButton1Click:Connect(function()
	jump += 5
	if jump > 40 then jump = 7 end
	humanoid.JumpPower = jump
	jumpBtn.Text = "Jump: "..jump
end)

-- DASH
local dashBtn = createButton("Dash 💨", 220)
dashBtn.MouseButton1Click:Connect(function()
	if root then
		root.Velocity = workspace.CurrentCamera.CFrame.LookVector * 120
	end
end)

-- NOCLIP
local noclipBtn = createButton("Noclip OFF", 270)
local noclip = false
local noclipConn

noclipBtn.MouseButton1Click:Connect(function()
	noclip = not noclip
	noclipBtn.Text = noclip and "Noclip ON" or "Noclip OFF"

	if noclip then
		noclipConn = RunService.Stepped:Connect(function()
			if char then
				for _,v in pairs(char:GetDescendants()) do
					if v:IsA("BasePart") then
						v.CanCollide = false
					end
				end
			end
		end)
	else
		if noclipConn then noclipConn:Disconnect() end
	end
end)

-- KEY
check.MouseButton1Click:Connect(function()
	if input.Text == KEY then
		keyFrame:Destroy()
		toggle.Visible = true
		hub.Visible = true
	else
		floatingText("❌ Wrong Key")
	end
end)
