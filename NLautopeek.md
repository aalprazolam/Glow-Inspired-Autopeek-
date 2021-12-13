local autopeek_enable = Menu.SwitchColor("Visuals Extension", "Enable Autopeek",false,Color.new(1, 1, 1, 1), "Put your normal Neverlose autopeek alpha to 0 and turn on this autopeek.")

-- Skeet autopeek
local draw_autopeek = function()

    if autopeek_enable:Get() == true then
    if EntityList.GetLocalPlayer() == nil then return end
    if EntityList.GetLocalPlayer():GetProp("m_iHealth") <= 0 then return end

    if Menu.FindVar("Miscellaneous", "Main", "Movement", "Auto Peek"):Get() == false then
        apeekorigin = EntityList.GetLocalPlayer():GetProp('m_vecOrigin')
        return
    end


    for i = 1, 60 do 

        local apeekval = 1/i

        if i <= 60 then

            apeekval = apeekval + 1.5

        end

        apeekcolor = autopeek_enable:GetColor()

        apeekcolor.a = apeekval/50

        Render.Circle3DFilled(apeekorigin, 28, i / -2.5, apeekcolor)
        Render.Circle3DFilled(apeekorigin, 18, i / -2.6, apeekcolor)

    end
end
end
-- End

Cheat.RegisterCallback("draw", function()
    draw_autopeek()
end)
