sethiddenproperty(game.Players.LocalPlayer,"MaximumSimulationRadius",math.huge)
sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",1.0000000331814e+32)

for i,v in next, game:GetService("Players").LocalPlayer.Character:GetDescendants() do
if v:IsA("BasePart") and v.Name ~="HumanoidRootPart" then 
game:GetService("RunService").Heartbeat:connect(function()
v.Velocity = Vector3.new(0,-25.05,0)
wait(0.5)
end)
end
end

local Fling = true --// Recommended: true
local FlingBlockInvisible = false --// Recommended: false (So you can see the flinging block)
local HighlightFlingBlock = false --// Recommended: true
local FlingHighlightColor = Color3.fromRGB(30,30,30)
 
-- // Uses Mizt's bypass \\ --
 
Bypass = "death"
loadstring(game:GetObjects("rbxassetid://5325226148")[1].Source)()

e = Instance.new("BodyVelocity",game.Players.LocalPlayer.Character.HumanoidRootPart)
e.Velocity = Vector3.new(0,-25.05,0)
e.P = math.huge
--e.MaxForce = Vector3.new(0,3000,0)
 
local IsDead = false
local StateMover = true
 
local playerss = workspace.non
local bbv,bullet
if Bypass == "death" then
	bullet = game.Players.LocalPlayer.Character["HumanoidRootPart"]
	bullet.Transparency = (FlingBlockInvisible ~= true and 0 or 1)
	bullet.Massless = true
	if bullet:FindFirstChildOfClass("Attachment") then
		for _,v in pairs(bullet:GetChildren()) do
			if v:IsA("Attachment") then
				v:Destroy()
			end
		end
	end
 
	bbv = Instance.new("BodyPosition",bullet)
    bbv.Position = playerss.Torso.Position
end
 
if Bypass == "death" then
coroutine.wrap(function()
	while true do
		if not playerss or not playerss:FindFirstChildOfClass("Humanoid") or playerss:FindFirstChildOfClass("Humanoid").Health <= 0 then IsDead = true; return end
		if StateMover then
			bbv.Position = playerss.Torso.Position
    		bullet.Position = playerss.Torso.Position
		end
		game:GetService("RunService").RenderStepped:wait()
	end
end)()
end

if HighlightFlingBlock ~= false then
    local Highlight = Instance.new("SelectionBox")
    Highlight.Adornee = bullet
    Highlight.Color3 = (typeof(FlingHighlightColor)=="Color3" and FlingHighlightColor) or (Color3.fromRGB(255,0,0))
    Highlight.Parent = bullet
    Highlight.Name = "HighlightBox"
end
 
bbav = Instance.new("BodyAngularVelocity",bullet)
    bbav.MaxTorque = Vector3.new(math.huge,math.huge,math.huge)
    bbav.P = 100000000000000000000000000000
    bbav.AngularVelocity = Vector3.new(10000000000000000000000000000000,100000000000000000000000000,100000000000000000)

local Player=game.Players.LocalPlayer local Character=workspace.non local hum = Character.Humanoid local LeftArm=Character["Left Arm"] local LeftLeg=Character["Left Leg"] local RightArm=Character["Right Arm"] local RightLeg=Character["Right Leg"] local Root=Character["HumanoidRootPart"] local Head=Character["Head"] local Torso=Character["Torso"] local Neck=Torso["Neck"] local mouse = Player:GetMouse() local position = nil local sine = 0 local t = 0 local change = 1

