# Entry 2
##### 12/19/21

Throughout the past month I have been playing around with Unity quite a lot. Even though I wanted to make a 2D project, I actually tinkered around with 3D for quite a while as well. I think it's important to know both aspects since I'll most likely be using Unity for future projects as well. One thing I focused on this month is controlling the character, without it you wouldn't be able to move so it was one of the first things I started since it's very easy to see the results visually. 

First off when starting to code in Unity you will see something like this:

``
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class NewBehaviourScript : MonoBehaviour
{

    void Start()
    {
        
    }

    void Update()
    {
        
    }
}
``

The code above is what you will see when you load up a C# script. Everything inside ``void Start()`` will run once in the beginning and everything inside ``void Update()`` will once once per frame. You can also use ``void FixedUpdate()`` instead since it works better with physics but in my case I won't be using it since there are no physics in a 2D game (I hope so). After I learned about this I decided to try to make a Player Movement script and the code below is essential for that.

``
Input.GetAxis("Horizontal");
Input.GetAxis("Vertical");
``

This code above is what I used to get the user input for movement. The input of `horizontal` and `vertical` is determined by the WASD keys. If a user presses W the vertical will go towards 1, if the user presses S the vertical will go towards -1. This also applies to Vertical but with the A and D keys. You can also use the code below:

``
Input.GetAxisRaw("Horizontal");
Input.GetAxisRaw("Vertical");
``

The only difference from ``GetAxis()`` and ``GetAxisRaw()`` is that ``GetAxisRaw()`` will only return 0, 1, or -1 while ``GetAxis()`` will gradually change and also return the numbers in between. This can be both used, for example moving vertically would need ``GetAxis()`` so you can detect if it's closer to -1 or 1 then move according to those numbers. Once we get the axis, animation is quite easy as Unity has something called the [Animator Controller](https://docs.unity3d.com/Manual/class-AnimatorController.html). This allows you to set animations pretty easier, but it does get a bit messy if you have a lot of animations. This [video](https://www.youtube.com/watch?v=wdOk5QXYC6Y) helped me with 3D animation while this [video](https://www.youtube.com/watch?v=wdOk5QXYC6Y) helped me with 2D animation. Both were really useful as Unity can be a bit confusing at times since there is a lot of different things you have to do.

Another thing to keep in mind is that when using [C#](https://docs.microsoft.com/en-us/dotnet/csharp/)(the language Unity runs on) you often need to specify what unit you are using behind the number in which cases most will be a `float`, floats are similar to doubles but a `double` has 2 times the precision of a float. Floats are used more often that doubles because doubles tend to occupy more space hence they are more accurate. 

Currently I have a decent idea of what I want to do and I want to make the basis of the game first so I have to makecharacter walking, running, attacking, and more animations. I also need to make it so the player interacts with the world properly. To do this I will first use free assets off (Unity's Asset Store)[https://assetstore.unity.com/], there are paid assets but I will be using the free ones provided on the store. After that I plan to make my own assets and use them to make the game have more originalty. I'll also have to learn about tilemaps and how they work because that will be what I will use in order to build my maps in a RPG.

[Previous](entry01.md) | [Next](entry03.md)

[Home](../README.md)
