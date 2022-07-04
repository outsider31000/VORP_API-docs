---
title: VORP INPUTS
author: outsider
date: 2022-05-08 14:10:00 +0800
categories: [Documentation Lua, INPUTS]
tags: [Lua]
render_with_liquid: false
---

### vorp inputs is a tool that is mandatory within the vorp framework. 

[`VORP INPUTS LUA`][inputs] **downlaod**

# **USAGE**
--------------------
--------------------

Can only be used in client side 


### ***single input***

```lua
local button = "Confirm"
local placeholder = "Text here"

    TriggerEvent("vorpinputs:getInput", button, placeholder, function(result)

        if result ~= "" or result then -- making sure its not empty
            print(result) -- returs a string
        else
            print("its empty?") -- notify
        end
    end)

```




### ***with input Type***

```lua
    local button = "Confirm"
    local placeholder = "Test Here"
    local inputType = "input" -- number ,textarea , date, etc.
    TriggerEvent("vorpinputs:getInput", button, placeholder,inputType, function(result)

        if result ~= "" or result then -- making sure its not empty
            print(result) -- returs the input type
        else
            print("its empty?") -- notify
        end
    end)
```

### ***advanced inputs***   `NEW`

```lua

local myInput = {
    type = "enableinput", -- don't touch
    inputType = "input", -- input type
    button = "confirm", -- button name
    placeholder = "insertamount", -- placeholder name
    style = "block", -- don't touch
    attributes = {
        inputHeader = "HEADER", -- header
        type = "text", -- inputype text, number,date,textarea 
        pattern = "[0-9]", --  only numbers "[0-9]" | for letters only "[A-Za-z]+" 
        title = "message", -- if input doesnt match show this message
        style = "border-radius: 10px; background-color: ; border:none;"-- style 
    }
}

TriggerEvent("vorpinputs:advancedInput", json.encode(myInput), function(result)
    
    if result ~= "" and result then
        print(result)
    else
        print("it's empty?")
    end
end)

```



-------
### ***devtips***

 **split a string into more than one**

 ```lua

local result = yourvariable
local splitString = {}
      for i in string.gmatch(result, "%S+") do
         splitString[#splitString + 1] = i
       end
local data1, data2 = splitString[1],splitString[2]

 ```

 ```lua 

 -- use can use these to make sure what you want the input to be.
 tostring(data1) -- returns a string
 tonumber(data2) -- returns a number

 ```
------

[inputs]:https://github.com/VORPCORE/vorp_inputs-lua


