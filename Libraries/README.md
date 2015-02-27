# Libraries

A collection of (mostly) complete and tested Zero/Zilch Libraries. Each library contains a Zero Project, as well as a '`JustCode`' directory that contains only the library scripts.

## Contents

Libraries were last tested with **Zero Build 10681**

### <a href=https://github.com/JohannesMP/Zilch-Snippets-and-Libraries/tree/master/Libraries/TYPE_Map>`Map` Type</a>

- Currently you cannot iterate over <a href=http://zero.digipen.edu/Zilch/ZilchTypes/HashMap.html>hashmaps</a> in Zilch.
- This custom container combines a hashmap and an <a href=http://zero.digipen.edu/Zilch/ZilchTypes/Array.html>array</a> to allow you to iterate over it, while still being able to use it like a hashmap.

For example, you can use the `Map` type like this:

    var map = new Map[String, Real3]()[ ["foo",  Real3(1,2,3)],
                                        ["derp", Real3(4,5,6)],
                                        ["bar",  Real3(7,8,9)] ];
    foreach(var pair in map)
    {
      Console.WriteLine("Key: `pair.Key`, Value: `pair.Value`");
    }

## License

All content is provided free for all DigiPen students to use, copy, modify, etc. without limitations.

***All content © 2015 DigiPen (USA) Corporation, all rights reserved***

