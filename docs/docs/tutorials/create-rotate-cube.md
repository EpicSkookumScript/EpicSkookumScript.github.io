---
layout: page
section: docs
title: Create a cube Blueprint and rotate it using SkookumScript
sidebar-page: none
footer: false
sharing: false

---

#### SkookumScript UE4 Plugin Basic Tutorial 1

1. Create a new UE4 project that uses **Starter Content**.

2. Select the **First-person** template.

3. In the UE4 Editor **Content** browser, navigate to **Geometry/Meshes**. Right-click **1M_Cube** > **Asset Actions** > **Create Blueprint Using This**.

4. Name your new Blueprint `BP_Cube`.

You now have a Blueprint that holds a static mesh of a cube. You may apply a material to the cube so it's more visible (**M_ColorGrid_LowSpec** is a good choice), but this is completely optional. 

{:start="5"}
5. Select the **StaticMesh** component.

6. Under **Physics**, turn off **Enable Gravity**.

7. Save and compile `BP_Cube`. (Note that the SkookumIDE will also auto-compile). 

Your new `BP_Cube` class will appear in the SkookumIDE **Classes** widget.

{:start="8"}
8. In the UE4 **Content** browser, navigate to **Blueprints** and drag our cube into the world somewhere. Make sure it's nice and visible.

9. Save your current level.

10. In the toolbar of the `BP_Cube` window, click the **[Sk]** (Show in IDE) button. This will take us to the `BP_Cube` class in the SkookumIDE **Classes** widget.

11. Ensure sure the class is highlighted and click **New Class or Member** at the bottom of the **Members** widget. (If a "Skookify your project?" confirmation message appears, click **OK**.)

The [**New Class or Member** pane](/docs/v3.0/ide/new/) is used to add subclasses, coroutines, data members, and methods to our highlighted class. In this case we will create a _constructor method_.

{:start="12"}
12. In the **New Class or Member** pane, create a constructor by typing `!` and pressing Enter.

13. Now create a coroutine by typing  `_rotate` and clicking **Add**. 

Your new `_rotate` coroutine will display in an **Editor** widget. This is where we'll put our code for rotating the cube. (We could have just added the code to the constructor itself, but it's a good rule of thumb to keep constructors brief and tidy).

{:start="14"}
14. Now we'll add the code for rotating the cube. In the `_rotate` **Editor** widget, paste in the following code:

{% highlight js %}
() 
[
loop
  [
  !r : RotationAngles!yaw_pitch_roll(100.0 * GameLib.world_delta_seconds 0.0 0.0)

  add_actor_world_rotation(r)

  _wait //wait until the next frame before executing this loop again
  ]
]
{% endhighlight %}

{:start="15"}
15. Now we'll call our coroutine from inside our constructor. Select `!` and paste in the following code:

{% highlight js %}
() 
[
branch [_rotate]
]
{% endhighlight %}

<div markdown="1" class="aside">
Learn more about the `branch` command [here](https://skookum.chat/t/branch-command-explained/118).
</div>

{:start="16"}
16. Press F7 to compile.

17. Run the project, and voilà! Behold a rotating cube!

Stay Skookum!

_Special thanks to [@Gigantoad](https://skookum.chat/users/gigantoad) for suggesting the basic problem, and to [@error454](https://skookum.chat/users/error454) for suggesting a solution!_

---
[**Next >>**{:.tip} **SkookumScript UE4 Plugin Basic Tutorial 2: Spawn cubes dynamically and manipulate them**](/docs/tutorials/spawn-cubes/)<br/>
[**<< Previous**{:.tip} **SkookumScript Intro Tutorial 1: Create and modify a method in SkookumScript**](/docs/tutorials/create-first-routine/)
{:.bubble-link}
