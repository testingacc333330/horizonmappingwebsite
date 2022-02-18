> This is the fixed version of the API code on Horizons

```lua
--[[

/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
/ / / / /																																							  / / / / 
/ / / / /														dont touch anything in here please											  / / / / 
/ / / / /							the engine uses it for communication between level sequencing							  / / / / 
/ / / / /						also it handles every function in the sequencing and handles variables					  / / / / 
/ / / / /													so no touchy or entire game break!!!!!!!!!!!										  / / / / 
/ / / / /																																							  / / / / 
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 

]]--

--[[

/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \

]]--

--[[

/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
/ / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / / 
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \

]]--

local l__PlayerGui__1 = game.Players.LocalPlayer.PlayerGui
local l__axle__2 = game.SoundService.Voice.axle;
local v1 = require(l__PlayerGui__1.Subtitles.SubtitleModule);
local l__PortalA__3 = workspace.Portals.PortalA;
local l__PortalB__4 = workspace.Portals.PortalB;
local l__HumanoidRootPart__1 = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart");
local v24 = require(l__PlayerGui__1.Subtitles.SubtitleModule);
local u1 = {}

return {
	function(Factor : Number)
		l__PlayerGui__1.ShakeOffset.Value += Factor;
	end,
	function(AudioId : Number, p95, p96, p97,tl,dowait,added)
		if string.len(AudioId) ~= 0 then
			l__axle__2.SoundId = "rbxassetid://" .. AudioId;
			l__axle__2.Volume = p95;
		end
		if not l__axle__2.IsLoaded then
			while true do
				if (not l__axle__2.IsLoaded) or (l__axle__2.SoundId ~= "rbxassetid://"..AudioId) then
					task.wait(1/60)
				else
					break;
				end;		
			end;
		end;
		tl = tl or l__axle__2.TimeLength
		if (not l__PlayerGui__1.axleDisabled.Value) or (p97 == true) then
			l__axle__2:Play();
			v1.AddSubtitle("Axle: " .. p96, tl + (added or 3), "axle");
			if dowait then
				wait(tl)
			end
			if p97 then
			else
				return;
			end;
		else
			if dowait then
				wait(tl)
			end
			return;
		end;
	end,
	function()
		local v394 = require(game.ReplicatedStorage.PortalPlacement);
		local v395 = false;
		if l__PortalA__3.CanBeClosed.Value then
			if l__PortalA__3.Active.Value then
				v395 = true;
				v394.closePortal(l__PortalA__3, false, game.Players.LocalPlayer);
			end;
		end;
		if l__PortalB__4.CanBeClosed.Value then
			if l__PortalB__4.Active.Value then
				v395 = true;
				v394.closePortal(l__PortalB__4, false, game.Players.LocalPlayer__7);
			end;
		end;
		if v395 then
			l__PlayerGui__1.Crosshair.Crosshair.Image = "rbxassetid://4657739256";
			l__PlayerGui__1.clearPortals.Value = true;
		end;
	end,
	function(Trigger : Instance)
		local u138 = false;
		local u139 = #u1 + 1;
		u1[u139] = Trigger.Touched:Connect(function(p127)
			if p127 == l__HumanoidRootPart__1 then
				u138 = true;
				u1[u139]:Disconnect();
			end;
		end);
		while true do
			wait();
			if u138 ~= true then

			else
				break;
			end;	
		end;
	end,
	l__HumanoidRootPart__1,
	function()
		l__HumanoidRootPart__1.Parent.Humanoid:TakeDamage(99999999999999999999999)
	end,
	function(Value : Bool)
		l__PlayerGui__1.hasPortalGun.Value = Value
	end,
	function(Value : Number)
		l__PlayerGui__1.PortalLevel.Value = Value
	end,
	function(Value : Number)
		l__PlayerGui__1.axleKeyframePhase.Value = Value
	end,
	function(ExpressionName : String)
		l__PlayerGui__1.AxleAnimator.SetExpression:Fire(ExpressionName);
	end,
	function(SubtitleText : String,TimeLength : Number,Preset : String)
		v24.AddSubtitle(SubtitleText, TimeLength, Preset or "announcer");
	end,
	function(LevelName : String)
		if LevelName ~= nil then
			if string.find(LevelName,"import:_") then
				local id = tonumber(string.sub(LevelName,9))
				workspace.LevelImportTest.UnpackLevel:FireServer(id)
				local l__LocalPlayer__1 = game.Players.LocalPlayer;
				local levelname = game.ReplicatedStorage.LevelUnpacked.OnClientEvent:Wait()
				for _,i in ipairs(workspace.Unpacked_SpawnLocations:GetChildren()) do
					i.Parent = game.ReplicatedStorage.SpawnLocations
				end
				l__LocalPlayer__1.PlayerGui.Fade.FadeSolid.Value = true;
				l__LocalPlayer__1.PlayerGui.Fade.FadeTime.Value = 10;
				wait(0.2);
				l__LocalPlayer__1.PlayerGui.CurrentLevel.Value = levelname
				l__LocalPlayer__1.Character.HumanoidRootPart.CFrame = CFrame.new(0, -200, 0);
				wait();
				while true do
					wait();
					if l__LocalPlayer__1.PlayerGui.levelLoaded.Value then
						break;
					end;				
				end;
				if not LevelName ~= "chp1_sp_00" then
					l__LocalPlayer__1.PlayerGui.Fade.FadeSolid.Value = false;
					l__LocalPlayer__1.PlayerGui.Fade.FadeTime.Value = 8;
				end
			else
				local l__LocalPlayer__1 = game.Players.LocalPlayer;
				if game.ReplicatedStorage.Levels:FindFirstChild(LevelName) and LevelName ~= "intro" then
					l__LocalPlayer__1.PlayerGui.Fade.FadeSolid.Value = true;
					l__LocalPlayer__1.PlayerGui.Fade.FadeTime.Value = 10;
					wait(0.2);
					l__LocalPlayer__1.PlayerGui.CurrentLevel.Value = LevelName;
					l__LocalPlayer__1.Character.HumanoidRootPart.CFrame = CFrame.new(0, -200, 0);
					wait();
					while true do
						wait();
						if l__LocalPlayer__1.PlayerGui.levelLoaded.Value then
							break;
						end;				
					end;
					if not LevelName ~= "chp1_sp_00" then
						l__LocalPlayer__1.PlayerGui.Fade.FadeSolid.Value = false;
						l__LocalPlayer__1.PlayerGui.Fade.FadeTime.Value = 8;
					end
				end;
			end
		end;
	end
}
```
