cout
====

Lua mod for printing text and images to client screens in Natural Selection 2.

Simple how to use:

Create network hook on client:

Cout:createClientNetworkAction("askServerInfo", function (message) RBPS:sendServerInfo() end )

When client receives command "askServerInfo" from server it will do for example: RBPS:sendServerInfo() which sends info to server. "askServerInfo" can be anything you want. Notice that message is not used.

On server use (for same) (action part is meaningless here and can be anything you want):

local player = client:GetControllingPlayer() if player then Cout:SendMessageToClient(player, "askServerInfo",{action = "connect"}) end

Example to print text to client screens:

Cout:addServerTextMessageToAllClients(1/2,1/10,text,4,{r = 255, g = 230-(streak*10), b = 260-(streak*10) },"multikill")

first parameters are x,y. Its scaled value based on client screen, so 1/2 is middle. Third is color, fourth is duration in seconds that message is displayed, fifth is color and last is identifier: message can be updated if same identifier is used. So if that same message is spammed many times in row then it won't print many messages, only updates message with same "multikill" identifier.
