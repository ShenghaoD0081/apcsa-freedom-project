# Entry 4
##### 3/20/22

### Content

During these weeks, I have worked on making the camera follow the player. Since I'm making a Top-Down game I would have to orient the camera above the player and not behind (for third person) or on the player (for first person). In order to get a deeper understanding of how to have the camera follow the player I watched this [video](https://www.youtube.com/watch?v=GOQV688wbU0). For starters I needed to make a public [Transform](https://docs.unity3d.com/ScriptReference/Transform.html), transform is used to change the position, rotation, and scale of a object. In this case we will need to use transform to change the position of our camera. In this case we will name our Transform "target" and the target will be set as the player. At first I tried this code below:

`(transform.position = new Vector3(target.transform.position.x, target.transform.position.y, target.transform.position.z);`

What this does is change the position of the camera to exactly where the player is. As you can see I used a [Vector3]() here which takes in 3 values, and here we are taking the players x, y, and z coordinates to find out exactly where the player is. However when you run this code you will see something like this: 

![image](https://user-images.githubusercontent.com/56265106/159388766-691099d2-b75e-44c6-a2c8-06eb5b0e39cc.png)

As you can see it's just a blue screen. This is caused by us having the same z value (up and down) as the player which puts us under the player. The result is what you see here, a blue screen. In order to fix this, I changed `target.transform.position.z` to `transform.position.z` which makes it so we only change to the player's x and y coordinates and instead we have a top down view now, here is the new result:

![Alt Text](https://user-images.githubusercontent.com/56265106/159388682-916f0008-82e1-4e3e-b8c7-662bc9268d2d.gif)

As you can now the camera properly follows the player. The Red Cube you see here is the "Enemy" and it's following the player using pathfinding that I wrote about in my last blog entry.

### Engineer Design Process

I am still creating a prototype. There are still many features I have to add such as health bars and a attacking system for both the player and the enemy. I am beginning to inch towards the finished product little by little. So far the project has no game breaking bugs which  is a good thing but it is something I will have to note down in the future when there is more code and the game wil be more prone to bugs at that time. One important skill I learned was to **READ** things carefully. Sometimes I'm too absorbed into watching tutorials on how to do something and get stuck there when I could just read the documentation. The [Unity Documentation](https://docs.unity3d.com/Manual/index.html) really helps me out a lot and whenever there was something I didn't understand I would reference it.

### Next Plans

I still want to make it so the camera following the player doesn't go out of the map but that is lower on my priority. I want to first finish changing scenes so I can create more maps for the game. Then I want to add a attack system as well as a HP system. I want to prioritize the mechanics that are vital to a RPG game before I make any quality of life changes that would make the game more enjoyable. I also plan on trying to draw my own sprites and maybe trying to animate them but that will be quite difficult. Hopefully I will be able to make one as it will make the game more unique.

[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
