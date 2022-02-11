# What is an UI ?
UI are all the windows of the game. Like inventories, health panel, craft menu, ect.  
`x, y` are the position on the UI; `r, g, b` is the color in red, blue, green and `a` the transparency.  

# Make the handler
This is the base of a UI, it's gonna display a rectangle with "Hello world" write in it.  
```lua
require "ISUI/ISPanel" -- Or require "ISUI/ISPanelJoypad"

MyUI = ISPanel:derive("MyUI"); -- Or MyUI = ISPanelJoypad:derive("MyUI")

function MyUI:initialise()
    ISPanel.initialise(self); -- Or ISPanelJoypad.initialise(self);
    self:create();
end

function MyUI:prerender() -- Call before render, it's for harder stuff that need init, ect
    ISPanel.prerender(self); -- Or ISPanelJoypad.prerender(self);
    self:drawText("Hello world",0,0,1,1,1,1, UIFont.Small); -- You can put it in render() too
end

function MyUI:render() -- Use to render text and other
end

function MyUI:create() -- Use to make the elements
end

function MyUI:new(x, y, width, height)
    local o = {};
    o = ISPanel:new(x, y, width, height); -- Or o = ISPanelJoypad:new(x, y, width, height);
    setmetatable(o, self);
    self.__index = self;

    return o;
end
```

# How to display and remove my UI ?
To display and use a UI you need to create it. Once used, it must be destroyed or hide. I recommend destroying and rebuilding the UI each time because it's not more complicated on the code side and it avoids creating invisible copies of menus that stack  
To create:  
```lua
local myUI = MyUI:new(x, y, w, h);
myUI.parent = self; -- Optional but rly useful
myUI:initialise();
myUI:addToUIManager();
```
To destroy:  
```lua
myUI.parent.myUI = nil; -- If you use parent
myUI:setVisible(false);
myUI:removeFromUIManager();
```

# Useful function
```lua
getCore():getScreenWidth() -- Get the screen resolution
getCore():getScreenHeight() -- Get the screen resolution
getMouseX() -- Get position of the mouse on the screen
getMouseY() -- Get position of the mouse on the screen
isShiftKeyDown() -- True if the shift key is down
isCtrlKeyDown() -- True if the ctrl key is down
```

# How to add elements ?
The foundation of an UI is the elements that we put in it. They can be custom or already present in the game.  
They can be found in `media\lua\client\ISUI`  
Each time I specify the file because I strongly recommend going to see them to see the functions linked to each one. I can't list everything here.  

## Text
To display text use that in `prerender()` or `render()`:  
`self:drawText("Text", x, y, r, g, b, a, UIFont.Small)`  
To get the size of a text: `getTextManager():MeasureStringX(UIFont.Small, "Text)`

## Rectangle
There is two type of rectangle, the full and the border:  
`self:drawRectBorder(x, y, w, h, a, r, g, b)`  
`self:drawRect(x, y, w, h, a, r, g, b)`

## Button
Here is an example to add a button, file `ISButton.lua`  
You need to add that in `MyUI:create()`, like that:  
```lua
function MyUI:create()
    local btnWid = 75
    local btnHgt = getTextManager():getFontHeight(UIFont.Small) + 2 * 4

    self.button = ISButton:new(x, y, btnWid, btnHgt, "My button", self, MyUI.onOptionMouseDown);
    self.button.internal = "MYBUTTON";
    self.button:initialise();
    self.button:instantiate();
    self.button.borderColor = {r=0.7, g=0.7, b=0.7, a=0.5}; -- Optional
    self:addChild(self.button);
end
```
You also need to make `MyUI.onOptionMouseDown`, which is the function call when the button is pressed.  
Exemples with a button to close the UI:  
```lua
function MyUI:onOptionMouseDown(button, x, y)
    if button.internal == "MYBUTTON" then
        self:setVisible(false);
        self:removeFromUIManager();
    end
end
```

## Tick box
Here is an example to add a tick box, file `ISTickBox.lua`  
You need to add that in `MyUI:create()`, like that: 
```lua
function MyUI:create()
    self.tickBox = ISTickBox:new(100, 20, 10, 10, "", nil, nil);
    self.tickBox:initialise();
    self.tickBox:instantiate();
    self.tickBox.selected[1] = false; -- Start false or not
    self:addChild(self.tickBox);
    self.tickBox:addOption("This is my tick box:"); -- To add a text at the left of the box
end
```
After that, to check the value: `self.tickBox.selected[1]`

