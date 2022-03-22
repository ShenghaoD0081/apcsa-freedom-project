# Entry 4
##### 3/20/22

Content:

During these weeks, I have worked on making the camera follow the player. Since I'm making a Top-Down game I would have to orient the camera above the player and not behind (for third person) or on the player (for first person). In order to get a deeper understanding of how to have the camera follow the player I watched this [video](https://www.youtube.com/watch?v=GOQV688wbU0). For starters I needed to make a public [Transform](https://docs.unity3d.com/ScriptReference/Transform.html), transform is used to change the position, rotation, and scale of a object. In this case we will need to use transform to change the position of our camera. In this case we will name our Transform "target" and the target will be set as the player. At first I tried this code below:

`(transform.position = new Vector3(target.transform.position.x, target.transform.position.y, target.transform.position.z);`

What this does is change the position of the camera to exactly where the player is. As you can see I used a [Vector3]() here which takes in 3 values, and here we are taking the players x, y, and z coordinates to find out exactly where the player is. However when you run this code you will see something like this: 

![image](https://user-images.githubusercontent.com/56265106/159387821-92dedda1-9fd8-4802-b009-9cc19b8a75c8.png)

As you can see it's just a blue screen. This is caused by us having the same z value (up and down) as the player which puts us under the player. The result is what you see here, a blue screen. In order to fix this, I changed `target.transform.position.z` to `transform.position.z` which makes it so we only change to the player's x and y coordinates and instead we have a top down view now, here is the new result:

![Alt Text](https://user-images.githubusercontent.com/56265106/159388682-916f0008-82e1-4e3e-b8c7-662bc9268d2d.gif)


[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
