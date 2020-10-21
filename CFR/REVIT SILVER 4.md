Backgrounds, Links, and Title blocks - SILVER TRAINING - 4

# Linking

## Revit Model

To find your architectural links, go to Manage>Manage Links. Here you can see the name of your link and the path. Click reload if the link needs to be reset. 

To insert new link, Insert>Link Revit. Select origin to origin. Make sure the link is on the right workset. You want your architectural link on the architectural workset. MEP links should be under the "OTHER" workset. 

## CAD Background 

To insert a CAD Background, Insert>Link CAD. Find your .dwg drawing and then have the following settings: Colors Black and White, Layers All, Import Units Auto-Detect, Positioning Auto, Place at one level. The drawing will be placed into space on a random floor. 

To change what floor it is on, click the CAD and change Base Level to 02 FP (or whatever floor it is for).

To check that all your floors are good, View>Play Views>Floor Plan>02FP. Click query to see what existing layers are there. You can turn off certain layers there or under visibility. Turn off furniture, fixtures, etc. and make the entire layer half-tone. 

## Selecting

On the bottom right, you can turn off the ability to select links or pinned items.

# Title Block

TYPICALLY SET UP FOR YOU

To load a title block, go to Insert>Load Family.

Under the revision charts, you need to add TEXT boxes.

For scale, go to family type properties and turn off all the scales that is not yours.

Load in family to add stamp, that can be found under BIM 2018 Standards folder. If you use Jeff stamp, make sure to change the family type>other>Pete MD Seal to JEFF MD Seal. If you are adding it yourself, associate the visibility parameter to (create yourself;group parameter under visibility) JEFF STAMP parameter. 

Family Types>You might create many family types. One for ELEC PERMIT SET, NO STAMP, or MECH PERMIT SET. Delete the default type 

After you have fixed everything, click "Load into Project and Close". 

Find the sheet like M001 or E001 and select the title block. Change the type to one of the family types you made.

## For M201

Select all (shortcut is SA) to change all the types to teh same one 