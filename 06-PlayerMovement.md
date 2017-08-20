## Basic Player Movement

We're finally ready to start writing some code! Create a new Script **PlayerMovement.cs** in your scripts folder. Add this to your **Player** prefab (or to the one in your scene, but make sure to **apply** your changes at the end!)

![PlayerMovementCS](./06/PlayerMovementCS.PNG)

{% include start-expand.html title="Couldn't I just create a Player.cs script and write all of my code there?" %}
<p>No no no no no!</p>
<p>One of the most important concepts of Unity is having your components as small and specialized as possible! This will make your code a lot easier to maintain and much more reusable</p>
<p>While the reasoning is a little less obvious for the Player, it is obvious once you start thinking about it in terms of an enemy</p>
<p>The Zoomer can Crawl, deal damage to things it hits, take damage, die, and drop collectables.</p>
<p>The Skree can Drop down, deal damage to things it hits, take damage, die, and drop collectables.</p>
<p>If you just had two separate scripts for these, you would end up rewriting all of the code except for movement. Not to mention how confusing it would be having one ~200 line solution instead of four ~50 line solutions</p>
<p>But seriously, in the past we've seen people come in with a single Player.cs script that's over 2000 lines long. Don't be one of those people.</p>
{% include end-expand.html %}

First add a new variable to store a reference to the **RigidBody**. In Awake() set this using **GetComponent()**.

![RigidBody](./06/RigidBody.PNG)

{% include start-expand.html title="What is GetComponent?" %}
<p>GetComponent is one of the most useful functions an object has access to. This is, and related functions, is how your scripts should communicate Unity's components (Rigidbodies, colliders, renderers, etc...) and with your own scripts.</p>
<p>Many students have trouble at first knowing when to use GetComponent(). Instead of using it they either write everything into one big script or use a lot of static variables. Don't do this or your code will quickly become unmaintainable.</p>
{% include end-expand.html %}

{% include start-expand.html title="Couldn't I just call GetComponent in Update? Why did I store it as a variable?" %}
<p>Calling GetComponent is a relatively expensive operation, and doing it every physics update can cause some performance issues.</p>
<p>In fact, you used to be able to do gameObject.rigidBody. However this has been deprecated as many newbies didn't realise that this was calling GetComponent behind the scenes.</p>
<p>The one exception to this is the Transform component. You can always call gameObject.transform and it will be pre-cached for you.</p>
{% include end-expand.html %}

{% include start-expand.html title="Why did I put \"this\" in front of GetComponent?" %}
<p>Partially because it makes sense for me to think about it as a function of the object itself rather than some global function, but mostly because it makes the auto-complete come up a bit faster :).</p>
{% include end-expand.html %}

### Horizontal Movement

We are also going to need a **public float** to control the player's move speed. Set its value to **5** for now.

![MoveSpeed](./06/MoveSpeed.PNG)

{% include start-expand.html title="Why use floats and not doubles?" %}
<p>This is a game, not rocket science. We don't need that kind of precision here!</p>
<p>Plus there are very, very few instances where built-in Unity code uses doubles.</p>
{% include end-expand.html %}

{% include start-expand.html title="Why is moveSpeed public while rigid is (implicitly) private?" %}
<p>In addition to their traditional use, public variables also make a variable visible and changeable in the Unity inspector.</p>
<p>This is preferred for things like Movement Speed that we may want to play around with, while a Rigidbody isn't something we want to manually set ourselves.</p>
<p>As an alternative to using public, you can also use the attributes [ShowInInspector] and [HideInInspector].</p>
{% include end-expand.html %}

Now that we have access to the **RigidBody**, we can update the **rigid.velocity**. Set a new **Vector3** equal to the current velocity. Update the x component of this to be equal to the Input on the Horizontal axis multiplied by the move speed.

![Horizontal](./06/Horizontal.PNG)

{% include start-expand.html title="What is Input.GetAxis()?" %}
<p>Input.GetAxis() returns a float from -1 to 1 for current along a given axis. The strength of this compared to calling individual keys is that it works regardless of whether you're using a controller, or a keyboard. Plus users can rebind these keys if they want to.</p>
{% include end-expand.html %}

{% include start-expand.html title="Why can't I just do something like rigid.velocity.x? Why do I need to make a new Vector3?" %}
<p>Under the hood, there is often times a good bit of extra work every time one of these variables is set. For instance, if you set transform.position to a new value, Unity has to update all of that object's children, colliders, renderers, and more.</p>
<p>To encourage reducing this work, Unity forces you to update it all at once instead of by x, y, and z.</p>
{% include end-expand.html %}


### Vertical Movement

The first thing you may think to do is add gravity. However, Rigidbodies default to having gravity by default.

{% include start-expand.html title="What if I want to change the acceleration of gravity?" %}
<p>You can either set the object to not use gravity then implement the downwards acceleration yourself, or change it in Edit->Project Settings->Physics.</p>
{% include end-expand.html %}

But we still need to add jumping. Just as you did with moveSpeed, make a public **jumpPower** variable and set it to **15**.

![JumpPower](./06/JumpPower.PNG)

Next check for the **A** key being pressed and set the velocity to the **jumpPower** when this happens.

![Vertical](./06/Vertical.PNG)

### Conclusion

And that's it for movement, run your game and you'll see that... there are a lot of problems...

![Movement](./06/Movement.GIF)

But that's OK because in the next tutorial we'll be going over how to fix these problems. When you're ready commit your changes and go to [07-Player Movement Fixes](./07-PlayerMovementFixes).