# Game objects

- **來源網址**: https://docs.unity.com/en-us/engine/6000.0/manual/working-with-gameobjects/game-objects
- **適用版本**: Unity 6.0 (6000.0)
- **擷取時間**: 2026-11-22
- **官方標題**: Game objects

---

* [Unity Engine documentation](/en-us/engine/6000.0)
*
* [Unity 6.0 User Manual](/en-us/engine/6000.0/manual)
*
* [GameObjects](/en-us/engine/6000.0/manual/working-with-gameobjects)

# Introduction to GameObjects
Understand what GameObjects are and their fundamental role as containers for components in Unity.Read time 2 minutesLast updated 23 days agoThe GameObject

?

is the most important concept in the Unity Editor.
Every object in your game is a **GameObject**, from characters and collectible items to lights, cameras and special effects. However, a GameObject can't do anything on its own; you need to give it properties before it can become a character, an environment, or a special effect.

Four different types of GameObject: an animated character, a light, a tree, and an audio source

**GameObjects** are the fundamental objects in Unity that represent characters, props and scenery. They do not accomplish much in themselves but they act as containers for **Components**, which implement the functionality.
To give a GameObject the properties it needs to become a light, or a tree, or a camera, you need to add [components](/en-us/engine/6000.0/manual/working-with-gameobjects/unity-components/components) to it. Depending on what kind of object you want to create, you add different combinations of components to a GameObject.
Unity has lots of different built-in component types, and you can also make your own components using the [Unity Scripting API](/en-us/engine/6000.0/manual/working-with-gameobjects/unity-components/creating-components).
For example, a Light object is created by attaching a [Light](/en-us/engine/6000.0/manual/lighting-overview/lighting-birp/class-light) component to a GameObject.

A simple Light GameObject with several Components

A solid cube object has a Mesh Filter and Mesh Renderer component, to draw the surface of the cube, and a Box Collider component to represent the object's solid volume in terms of physics.

A simple Cube GameObject with several Components

## [](#details)Details

A GameObject always has a [Transform](/en-us/engine/6000.0/manual/working-with-gameobjects/gameobject-fundamentals/class-transform) component attached (to represent position and orientation) and it is not possible to remove this. The other components that give the object its functionality can be added from the editor's **Component** menu or from a script. There are also many useful pre-constructed objects (primitive shapes, Cameras, etc) available on the **GameObject > 3D Object** menu, see [Primitive Objects](/en-us/engine/6000.0/manual/working-with-gameobjects/gameobject-fundamentals/primitive-objects).
Because GameObjects are an important part of Unity, there is a lot of manual content with extensive detail about them. See the following sections for more information on using GameObjects in Unity:

* [Transforms](/en-us/engine/6000.0/manual/working-with-gameobjects/gameobject-fundamentals/class-transform)

* [Introduction to components](/en-us/engine/6000.0/manual/working-with-gameobjects/unity-components/components)

* [Using Components](/en-us/engine/6000.0/manual/working-with-gameobjects/unity-components/using-components)

* [Primitive and placeholder objects](/en-us/engine/6000.0/manual/working-with-gameobjects/gameobject-fundamentals/primitive-objects)

* [Creating components with scripting](/en-us/engine/6000.0/manual/working-with-gameobjects/unity-components/creating-components)

* [Deactivating GameObjects](/en-us/engine/6000.0/manual/working-with-gameobjects/gameobject-fundamentals/deactivating-game-objects)

* [Tags](/en-us/engine/6000.0/manual/working-with-gameobjects/tags)

* [Static GameObjects](/en-us/engine/6000.0/manual/working-with-gameobjects/gameobject-fundamentals/static-objects)

* [Saving your work](/en-us/engine/6000.0/manual/unity-editor/editor-navigating-managing/saving)

You can find out more about controlling GameObjects from scripts on the [GameObject scripting reference page](/en-us/engine/6000.0/script-reference/unityengine/gameobject).Copyright © 2026 Unity Technologies[Legal](https://unity.com/legal)[Privacy Policy](https://unity.com/legal/privacy-policy)[Cookies](https://unity.com/legal/cookie-policy)[Documentation Terms of Use](https://unity.com/legal/docs-terms)[Do Not Sell or Share My Personal Information](https://unity.com/legal/do-not-sell-my-personal-information)[Your Privacy Choices (Cookie Settings)](#)

"Unity", Unity logos, and other Unity trademarks are trademarks or registered trademarks of Unity Technologies or its affiliates in the U.S and elsewhere ([more info here](https://unity.com/legal/trademarks)). Other names or brands are trademarks of their respective owners.

Some pages are machine-translated for convenience, and may contain inaccuracies. In the event of conflicting information, the English version is authoritative.