# Basic World Creation

Original outline by CyanLaser posted here: <http://vrchat.wikidot.com/worlds:beginner>

## Prerequisites

- Have a VRChat account with upload privileges. <https://vrchat.com/register>
- Download and install [Unity 2017.4.15f1](https://unity3d.com/get-unity/download/archive) - Make sure you click on "2017.x", then find "2017.4.15
- Download the VRChat SDK: <http://vrchat.com/download/sdk>

### 1. Setup the Unity Project

Launch Unity and start a new Unity project by pressing 'New'. Give it a name and set the save location.

![Creating a new project in Unity](https://i.imgur.com/bnxJfi6.jpg)

Once Unity completes the project creation, you will see an empty scene. This scene is what will be uploaded to VRChat. First, save your new scene. If you have not done so already, spend some time getting used to the Unity interface.

Next, import the VRChat SDK by going to `Assets > Import Package > Custom Package...` on the top menu and navigating to where you downloaded the [VRChat SDK](http://vrchat.com/download/sdk) to.

![Importing the VRChat SDK into Unity](https://i.imgur.com/RO2cOZj.jpg)

Once the SDK has been imported, you will have a menu at the top for VRChat SDK. Click this and open the Settings pane then log in to your account here. *Note that you need to have a VRChat account to upload content and you cannot upload with your steam account.


### 2. Creating a Basic World

The world is currently empty. Lets add a surface for players to stand on. Right click on the hierarchy and create a new cube.

![Right click > 3D Object > Cube](https://i.imgur.com/6mTHY3C.jpg)

![Position it and scale it out](https://i.imgur.com/dvJfTp7.jpg)

Now that we have a place for players to stand on, they need a way to spawn into the world. In your project Assets folder, search for "VRCWorld" and drag this into the scene. This prefab will be the spawn point into your world and also hold other world related settings. See [VRC_SceneDescriptor]() for more information.

![Search VRCWorld and drag this into the scene](https://i.imgur.com/wxiLMaG.jpg)


### 3. Upload the World

At this point, you are in a good position to save the project and preview it. Go to `File > Save Scenes` and give it a name. Next, open `VRChat SDK > Show Build Control Panel`. You might see an error that says "Layers are not yet configured for VRChat".  VRChat allows for custom layers on objects that will give different collision interactions. We do not need to worry about the details of this now. 

Simply follow the instructions and setup whatever is throwing errors until you are allowed to click the buttons Last Build and New Build below. In order to preview your scene, click "New Build" underneath Test and save the file as something like Test1 if it pops up. VRChat should begin launching:

![Testing the world in VRchat](https://i.imgur.com/BTNMt8q.jpg)

This is all that is necessary for a world, now it is time to upload the world into VRChat. Open back up the "Show Build Control Panel" again and at the bottom click the "New Build" button under "Upload". Unity will take some time to compile the world and then display a UI for you to name your world and set the world preview. In the hierarchy, you will see a new object called "VRCCam". You can move this object around to change your preview image. 

![Go back to Scene and click VRCCam in Heirarchy to change preview](https://i.imgur.com/gabY6tV.jpg)

When you are ready, click back to the Game tab and accept the terms then click Upload. Your world will then be uploaded to VRChat and once it completes, you will be able to select it in your worlds menu. This world will be private but you can start friends+ instances of your new world. See Public world requests for when you are ready to make your world public: <https://docs.vrchat.com/docs/submitting-a-world-to-be-made-public>.

---

## Other Resources

- [VRChat Home Kit tutorial](https://docs.vrchat.com/docs/vrchat-home-kit) - Learn to customize your Home Kit in less than 1 hour
- Intro Unity tutorials
- Link to Unity terrain tutorial
