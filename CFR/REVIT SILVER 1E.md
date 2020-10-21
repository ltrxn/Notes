Electrical Revit Basics - SILVER TRAINING - E1

# Setup

Work full should be the same as your electrical design process; Start with distribution and work your way down since in Revit, you can't circuit unless you have your panels set up.

Each piece of equipment needs to be set up with a proper voltage to work in Revit. To choose your settings go to Manage>MEP Settings>Electrical Settings>Distribution System.

Project Browser>Views>Electrical>Floor Plan>CFR Standards>Palette. This is for reference. You can find symbols and fixtures. Cover sheets under sheets has your sheets.

Project Browser>Views>Electrical>Floor Plan is where you can see everything in a project. 

Rename the working sheet as "Floor Plan: Existing drafting CELLAR" (replace cellar with the name of the floor). Under its property, change its sub-discipline to "Existing conditions" and Phase Filter to "Show Previous + Demo".

Make sure you are on the power workset. Workset settings bottom middle. Detailed view is bottom left looks like transparency grid.

# Laying things out

Phase should be "existing" when you lay out existing conditions. Then, individually change certain things to demo if they need to be demolished.

When you place these new elements in, make sure you change it's Phase to "Construction".

## Place Electrical Equipment 

Start with CFR_Panelboard. Add a tag (shortcut is TG) like "LP-1", then a 150V and 500V transformer. Tag it like "T1X". 

To set the distribution system: click on the panelboard and on the top there is a drop down for Distribution System and make it 208V/120V. For the Transformer, set the Distribution System and the Secondary Distribution System as 208/120

To connect the panelboard with the transformers, click on the panel board and select Power and under Panel chose a transformer (T1X)

## Place Electrical Fixtures

Everything else other than electrical equipment is an "electrical fixture/device" (shortcut is EF). Each receptacle has a load, and when the schedule is made it'll be calculated. Motors and VFDS have properties that work with smart schedule.

To move an electrical fixture to another wall. Select it and click Pick New.

To add a label to a electrical fixture, go to its type properties and scroll down the "Label". Go to electrical circuits tab (shortcut is EC) and name the Load Name something like "RECEPTS - ELECT ROOM"

### Circuiting

Select the fixture and then Power in the ribbon. Choose the Panel to be LP-1. 

To circuit two things on the same circuit, select both and then click Power.

Another way is to hover cursor over the fixture until its connector shows up. Click it and drag the homerun out. You can tag wires or the device itself. 

## Place Lighting Fixtures

Shortcut is LF. Chose "Place on Work Plane" and select the ceiling work plane (must be created)

To create a ceiling work plane: Go to view>Architectural>Building Elevation> Elevation: South. Make a new reference plane (shortcut is RP). Find the ceiling height and click it name it "cellar (or whatever the room is called) ceiling".

Place the light fixture. Power it. Tag it with type and then circuiting below it. Do edit circuit and under "Load Name" add unit information after so that it shows up on the panel, "LIGHTING - UNIT ABC". 

If you want to add extra fixtures to a certain circuit. Select the one that already is connected to the circuit you want and click edit circuit (shortcut is EC), and select all of them.  

## Place Lighting Device

Shortcut is LD. 

Place lighting work plane. Put switches and hubs in corridors.

## Place Fire Alarm Devices

Under Devices is Fire Alarm Devices. Choose the device and make sure your on the right layer. Offset ~8'. If you can't see it, make sure your view height covers it.

For fire alarms, you can turn off the coverage under Visibility>Wall Coverage Visible.

# Panel Schedules

Click on panel board>Create Panel Schedules>Use Default Template.

Feeder will look something like 2#12

"How to Input Metered Loads in Panels" is under Electrical Team Book of Knowledge>Revit 

## Individual schedules

Under Schedules there are things like "transformer schedules" where it just shows your transformers. When you name here, it affects the name on the sheet as well. KVA ratings may be wrong, but you can change things.

# Shortcuts and Speed ups

To **Tag All** that are similar, the shortcut is TA. Uncheck "Include elements from unlinked files". Select the Lighting fixture you put down, and it's going to tag all the fixtures.

If you wanted to power a lot of the same items on the same circuit, click one, select similar, and power and then choose panel.

Use the filter button to get rid of stuff you don't want.