## Combo box
Here is an example to add a combo box, file `ISComboBox.lua`  
You need to add that in `MyUI:create()`, like that:  
```lua
function MyUI:create()
    self.comboBox = ISComboBox:new(x, y, w, h, self);
    self.comboBox:initialise();
    self.comboBox:instantiate();
    self:addChild(self.comboBox);

    local keys = {"One", "Two", "Three"}
    for key,value in pairs(keys) do
        self.comboBox:addOption(key);
    end
end
```
And after that to find the text selected: `self.comboBox:getSelectedText()`

## Entry text
Here is an example to add a entry text, file `ISTextEntryBox.lua`  
You need to add that in `MyUI:create()`, like that:  
```lua
function MyUI:create()
    self.textEntry = ISTextEntryBox:new("Start text", 25, 40, 150, btnHgt);
    self.textEntry:initialise();
    self.textEntry:instantiate();
    self:addChild(self.textEntry);
end
```
After that to find the text in it: `self.name:getInternalText()`

## Scrolling list
Here is an example to add a scrolling text box, file `ISScrollingListBox.lua`  
You need to add that in `MyUI:create()`, like that:  
```lua
function MyUI:create()
    self.scrollingList = ISScrollingListBox:new(x, y, w, h)
    self.scrollingList:initialise();
    self.scrollingList:instantiate();
    self.scrollingList.itemheight = 15;
    self.scrollingList.joypadParent = self;
    self.scrollingList.font = UIFont.Small;
    self.scrollingList:setOnMouseDownFunction(self, self.onClickItem);
    self.scrollingList.drawBorder = true;
    self:addChild(self.scrollingList);
end
```
To get the value selected: `self.scrollingList.selected`  
`self.onClickItem` is the function call when an item is select.  
Here an exemple:  
```lua
function MyUI:onClickItem()
    print(self.scrollingList.selected)
end
```

# Full example
### UI that open when press Y with a button to close it and some elements
```lua
require "ISUI/ISPanel"
local FONT_HGT_SMALL = getTextManager():getFontHeight(UIFont.Small)

MyUI = ISPanel:derive("MyUI");

function MyUI:initialise()
    ISPanel.initialise(self);
    self:create();
end

function MyUI:prerender()
    ISPanel.prerender(self);
    self:drawText("Hello !", 10 ,10, 1,1,1,1, UIFont.Small);
end

function MyUI:render()
end

function MyUI:create()
local btnWid = 75
    local btnHgt = FONT_HGT_SMALL + 2 * 4
    local padBottom = 10

    self.name = ISTextEntryBox:new("", 25, 60, 150, btnHgt);
    self.name:initialise();
    self.name:instantiate();
    self:addChild(self.name);

    self.cancel = ISButton:new(self:getWidth() - btnWid - 5, self:getHeight() - padBottom - btnHgt, btnWid, btnHgt, "Cancel", self, MyUI.onOptionMouseDown);
    self.cancel.internal = "CANCEL";
    self.cancel:initialise();
    self.cancel:instantiate();
    self.cancel.borderColor = self.buttonBorderColor;
    self:addChild(self.cancel);

    self.tick = ISTickBox:new(100, 5, 10, 10, "", nil, nil);
    self.tick:initialise();
    self.tick:instantiate();
    self.tick:setAnchorLeft(true);
    self.tick:setAnchorRight(false);
    self.tick:setAnchorTop(false);
    self.tick:setAnchorBottom(true);
    self.tick.selected[1] = true;
    self:addChild(self.tick);
    self.tick:addOption("Test tick box");
end

function MyUI:new(x, y, width, height)
    local o = {};
    o = ISPanel:new(x, y, width, height);
    setmetatable(o, self);
    self.__index = self;

    return o;
end

function MyUI:onOptionMouseDown(button, x, y)
    if button.internal == "CANCEL" then
    self:setVisible(false);
        self:removeFromUIManager();
    end
end

function MyUI:new()
    local o = {};
    x = getMouseX() + 10;
    y = getMouseY() + 10;
    o = ISPanel:new(x, y, 200, 120);
    setmetatable(o, self);
    self.__index = self;
    o.variableColor={r=0.9, g=0.55, b=0.1, a=1};
    o.borderColor = {r=0.4, g=0.4, b=0.4, a=1};
    o.backgroundColor = {r=0, g=0, b=0, a=1};
    o.buttonBorderColor = {r=0.7, g=0.7, b=0.7, a=0.5};
    o.zOffsetSmallFont = 25;
    o.moveWithMouse = false;

    return o;
end

function onCustomUIKeyPressed(key)
    if key == 21 then
        local myUI = MyUI:new()
        myUI:initialise();
        myUI:addToUIManager();
    end
end

Events.OnCustomUIKeyPressed.Add(onCustomUIKeyPressed)
