# Experimentals

These are various Zero Projects created for the sake of exploring a specific feature or concept. They are in varying states of completion/buggyness and should be used at your own risk.

## Contents

Experimentals were last tested with **Zero Build 10681**.

### <a href=https://github.com/JohannesMP/Zilch-Snippets-and-Libraries/tree/master/Experimentals/Arc_Predict>Arc Prediction</a>
<img width=300 src=http://i.imgur.com/br4Q816.png />
* Using JDebug to draw some ballistic arcs that take gravity and drag into account
* Features various parameters that you can modify via keyboard with on-screen instructions

This was a fun exploration of properly pre-predicting physics for debug purposes. Special thanks to Rob for his physics insights and getting the simulated arc physics to exactly match up with those of the actual engine.

I may expand on this later with a general library that takes delegates as an argument, allowing you to do fun things like accurately draw the path a particle would take through a gravity/vector field.


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

