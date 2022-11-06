v23.OnClientEvent("ChatDonationAlert"):Connect(function(p32, p33, p34, p35)
	local v138 = "";
	local v139 = Color3.fromRGB(255, 255, 255);
	local v140 = nil;
	if p35 == "global" then
		v138 = "[GLOBAL]: ";
	elseif p35 == "admin" then
		v139 = Color3.fromRGB(255, 100, 72);
	end;
	local v141 = v19.formatCommas(p34);
	print(v138 .. string.format("\240\159\146\176 %s tipped %s Robux to %s", p32, v141, p33));
	if p35 == "admin" then
		game.StarterGui:SetCore("ChatMakeSystemMessage", {
			Text = p34, 
			Color = v139, 
			Font = Enum.Font.GothamBold
		});
		return;
	end;
	if p34 >= 1000000 then
		v140 = "%s just gave %s ROBUX to %s!?!?";
		v139 = Color3.fromRGB(255, 0, 100);
	elseif p34 >= 100000 then
		v140 = "%s dropped a %s Robux nuke to %s!!!";
		v139 = Color3.fromRGB(255, 0, 230);
	elseif p34 >= 10000 then
		v140 = "%s dropped %s Robux to %s!!";
		v139 = Color3.fromRGB(0, 230, 255);
	elseif p34 >= 1000 then
		v140 = "%s donated %s Robux to %s!";
		v139 = Color3.fromRGB(255, 210, 0);
	elseif p34 >= 100 then
		v140 = "%s donated %s Robux to %s!";
		v139 = Color3.fromRGB(8, 255, 36);
	elseif p34 >= 1 then
		v140 = "%s tipped %s Robux to %s";
		v139 = Color3.fromRGB(8, 255, 36);
	end;
	game.StarterGui:SetCore("ChatMakeSystemMessage", {
		Text = v138 .. string.format(v140, p32, v141, p33), 
		Color = v139, 
		Font = Enum.Font.GothamBold
	});
end);
v23.OnClientEvent("GlobalDonationsDown"):Connect(function(p36)
	print("worked")
	if p36 then
		local v142 = "[GLOBAL] Global donations have been temporarily disabled, we will try to get them enabled ASAP.";
		local v143 = Color3.fromRGB(255, 111, 8);
	else
		v142 = "[GLOBAL] Global donations are back up!";
		v143 = Color3.fromRGB(6, 255, 131);
	end;
	game.StarterGui:SetCore("ChatMakeSystemMessage", {
		Text = v142, 
		Color = v143, 
		Font = Enum.Font.GothamBold
	});
end);
game.ReplicatedStorage.Notify.OnClientEvent:Connect(function(p37, p38, p39) -- donator reciever amount
	local v144 = v19.formatCommas(p39)
	if p37 == l__LocalPlayer__26 then
		l__SoundService__3.DonationSent:Play()
		u9(string.format("you donated %s to %s", v144, p38.Name), Color3.fromRGB(255, 255, 0))
	end
	if p38 == l__LocalPlayer__26 then
		l__SoundService__3.KaChing:Play();
		u9(string.format("%s DONATED %s TO YOU!", p37.DisplayName:upper(), v144), Color3.fromRGB(0, 255, 0))
	end
end)
