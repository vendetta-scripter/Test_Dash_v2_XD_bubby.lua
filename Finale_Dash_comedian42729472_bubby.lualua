-- LocalScript

local player = game.Players.LocalPlayer
local RunService = game:GetService("RunService")

-- GUI Setup
local screenGui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
screenGui.Name = "SideDashGui"
screenGui.ResetOnSpawn = false

local button = Instance.new("TextButton", screenGui)
button.Size = UDim2.new(0, 250, 0, 100)
button.Position = UDim2.new(0, 10, 0, 10)
button.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
button.BackgroundTransparency = 0.2
button.BorderSizePixel = 3
button.BorderColor3 = Color3.new(1, 1, 1)
button.Text = "Side Dash M1 - Made by bubby"
button.Font = Enum.Font.GothamBold
button.TextSize = 15
button.TextColor3 = Color3.new(1, 1, 1)
button.Active = true
button.Draggable = true

local humanoid, hrp, animTrack

-- Animation setup
local animation = Instance.new("Animation")
animation.AnimationId = "rbxassetid://10480793962"

-- Function to update references on character load
local function onCharacterAdded(character)
    humanoid = character:WaitForChild("Humanoid")
    hrp = character:WaitForChild("HumanoidRootPart")
    animTrack = humanoid:LoadAnimation(animation)
end

-- Connect to current or next character
if player.Character then
    onCharacterAdded(player.Character)
end
player.CharacterAdded:Connect(onCharacterAdded)

-- Dash function using BodyVelocity
local function dashRight()
    if not hrp or not animTrack then return end

    animTrack:Play()

    -- Create BodyVelocity for smooth, physics-respecting movement
    local bodyVelocity = Instance.new("BodyVelocity")
    bodyVelocity.Velocity = hrp.CFrame.RightVector * 73 -- Adjust speed here
    bodyVelocity.MaxForce = Vector3.new(1e5, 0, 1e5)
    bodyVelocity.P = 10000
    bodyVelocity.Parent = hrp

    -- Remove after short time
    game.Debris:AddItem(bodyVelocity, 0.27)
end

-- Button click event
button.MouseButton1Click:Connect(dashRight)
