local Window = Rayfield:CreateWindow({
   Name = "PEDRINHUU HUB",
   Icon = 0, -- Icon in Topbar. Can use Lucide Icons (string) or Roblox Image (number). 0 to use no icon (default).
   LoadingTitle = "Loading...",
   LoadingSubtitle = "by PEDRINHUU SCRIPTS",
   ShowText = "PEDRINHUU SCRIPTS", -- for mobile users to unhide rayfield, change if you'd like
   Theme = "DarkBlue", -- Check https://docs.sirius.menu/rayfield/configuration/themes

   ToggleUIKeybind = "K", -- The keybind to toggle the UI visibility (string like "K" or Enum.KeyCode)

   DisableRayfieldPrompts = false,
   DisableBuildWarnings = false, -- Prevents Rayfield from warning when the script has a version mismatch with the interface

   ConfigurationSaving = {
      Enabled = true,
      FolderName = nil, -- Create a custom folder for your hub/game
      FileName = "PEDRINHUU HUB"
   },

   Discord = {
      Enabled = false, -- Prompt the user to join your Discord server if their executor supports it
      Invite = "noinvitelink", -- The Discord invite code, do not include discord.gg/. E.g. discord.gg/ ABCD would be ABCD
      RememberJoins = true -- Set this to false to make them join the discord every time they load it up
   },

   KeySystem = false, -- Set this to true to use our key system
   KeySettings = {
      Title = "Untitled",
      Subtitle = "Key System",
      Note = "No method of obtaining the key is provided", -- Use this to tell the user how to get a key
      FileName = "Key", -- It is recommended to use something unique as other scripts using Rayfield may overwrite your key file
      SaveKey = true, -- The user's key will be saved, but if you change the key, they will be unable to use your script
      GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like Rayfield to get the key from
      Key = {"Hello"} -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings ("hello","key22")
   }
})

local MainTab = Window:CreateTab("MainTab", 4483362458) -- Title, Image

Rayfield:Notify({
   Title = "PEDRINHUU HUB LOADED SUCCESSFULLY",
   Content = "Criado por: PEDRINHUU SCRIPTS!",
   Duration = 6.5,
   Image = 4483362458,
})

local InvisibleButton = MainTabTab:CreateButton({
    Name = "Invisibilidade",
    Callback = function()
        -- Função: Alternar visibilidade do jogador
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
        local humanoidRoot = character:WaitForChild("HumanoidRootPart")

        -- Variável para armazenar o estado de invisibilidade
        if not player:GetAttribute("Invisible") then
            player:SetAttribute("Invisible", false)
        end

        local isInvisible = player:GetAttribute("Invisible")

        if not isInvisible then
            -- Torna invisível
            for _, part in ipairs(character:GetDescendants()) do
                if part:IsA("BasePart") and part.Name ~= "HumanoidRootPart" then
                    part.Transparency = 1
                elseif part:IsA("Decal") or part:IsA("Texture") then
                    part.Transparency = 1
                end
            end
            player:SetAttribute("Invisible", true)
            print("👻 Jogador ficou invisível!")
        else
            -- Torna visível novamente
            for _, part in ipairs(character:GetDescendants()) do
                if part:IsA("BasePart") and part.Name ~= "HumanoidRootPart" then
                    part.Transparency = 0
                elseif part:IsA("Decal") or part:IsA("Texture") then
                    part.Transparency = 0
                end
            end
            player:SetAttribute("Invisible", false)
            print("😎 Jogador ficou visível novamente!")
        end
    end,
})