local HEADLERP = Instance.new("ManualWeld")
HEADLERP.Parent = Head
HEADLERP.Part0 = Head
HEADLERP.Part1 = Head
HEADLERP.C0 = CFrame.new(0, -1.5, -0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
 
local TORSOLERP = Instance.new("ManualWeld")
TORSOLERP.Parent = Root
TORSOLERP.Part0 = Torso
TORSOLERP.C0 = CFrame.new(0, 0, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
 
local ROOTLERP = Instance.new("ManualWeld")
ROOTLERP.Parent = Root
ROOTLERP.Part0 = Root
ROOTLERP.Part1 = Torso
ROOTLERP.C0 = CFrame.new(0, 0, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
 
local RIGHTARMLERP = Instance.new("ManualWeld")
RIGHTARMLERP.Parent = RightArm
RIGHTARMLERP.Part0 = RightArm
RIGHTARMLERP.Part1 = Torso
RIGHTARMLERP.C0 = CFrame.new(-1.5, 0, -0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
 
local LEFTARMLERP = Instance.new("ManualWeld")
LEFTARMLERP.Parent = LeftArm
LEFTARMLERP.Part0 = LeftArm
LEFTARMLERP.Part1 = Torso
LEFTARMLERP.C0 = CFrame.new(1.5, 0, -0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
 
local RIGHTLEGLERP = Instance.new("ManualWeld")
RIGHTLEGLERP.Parent = RightLeg
RIGHTLEGLERP.Part0 = RightLeg
RIGHTLEGLERP.Part1 = Torso
RIGHTLEGLERP.C0 = CFrame.new(-0.5, 2, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
 
local LEFTLEGLERP = Instance.new("ManualWeld")
LEFTLEGLERP.Parent = LeftLeg
LEFTLEGLERP.Part0 = LeftLeg
LEFTLEGLERP.Part1 = Torso
LEFTLEGLERP.C0 = CFrame.new(0.5, 2, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))

function swait(num)
	if num == 0 or num == nil then
		game:service("RunService").Stepped:wait(0)
	else
		for i = 0, num do
			game:service("RunService").Stepped:wait(0)
		end
	end
end

coroutine.wrap(function() -------Checks
while true do
if Root.Velocity.y > 1 then
position = "jump"
elseif Root.Velocity.y < -1 then
position = "fall"
elseif Root.Velocity.Magnitude < 2 then
position = "idle"
elseif Root.Velocity.Magnitude < 20 then
position = "walk"
elseif Root.Velocity.Magnitude > 20 then
position = "run"
end
wait()
end
end)()

coroutine.wrap(function()
while true do
sine = sine + change
if position == "idle" then
change = 1
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 1 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12))),0.1)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.5 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 3 * math.sin(sine/12))),0.1)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.5 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + -3 * math.sin(sine/12))),0.1)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.5 + 0 * math.sin(sine/12), 2 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12))),0.1)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.5 + 0 * math.sin(sine/12), 2 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(3 + 0 * math.sin(sine/12))),0.1)
elseif position == "walk" then
change = 1
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 1 * math.sin(sine/12)), math.rad(0 + 3 * math.sin(sine/12))),0.1)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.5 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(0 + 0 * math.sin(sine/12)), math.rad(13 + 0 * math.sin(sine/12)), math.rad(0 + 10 * math.sin(sine/12))),0.1)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.5 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(0 + 0 * math.sin(sine/12)), math.rad(-13 + 0 * math.sin(sine/12)), math.rad(0 + -10 * math.sin(sine/12))),0.1)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.5 + 0 * math.sin(sine/12), 2 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(-24 + -17 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12))),0.1)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.5 + 0 * math.sin(sine/12), 2 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(25 + 17 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12))),0.1)
elseif position == "run" then
change = 1
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(-41 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12))),0.1)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.5 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(52 + 21 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12))),0.1)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.5 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(52 + -27 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12))),0.1)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.5 + 0 * math.sin(sine/12), 2 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(-1 + 39 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12))),0.1)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.5 + 0 * math.sin(sine/12), 2 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(-36 + -32 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12))),0.1)
elseif position == "jump" then
change = 1
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0 + 0 * math.sin(sine/12), 9 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 1 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12))),0.1)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.5 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 3 * math.sin(sine/12))),0.1)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.5 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12), 0 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + -3 * math.sin(sine/12))),0.1)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.5 + 0 * math.sin(sine/12), 1 + 0 * math.sin(sine/12), -1 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(-94 + 3 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12))),0.1)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.5 + 0 * math.sin(sine/12), 1 + 0 * math.sin(sine/12), -1 + 0 * math.sin(sine/12)) * CFrame.Angles(math.rad(-94 + -4 * math.sin(sine/12)), math.rad(0 + 0 * math.sin(sine/12)), math.rad(3 + 0 * math.sin(sine/12))),0.1)
elseif position == "fall" then
--clerp here
end
swait()
end
end)()
--Converted using Xen Imator
