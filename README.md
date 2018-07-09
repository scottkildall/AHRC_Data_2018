# AHRC_Data_2018


## Overview

###Model Import into Unreal
Design 2D profile, 50% of it in Illustrator with a center-line axis. Export as an SVG. Do this on an 8.5" x 11" sheet

In Fusion 360, do a revolve to create a radially-symmetrical object. It is important to have a single body for the model

In a360, export as an FBX, check email for download and then download the FBX

User Blender to unwrap textures, steps are:

1.Launch Blender, press 'X' to delete the default cube
2. Import->FBX, choose the FBX file. You will probably have to zoom way in to view it
3. Grab diagonal hatch icon from upper-right to make 2 windows
4. Next to view on the 2nd window, choose UV Image Editor
5. right-click on mesh, press TAB to set to edit
6. Select the Shading/UVs tab
7. Under the UV Mapping drop-down menu, choose Smart UV Project. You should see a UV map that now fits into the texture map area
8. Export the FBX, add "_uv_mapped" to to the orignal filename
  
In Unreal, import the mesh

1. Go to Flag Meshs folder, click on the Import Button (not the Import into Level), Choose the "Import" button at the dialog,
2.FBX Import Options:

	set Uniform Scale to 100

2. Delete the old mesh, eg. "carbon_mesh" and do a Force Delete
3. Retitle the newly imported mesh, eg. "carbon_uv_mapped" -> "carbon_mesh"
4. Go to the flagscape_consolidated database, and choose Reimport.
5. Double-click on flagscape_consolidated and the mesh should be valid at this point

##Blueprint/Code model

###Flagsape_Data_Spawner
Has entry function **SpawnDataPrimbyName** which uses the **RowName**, which is the number of the row in the database.

Spawns a BPP_FS_DataPrim object
Then sets variables for BPP_FS_DataPrim:
	Country, FlagMaterial, IdName, Amount and then calls ActiveVariables()
	
	
###BPP_FS_DataPrim

SetDataEntries() function is weird, why is it there? I think we can delete it

ActivateVariables() function called by Flagscape_Data_Spawner


Has instance variables:
	idName = rowName (used for respawn later, I think)
	Country = country 
	Amount: this corresponds to the Value field
	FlagMaterial: the flag material, inside FLAG_MATERIALS

	
##Next to do
####Immigration database, can we add this?
####Clean code, expunge old remnanats and document code model better
####Scaling for population and other variables
####Flying controls to be improved, right always does nav, left to accelerate
####Pointer-data acquisition
