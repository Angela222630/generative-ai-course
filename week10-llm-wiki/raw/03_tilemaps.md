# Tilemaps

- **來源網址**: https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/tilemaps/tilemaps
- **適用版本**: Unity 6.0 (6000.0)
- **擷取時間**: 2026-11-22
- **官方標題**: Tilemaps

---

* [Unity Engine documentation](/en-us/engine/6000.0)
*
* [Unity 6.0 User Manual](/en-us/engine/6000.0/manual)
*
* [2D game development](/en-us/engine/6000.0/manual/unity2d)
*
* [Tilemaps](/en-us/engine/6000.0/manual/unity2d/tilemaps)

# Introduction to tilemaps
Learn about how to create a tilemap, and the different layouts of tilemaps.Read time 1 minuteLast updated 23 days ago

An example of a 2D farming game that uses rectangular tilemap. The environment is laid out on a rectangular grid.

Build the game world and levels of your 2D project by painting tiles onto the scene.
NoteTo use tilemaps, make sure the 2D Tilemap Editor package is installed in your project. For more information, refer to [set up your project for 2D games](/en-us/engine/6000.0/manual/unity2d/2d-game-development/setup-project-2d-game).
To paint with tiles, follow these steps:

* [Create a tile palette](/en-us/engine/6000.0/manual/unity2d/tilemaps/create-tile-palette/assets), which is a collection of tile assets you paint with. Tile assets are rectangular, isometric, or hexagonal sprites.

* Create a tilemap, which is the area you paint the tiles onto, then paint your tiles. For more information, refer to [Paint tiles into the scene](/en-us/engine/6000.0/manual/unity2d/tilemaps/create-tilemap/create-tilemap).

## [](#render-pipeline-compatibility)Render Pipeline Compatibility

Tilemaps are supported by all render pipelines that support 2D projects.

## [](#types-of-tilemap)Types of tilemap

Unity supports the tilemaps with the following tile layouts:

* Rectangular. This is the default.

* Hexagonal. This type of tilemap is often used for strategy games. You can align the hexagons so they have a point at the top, or a flat edge at the top.

* Isometric. This type of tilemap uses a 2D grid to create the illusion of 3D height and depth.

A rectangular tilemap, a flat top hexagonal tilemap, a point top hexagonal tilemap, and an isometric tilemap

## [](#additional-resources)Additional resources

* [Tilemap API documentation](/en-us/engine/6000.0/script-reference/unityengine/tilemaps/tilemap)

* [2D Tilemap Extras](https://docs.unity3d.com/Packages/com.unity.2d.tilemap.extras@latest)

Copyright © 2026 Unity Technologies[Legal](https://unity.com/legal)[Privacy Policy](https://unity.com/legal/privacy-policy)[Cookies](https://unity.com/legal/cookie-policy)[Documentation Terms of Use](https://unity.com/legal/docs-terms)[Do Not Sell or Share My Personal Information](https://unity.com/legal/do-not-sell-my-personal-information)[Your Privacy Choices (Cookie Settings)](#)

"Unity", Unity logos, and other Unity trademarks are trademarks or registered trademarks of Unity Technologies or its affiliates in the U.S and elsewhere ([more info here](https://unity.com/legal/trademarks)). Other names or brands are trademarks of their respective owners.

Some pages are machine-translated for convenience, and may contain inaccuracies. In the event of conflicting information, the English version is authoritative.