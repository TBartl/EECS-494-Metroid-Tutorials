## Project and Scene Setup

For any game you'll create in this class, the first thing you're going to need to do is **setup the project** with **version control** and setup your first **scene**. You may find it helpful to **come back to this page** on future projects as a reference.  

### Creating the Project

Open Unity and click the "New" button to create a new project.

![UnityStartup](./01/UnityStartup.PNG)

On the next screen give your project a name. It should follow the format **"eecs-494-p1-\<uniqname\>"** where \<uniqname\> is your uniqname.

Next select **2D** as Metroid is a 2D game.

{% include start-expand.html title="What's the difference between a 2D and a 3D game?" %} 
  <p>Regardless of which option you select, your game will still build and play the same.</p>
  <p>The difference between the two is that some settings will default to different things. With 2D set cameras default to orthograpic instead of perspective, images default to sprites instead of textures, and backgrounds are set to a solid color instead of a skybox to name a few.</p>
{% include end-expand.html %}

Finally hit **"Create project"**.

![UnityNewConfig](./01/UnityNewConfig.PNG)

After Unity finishes setting up your project, you will be greeted with the **Unity Editor**.


![UnityEditor](./01/UnityEditor.PNG)

### Importing Unity Packages

At any point when developing your project you can import a Unity Package to your game. For this project, we will be using a Unity package the instructors have developed to jump-start the project. 

{% include start-expand.html title="What is a Unity package?" %} 
  <p>Unity packages are a collection of Assets that you can import into your project</p>
  <p>What separates Unity packages from simply dragging in your assets is that Unity packages support meta data. This means that settings on things like textures will already be setup correctly. It also means that a Unity package can have Unity specific assets like Prefabs, Scenes, and Materials.</p>
{% include end-expand.html %}

First download the **Unity Package** from the [canvas website](https://umich.instructure.com/courses/164929/files/folder/p1). You can find it in the "Files" tab inside the "p1" folder with the name "494-p1-templatePackage.unitypackage".

![CanvasSite](./01/CanvasSite.PNG)

Once downloaded **double click** the .unitypackage and it should open up into your current Unity project.

![ImportPackage](./01/ImportPackage.PNG)

A list of assets will appear. From here you can choose what you want and don't want to import. In this case, we don't want the Zelda assets so feel free to uncheck those. Once that's done hit **Import**.

![PostImport](./01/PostImport.PNG)

Thanks to the Unity package, we now have a number of new assets in our project. It isn't important to know what all of these are right now, but as we go through the tutorial we will use all of these.

Note that this isn't a complete set of assets that you'll need for your game, it's up to you to find the rest!

{% include start-expand.html title="Where can I find the other assets I need?" %} 
  <p>Unity provides a number of standard asset Unity packages that you can import by simply going to "Assets" tab and selecting "Import Package".</p>
  <p>For the sprites you'll need, you can check out spriters-resource.com. However, note that there needs to be special care to import any images into your project; we'll cover this in the next section.</p>
  <p>For the sound effects you'll need, you can check out spriters-resource.com</p>
{% include end-expand.html %}

{% include start-expand.html title="Where else can I find Unity packages?" %} 
  <p>Unity provides a number of standard asset Unity packages that you can import by simply going to "Assets" tab and selecting "Import Package".</p>
  <p>In addition, you can find many unity packages, both free and paid, on the Unity Store.</p>
  <p>For this project you won't be required to use any other unity packages, but in future projects you're free to explore some of these.</p>
{% include end-expand.html %}
