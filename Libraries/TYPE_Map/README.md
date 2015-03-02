
# Type: Map

<img width=300 src=http://i.imgur.com/scltrMn.png/>

- Currently you cannot iterate over <a href=http://zero.digipen.edu/Zilch/ZilchTypes/HashMap.html>hashmaps</a> in Zilch.
- This custom container combines a hashmap and an <a href=http://zero.digipen.edu/Zilch/ZilchTypes/Array.html>array</a> to allow you to iterate over it, while still being able to use it like a hashmap.
- It also includes some additional functionality, such as being able to sort by Keys or Values.

For example, you can use the `Map` type like this:

    var map = new Map[String, Real3]()[ ["foo",  Real3(1,2,3)],
                                        ["derp", Real3(4,5,6)],
                                        ["bar",  Real3(7,8,9)] ];
    foreach(var pair in map)
    {
      Console.WriteLine("Key: `pair.Key`, Value: `pair.Value`");
    }

For usage examples check the <a href=https://github.com/JohannesMP/Zilch-Snippets-and-Libraries/blob/master/Libraries/TYPE_Map/Content/MapTest.z>`MapTest.z`</a> file in the included project that has several testing functions that print stuff to the console.

## License

All content is provided free for all DigiPen students to use, copy, modify, etc. without limitations.

***All content © 2015 DigiPen (USA) Corporation, all rights reserved***

