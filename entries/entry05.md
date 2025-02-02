# Entry 5
##### 4/26/22

### Content:
During this month I got a lot of content done, to be specific I added the core mechanics that allows the game to function on a basic level. First I made it so that the enemy can damage the user by making it so whenever the enemy collides with the player; the player gets damaged.

```C#
    private void OnCollisionStay2D(Collision2D collision)
    {
        if(collision.gameObject.tag == "Player")
        {
            if(attackSpeed <= canAttack)
            {
                collision.gameObject.GetComponent<PlayerHealth>().UpdateHealth(-attackDamage);
                canAttack = 0f;
            }
            else
            {
                canAttack += Time.deltaTime;
            }
        }
    }
}
```
The code is above is what I did. [OnCollisionStay2D](https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnCollisionStay2D.html) is what makes this method work. It will run every time there is a collision and if the collision has the tag "Player" which the player does then it will get the PlayerHealth component that is in another script and decrease it. I also added a cooldown since multiple collisions can happen in the same frame and this could lead to the player dying too fast. This script accesses something in my `PlayerHealth` script in order to damage the enemy.

```C#
public void UpdateHealth(float mod)
    {
        health += mod;

        if (health > maxHealth)
        {
            health = maxHealth;
        }else if(health <= 0f)
        {
            health = 0f;
            healthSlider.value = 0f;
            Debug.Log("You Died!");
            Destroy(gameObject);
        }
    }
```
As you can see since the method is public, the enemies can call it from their script and it activates when the enemy collides into the player. the `float` value can also be used to heal the player so this isn't just for damaging the player. I can later make items that heal the player and use this script for both damaging and healing the player.As you can see there is a `healthSlider` in the code. This [video](https://www.youtube.com/watch?v=VOdYtqV_meo) was really nice and taught me how to use a slider as the HP bar which was really useful since it's built in unity and I didn't need to find assets for the HP Bar. After this I made another script which I use to decrease the enemies' health.

```C#
   public void takeDamage(float damage)
    {
        health -= damage;

        if(health <= 0)
        {
            Destroy(gameObject);
        }
    }
  ```
  This is a public method and will be activated via another script which I called `Bullet` since the player can shoot bullets that can damage the enemy. This time I also made it so when the bullet collided with the enemy it will call `collision.gameObject.GetComponent<Enemy>().takeDamage(damage);` which gets the Enemy script of the object it touches and runs the `takeDamage` method. In this case only our enemy will have the Enemy script so the enemy will get damaged. Now let's talk about how I get the bullet working, for the bullet I saved a small circle asset as a [prefab asset](https://docs.unity3d.com/Manual/Prefabs.html) which allows me to save a game object as a asset. Then I added a `public GameObject` called bullet which allows me to drag my bullet asset into the script like so:
  ![image](https://user-images.githubusercontent.com/56265106/165414986-5810e0d3-f557-4af9-b872-f77fd64340b9.png)

With this down, now I can call the object in the script. With this I used [Instantiate](https://docs.unity3d.com/ScriptReference/Object.Instantiate.html) which basically spawns the object I designate in the position I want. With this I stored this information like such:
`GameObject projectile = Instantiate(bullet, rb.position, firePoint.rotation);` rb is the `rididbody` of the each individual bullet made which is needed to make the bullet move or else the bullet would just be stuck in mid air. With that done I did this:
`projectile.GetComponent<Rigidbody2D>().AddForce(firePoint.up * fireForce, ForceMode2D.Impulse);`
This adds force to the bullet by interacting with it's rigid body and adding force which allows it to move. This is all I added to my Freedom Project

### Engineer Design Process
With my Minimum Viable Product done, I am on the improving part of the Engineer Design Process. Next I want to improve it by making the gameplay more smooth. I think adding a dash system and a melee attack will make the game more engaging and fun. I also plan to add a menu so the player can unlock and play more levels. One skill I learned was to problem solving since not everything worked out and I had to search for new solutions. One example was that the player wasn't facing and shooting the bullets the right away and all I had to do is `-90f` which flips the way the player was facing 90 degrees which fixed the issue.

### Next Plans
After finishing my product I want to add more features to the game and making the UI look better. Currently my HP Bar is just a bar with  no color, I want to add color to that and add a heart on it to show that it's the HP Bar. The game also needs balancing since the game seems to easy right now so I also need to do that. After that I plan to add more enemy types in order to make the game more enjoyable. These are just the thoughts I have right now, there is still much more I need to do to improve the game.

[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)
