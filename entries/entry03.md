# Entry 3
##### 2/13/2022

### Progress
During this month I got quite a few things down. Taking into account the basics of the game, I would need the enemy to follow the player so they can attack the player which means I need pathfinding. It would take some time to make my own pathfinding algorithm so I decided to use the [A* Pathfinding](https://arongranberg.com/astar/] project. Later on I would like to make my own algorithm but it's too complicated for now so I would like to work on that later. The implentation was quite easy however since there was no obstacle my enemy could actually follow me any where so next I decided to get a tile map and have it act as a obstacle. One issue I ran into was that I wanted certain objects like trees and houses to be obstacles but grass shouldn't be a obstacle. To fix that I have different layers as such:

![image](https://user-images.githubusercontent.com/56265106/157583418-056e1d36-5bef-447f-9e89-4f5b0a049999.png)

This made it so that the obstacle works and the player and enemy both bump into them but the pathfinding algorithm doesn't actually detect the obstacles. To fix that I assigned a the obstacles into a layer called SolidObject and all obstacles will be on that layer. So now I can make it so that if there is anything on the SolidObject layer then it is a obstacle.

![image](https://user-images.githubusercontent.com/56265106/157583536-1f050199-3b65-4128-822a-0a288e7c1fd4.png)

With this the pathfinding is done... Well sort of. The pathfinding causes the enemy to follow the player anywhere but I don't want that so I made a script to disable the code that makes the pathfinding work when the enemy is in a certain radius of the player. The code below is what I wrote to achieve that.

``` C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PathfindRadius : MonoBehaviour
{
    // Start is called before the first frame update
    Pathfinding.AIDestinationSetter aiDestination;
    public GameObject player;
    [SerializeField] float distanceFromPlayer; //[SerializeField] means it's still private but you can see it in the game editor.
    public float distance = 5;
    private GameObject enemy;
    Pathfinding.AIPath aiPath;
    void Start()
    {
        aiDestination = this.gameObject.GetComponent<Pathfinding.AIDestinationSetter>();
        aiPath = this.gameObject.GetComponent<Pathfinding.AIPath>();
        enemy = this.gameObject;
    }

    // Update is called once per frame
    void Update()
    {
        distanceFromPlayer = Vector3.Distance(player.transform.position, enemy.transform.position);
        if(distanceFromPlayer < distance)
        {
            aiDestination.enabled = true;
            aiPath.enabled = true;
        }
        else
        {
            aiDestination.enabled = false;
            aiPath.enabled = false;
        }
    }
}

```
First I made a reference to game object which you can see as `public GameObject player;` (Note: Player is set to public because I want to be able to choose what "Player" is set as whenever I want) and using that reference we can find the distance of the enemy from the player and if it's longer than a certain set distance then I will disable the `AIPath` and `AIDestinationSetter` which is used by the enemy to follow the user. As you can see in the code I use something called `Vector3` which is 3 values. In this case we are taking the x, y, and z positions of the player and enemy and comparing them to find the distance. I also use a `[SerializeField]` which makes the variable private but you can still see it in the editor so I can manage to see how far the enemy actually is. Now I all do is drag my player into the script that I added on the enemy and now there is a radius where he chases me.

![image](https://user-images.githubusercontent.com/56265106/157584325-f77b1d46-15a6-433f-a4f3-22bed617a51e.png)


### Next plans
I plan to take things step by step this time. I want to make the camera follow the player first then make it so it doesn't go out of bounds (outside the map). Then I want to implement the attacking system and a health bar system since those features are vital in a RPG Game. After that I would like to find sprites and create a animation for them which makes the game more RPG like since all I have right now besides the tile map are squares as the player and enemy. I am currently on the creating part of the Engineer Design process so I want to finish the core features first and make sure my game properly works then I can move on to save and load features as well as the UI. 

### Goals
My current goal is to finish my MVP (Minimal Viable Project) by April and use May and June to fine tune the game by optimizing the code and adding things beyond the MVP. Knowing me, I know it's going to be a hard process and it's very likely that it won't even happen so I will have to be stricter on myself when deciding work dates for this project.

[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)
