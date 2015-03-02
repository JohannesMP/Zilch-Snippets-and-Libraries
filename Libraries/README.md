# Libraries

A collection of (mostly) complete and tested Zero/Zilch Libraries. Each library contains a Zero Project, as well as a '`JustCode`' directory that contains only the library scripts.

## Contents

Libraries were last tested with **Zero Build 10681**

### <a href=https://github.com/JohannesMP/Zilch-Snippets-and-Libraries/tree/master/Libraries/TYPE_Map>Type: Map</a>

<img width=300 src=http://i.imgur.com/scltrMn.png/>

- Currently you cannot iterate over <a href=http://zero.digipen.edu/Zilch/ZilchTypes/HashMap.html>hashmaps</a> in Zilch.
- This custom container combines a hashmap and an <a href=http://zero.digipen.edu/Zilch/ZilchTypes/Array.html>array</a> to allow you to iterate over it, while still being able to use it like a hashmap.
- It also includes some additional functionality, such as being able to sort by Keys or Values.


### <a href=https://github.com/JohannesMP/Zilch-Snippets-and-Libraries/tree/master/Libraries/UI_StateManager>UI: State Manager</a>

<img width=300 src=http://i.imgur.com/trA26PH.png />

- An initial attempt to create an abstraction layer to correctly handle UI interactions and events for individual elements. 
- The `UIStateManager` component allows the user to track several UI 'states', such as visible, active, selected, as well as mouse-related states such as hover and being held by any number of mouse buttons.
- It also handles sending a UI click event when a true 'click' occurred, accounting for edge cases that simply listening to `Events.MouseUp` or `Events.MouseUpdate` would miss, while providing additional meta information such as what mouse button was released during the mouseUp.

*NOTE:* this is being reworked, but is usable in its current state.

## License

All content is provided free for all DigiPen students to use, copy, modify, etc. without limitations.

***All content © 2015 DigiPen (USA) Corporation, all rights reserved***

