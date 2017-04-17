# Setting up the project
1. Download or clone the repository onto your computer.
2. Open the project with Unity **5.4.0f3**.
![](http://image.prntscr.com/image/946e3916682d45e88b5eba23be8c1ec7.png)
3. Click `Nuterra > Build AssetBundles` to verify the assetbundles can be succesfully build.
![](http://image.prntscr.com/image/80f7097092ac4c2aa5c1f7150aa4ddb8.png)

# Creating your own block
[Album of gifs](http://imgur.com/a/HE0ab)

## Setting up the scene
1. Add a cube to the scene (`3D Object > Cube`).
2. Set the position of the cube to `(0, -1, 0)`
3. Add an empty GameObject to the scene (this will be referred to as your root object).
4. Set the position of the root object to `(0, 0, 0)`
![](http://imgur.com/sJfz142.gif)

## Adding your model
In order to add a model to your block, the model should already be imported into the Unity Editor.

1. Drag the model onto the root object, so it will be put inside of it.
2. Change the scale, position and rotation of the model to be correct for the block
3. Add colliders (note: if you want to use mesh colliders, they must be convex!)
![](http://imgur.com/Gqh7WTg.gif)

## Setting the information of your model

1. Add the following script to the root object: `Scripts > Nuterra.Editor > Custom Block Prefab`
2. Setup the information to your liking.
3. Make sure the BlockID is unique, otherwise Nuterra will throw an error during startup.
4. Make sure the dimensions of your block are at least 1 in each direction.
![Setup basic info](http://imgur.com/oxGXgbN.gif)
![Create simple icon](http://imgur.com/ruTHKVy.gif)

## Setting up your blockpack as asssetbundle
1. Create a folder for your blockpack, it must exist under `/Blocks`, example: `/Blocks/MyFirstPack`
2. Set the asset bundle of your blockpack folder with a name, it is handy to put all your assets in this folder so they all get serialized
3. Drag the root object into your blockpack folder to save the prefab
To save future edits on your custom block, you need to use the `Apply` button on the root object.
![Create assets folder](http://imgur.com/dg0C6KO.gif)

# Installing your blockpack
BlockPacks are put in the `/GeneratedAssetBundles` folder of the Unity project.
To install these, put them in `TerraTech/Nuterra_Data/BlockPacks/`

You can use the following script to make copying the required files easier:

### /GeneratedAssetBundles/copy-to-nuterra.bat
```batch
@echo off
set TT_ROOT=D:\Program Files (x86)\Steam\steamapps\common\TerraTech Beta
set PACK_NAME=myfirstpack

set TT_BLOCKS=%TT_ROOT%\Nuterra_Data\BlockPacks
if not exist "%TT_BLOCKS%" mkdir "%TT_BLOCKS%"
copy /Y %PACK_NAME% "%TT_BLOCKS%\%PACK_NAME%"
copy /Y %PACK_NAME%.manifest "%TT_BLOCKS%\%PACK_NAME%.manifest"
pause
```
