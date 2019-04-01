# Intro to Unity and Uploading Avatars

Originally posted By akalink on 15 September 2018 [here](http://vrchat.wikidot.com/tutorial:avatars:unity-upload-tutorial)

1. [Setting up Unity]()
2. [Importing Avatars]()
3. [Setting up Avatars for Upload]()
4. [Texture and Shaders]()
5. [Uploading your Avatar]()

## 1. Setting up Unity

The necessary version of unity and the VR Chat Unity SDK can be downloaded by logging into <https://www.vrchat.com> and proceeding to the download page. <https://www.vrchat.com/home/download>

During the Unity instal you will need to create a Unity account. The personal version of Unity is sufficient for creating content on VR Chat.

![Importing a custom package](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/Import%20pakage.png)

You will need to import the VR Chat SDK. Go to the assets option in the main menu -> import package -> custom package. Find and select the VR Chat SDK. After the package finishes uncompressing, a prompt will appear, click Import.

Before proceeding, you need to log in. Go to the newly added VRChat SDK option in the main menu -> settings. A new window will appear prompting you to log into you VR Chat account. Once logged in the window will also display if you are allowed to upload avatars.

![Opening the VRchat settings menu](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/User%20setting%20window.png)

## 2. Importing Avatars

In this tutorial we will be using Unity-Chan as our tutorial avatar. The goal of this tutorial in addition to learning how to navigate unity is to also teach you how to troubleshoot when things break. That being said, the de facto tool for preparing models before import to unity is blender with the cats blender plugin and mmd tools plugin. This will be covered in the intermediate guides.

VR Chat requires all avatars have less than **70,000 polygons**. If your avatar has more than 70,000 polys you will need to decimate it down to a lower poly count. You can check the number of polygons by importing the model into blender.


u can find Unity-Chan as a free asset on the Unity Asset store. Click on the Asset store tab above the scene window (center window). You will have to be logged into your Unity account to download assets from the asset store. You can find the Unity-Chan asset here: <https://assetstore.unity.com/packages/3d/characters/unity-chan-model-18705>

![Import the model into your project](http://vrchat.wdfiles.com/local--resized-images/tutorial:avatars:unity-upload-tutorial/Asset%20store%20image.jpg/medium.jpg)

Non-asset store models can easily be added by being drag & dropped into to Project (bottom) tab into the list of assets. FBX is the prefered model format, though other formats can also work. When importing models be sure to include the models texture files, these will be image files of varying formats, with the FBX.

![Drag and drop non-asset store models into Project](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/Project%20drag%20and%20drop%20here.jpg)

## 3. Setting up Avatars for Upload

With our avatar successfully imported as a unity asset, we will now add it to your Unity Scene.

Drag the FBX file from the Project (bottom) tab into the Scene (middle) or Hierarchy (left) tab. It is recommended to set the avatars position to zero, though it is not necessary. To do this: click on the avatar in the Hierarchy, this will bring up the models components in the Inspector (right) tab. Find the Transform component. The Transform component dictates an objects position, rotation, and size. You can manually type the values into the component. You are also able to do this in the Scene window to alter these values visually. You can always adjust your view in the Scene tab with the mouse scroll wheel, center and right mouse buttons.

![View the assets in your models folder](http://vrchat.wdfiles.com/local--resized-images/tutorial:avatars:unity-upload-tutorial/asset%20destination.jpg/medium.jpg)

If your avatar is Purple/Pink after you have added it to the scene, this is a shader issue. If it is clear or white it is missing its texture. Shaders and Textures will be covered in part 4.

Next we will need to set the model up as a humanoid rig. Models that are not set up as a humanoid rig will slide around in game in their default T or A pose.

To do this we will need to click the model in the Hierarchy tab. Unity uses a parent-child system for all game objects, clicking on the grey arrow next to a object in the hierarchy will display its child objects. Child objects can have child objects of their own. Be sure to click on the highest level parent of the model. Details of the model will appear in the inspector tab. Near the top of the inspector window will be a button called Select, click on the Select button. Three new buttons will appear in the inspector window; Model, Rig, and Animation. Click on the Rig button. Then change the Animation Type to Humanoid, then click Configure. Unity will ask you to save your scene. Save your scene because all software used for creative purposes is infamous for it propensity to crash.

![Change animation type to Humanoid](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/Set%20up%20rig%201.jpg)

You should be brought to the Bone Mapping window in the Inspector tab.

Unity is very good at automatically and correctly assigning the bones for a humanoid rig. You can test if the model is setup correctly by enforcing T-Pose at the bottom menu in the Inspector tab. If the model becomes disfigured check the bone assignments. If the assignments appear correct then you may need to fix the model in a modeling software and re import the model. This is usually caused by incorrect bone merging in the modeling process.

![Enforce T-pose, check the bones](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/set%20up%20rig%202.jpg)

Two common errors to look out for are: Assigning a eye bone to the jaw bone and not assigning purposely unweighted bones. The first problem can easily be fixed by clearing the jaw bone assignment. The second will require manual bone assignment. When in the bone mapping window, the entire parent-child bone system will be unwrapped in the Hierarchy tab. You can drag and drop bones from the Hierarchy tab into the bone mapping window.

![Map bones onto the hands](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/set%20up%20rig%203.jpg)

When you have finished apply your bone mapping and click done.

The next step is to add the VRC_Avatar_Descriptor component.

Click on the Avatar in the Hierarchy tab to select it. Go to the Inspector tab, click the Add Component Button. You can find the component manually, or you can use the search function to find it easier. Click on the component you want to add to add it.

![Add component, search for VRC_Avatar_Descriptor](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/add%20avatar%20component.jpg)

It is at this point if you wish to make your avatar smaller or larger using the Transform component and haven’t done so yet, you may want to do it now.

You should now see a grey ball in the Scene tab. If you do not see it, it may be obstructed by your avatar. This ball is your view position in game. The newly added Avatar Descriptor component contains the coordinates for the view position. Adjust the position of the ball until it is between the eyes. Do not worry if it is slightly behind the bridge of the nose or behind hair this it is in the models face The mesh very close to the view position is not rendered and will not affect your view. When making a giant avatar this may break.

![Tiny ball is your view position in game](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/Viewer%20set%20up.jpg)

Setting your avatar as male or female is up to personal preference. Male avatars sit with their legs apart, female with their legs crossed.

Custom Animations will be covered in intermediate tutorials.

Lip sync is used to set up mouth movements. It is not necessary to upload a avatar. If you wish to test out your new avatar, feel free to upload it, it can always be overwritten or deleted.

Lets next set up the avatars mouth movements. There are two ways to do it. The first is with a jaw bone. The second is with Blend Shapes. Blend shapes are animations built into the avatar’s mesh. They generally serve single purpose poses that would be difficult with the use of bones.

There are two options for using Blend Shapes, Jaw Flap and Viseme. Jaw Flap is if you have one Blend Shape for mouth flaps, Viseme is if you have more than one.

For our Unity-Chan avatar we will use the Jaw Flap Blend Shape option. We will then need to drag the face mesh (the mesh that contains the blend shape) from the Hierarchy into the face mesh slot.

Let’s look in the Project tab to find the name of the face Mesh. For Unity-Chan the name of the face mesh is MTH_DEF.

![This is the face mesh for Unity-Chan](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/Visime%20mesh%20location.jpg)

Normally every mesh will be the first child of the main parent object in the Hierarchy. Unity-Chan is strange as the face mesh is for some reason the child of the head bone. Click through the grey arrows until you find the MTH_DEF object. Click on the Avatars highest parent again to bring the Avatar Descriptor component visible again. Drag MTH_DEF into the Face Mesh slot.

![Click through grey arrows, drag MTH_DEF into Face Mesh](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/mth%20in%20hierarchy.jpg)

The last step is to select the mouth movement shape. For Unity-Chan it is blendshape1.MTH_SAP.

For other avatars the mouth blend shape you are most likely to see are: aaa, ah, or あ..

## 4. Texture and Shaders

Textures and Shaders are a pretty important part of VR Chat. Textures are images projected onto 3d models. Shaders are the code that determine how the mesh looks in game. Not all shaders work in VR Chat, and just because the shader looks good in unity doesn’t mean it will look good in VR Chat.

If you have already uploaded your Unity-Chan avatar, you may have noticed that she is completely black in game. The shader that comes with the Unity-Chan asset doesn’t work in VR Chat, we are going to have to replace it.

Let’s download [Cubed Unity Shaders](https://github.com/cubedparadox/Cubeds-Unity-Shaders). This shader is a toon shader, so any anime or cartoon characters will look pretty nice with it. You can download the shader from their github page. Once download you can drag and drop the extracted zip file right into unity.

n alternative shader is [Xiexe's Toon Shader](https://vrcat.club/threads/xiexes-toon-shader-v1-4-updated-9-6-2018-xstoon-the-user-experience-update.1878/). This shader is harder to use, but it offers a more robust and more efficient toon shader option.

Once the files are in Unity you click on the mesh in the hierarchy to bring up its components in the inspector. You can also find the material files the material folder in the project window, click on it there will achieve the same results. In the inspector you should see the material component. There is a drop down menu where you can select the shader. Pick cubed paradox -> Flat Toon lit.

![Add shader to material](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/changing%20shader.png)

The shader will give you options. Every shader is different, but a few options you may have is option to change the albedo color, reflection, outline, emission (light source), tiling, and the materials texture. You can find the models textures in its project folder if you wish to browse and preview its shaders.

![Browse model textures to preview its shaders](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/materials.PNG)

Once you have all the materials changed to no longer be “Unity Chan”. Your avatar is ready to upload. Don’t worry if you avatar comes out with black portions, you can easily overwrite your previous avatar if you make a mistake.

![Testing your avatar locally](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/unity%20chan%20shaders.jpg)

## 5. Uploading your Avatar

If you haven’t done so already, add the VRC_Avatar_Descriptor, this was covered in part 3.

Click the VRChat SDK option in the main menu, then click Show Build Control Panel. A new window will appear, that will display all the avatars you can currently upload as well as some details of the avatars.

At this point, you will also be able to see if your [Avatar Performance Rank](https://docs.vrchat.com/docs/avatar-performance-ranking-system) is as desired. The [official Avatar Optimizing Tips page](https://docs.vrchat.com/docs/avatar-optimizing-tips) from the VRChat docs is a worthy read. A well-optimized model will likely show as Very Good or Excellent. To reduce material or skinned mesh count, you will need to perform additional optimization (removing materials). The best and easiest way to do this is to open your model in Blender and perform atlasing using the CATS plugin or Shotariya's material combiner plugin. This process will be described in another wiki tutorial.

![VRChat SDK option > Show Build Control Panel](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/Upload.png)

Click the Build and Publish button to begin the upload process. Once the first part of the uploading process is finished, the scene tab will change to play mode, and a form will appear in that window. Sometimes the play button is stuck in pause mode, click the pause button to fix this problem.

If you want to change the preview image for you avatar, switch back to scene tab without going out of play mode. You can move the camera to where you want it to be. When you are all ready, click the upload button.

![Create a preview image by positioning camera](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/move%20camera.PNG)

Optional:

Clean up: When you are finished with you avatar and don’t want to delete it from your hierarchy, un-check the avatar in the inspector. Another way to do this is to right click a open space in the hierarchy, click create empty. Un-check this new object, place your avatar on this new object in the hierarchy. This will make it a child of the inactive gameobject.

![Uncheck this](http://vrchat.wdfiles.com/local--files/tutorial:avatars:unity-upload-tutorial/uncheck.png)
