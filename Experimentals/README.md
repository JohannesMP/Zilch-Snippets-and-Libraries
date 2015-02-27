# Experimentals

These are various Zero Projects created for the sake of exploring a specific feature or concept. They are in varying states of completion/buggyness and should be used at your own risk.

## Contents

Experimentals were last tested with **Zero Build 10681**.

### <a href=https://github.com/JohannesMP/Zilch-Snippets-and-Libraries/tree/master/Experimentals/Arc_Predict>Arc Prediction</a>
<img width=300 src=http://i.imgur.com/br4Q816.png />
* Using JDebug to draw some ballistic arcs that take gravity and drag into account
* Features various parameters that you can modify via keyboard with on-screen instructions

This was a fun exploration of properly pre-predicting physics for debug purposes. Special thanks to Rob for his physics insights and getting the simulated arc physics to exactly match up with those of the actual engine.

- The basic idea is to take a given point, its current velocity and the forces it is experiencing, then run the same calculation that the engine would do to arrive at a new point, with its own new velocity.
- In a `for` loop, run this calculation for X number of iterations, each time taking the point/velocity of the previous iteration as the starting point for the current one.
- The critical point to realize is that while calculating lots of physics is (relatively) fast, drawing lines between every single point is not. Therefore if you plan on drawing the arc in the game space, use some metric to only draw a line every X number of points
- In the case here I kept a running total of the distances between all the points, and only drew a new line connecting two points once a minimum distance was reached. This ensures that the endpoints between lines are always about the same distance apart.
- The best solution would be to look at the slope of the line and only draw a new line once a certain change in slope has been reached, which would allow long straight parts of the line to only consist of very few line segments.

I may expand on this later with a general library that takes delegates as an argument, allowing you to do fun things like accurately draw the path a particle would take through a gravity/vector field.


### <a href=https://github.com/JohannesMP/Zilch-Snippets-and-Libraries/tree/master/Experimentals/Follow_Target>Follow Target</a>
<img width=300 src=http://i.imgur.com/9If3seo.png />

A small example script that shows how getters and setters can be used to create complex behavior with very little code. The core code is in FollowTarget.z, and the interesting part is first few lines before initialize that define TargetDist and targetDiff. 

You can move the objects on the screen with the arrow keys. Notice how the objects appear as if they have a physics simulation with joints, etc governing their behavior. It's actually far simpler than that.


* On a given object you can set its target via the TargetPath property. 
* By simply setting TargetDist equal to a given value, the getters/setters correctly resolve the position of the object relative to its target.
* Then all you have to do is create a bunch of objects and chain them together with their respective targetpaths, and you get behavior that appears far more complex than it actually is.
* Here are some examples of behaviors you can achieve:
    * Replace the contents of `OnLogicUpdate` with `this.TargetDist = 1.0;`
    * Replace the contents of `OnLogicUpdate` with `this.TargetDist *= 0.95;`
       * now parent the camera to one of the objects in the chain (making sure to set its relative X and Y coordinates to 0)


### <a href=https://github.com/JohannesMP/Zilch-Snippets-and-Libraries/tree/master/Experimentals/Masked_Sprites>Masked Sprites</a>
<img width=300 src=http://i.imgur.com/3Jncu5W.png />
* A crude implimentation of a 'masking' functionality for sprites, since Zero currently does not allow us to draw to our own textures.
* Run project in the editor and move the mouse over the center of the sprite in the middle to reveal the masked sprite.

This was definitely the kind of project where it's less about the number of lines of code, and more about conceptually figuring out how to achieve the desired effect.

The masking effect is created as follows:

1. On the level with the sprites to be masked, use the `DeferredRenderer` component with `RenderMasks` enabled.
2. You will need a png that is completely transparent, which will be used to hide our sprites outside the mask, and import it as a SpriteSource
3. Create a Sprite object with the transparent texture as spritesource, a `BlendMode` of `Multiply` and `RenderMask` enabled. note that enabling `RenderMask` will make the sprite appear invisible in the editor.
4. Add the `Area` component on the sprite, and make sure that Transform->Scale is 1,1,1
5. At runtime our code needs to scale ths transparency sprite to cover the entire screen.
   - See `ScaleToScreen.z`, which uses the area component and my `CameraBounds.z` snippet.
   - running the game now should hide any other sprites in the level.
6. Add a Sprite Object with a `SpriteSource` that corresponds to the 'visible' component of the desired mask. (I just used the default 'Circle'). Set its `BlendMode` to `Alpha` and enable `RenderMask`.
   - Whatever sprites (without RenderMask enabled) are now behind this object will be visible.
   - I just added a script that moves it to always be under the mouse (see `MaskLogic.z` which uses my `MousePos.z` Snippet).
7. While not required, I chose to do this in a separate level which is then loaded into its own space on top of the base level (which is still using the normal ForwardRenderer). This means that The base level is unaffected by the Masking.

## License

All content is provided free for all DigiPen students to use, copy, modify, etc. without limitations.

***All content © 2015 DigiPen (USA) Corporation, all rights reserved***

