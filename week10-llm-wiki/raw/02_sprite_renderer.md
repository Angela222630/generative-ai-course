# Sprite Renderer component reference

- **來源網址**: https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/sprite/sprite-renderer-reference
- **適用版本**: Unity 6.0 (6000.0)
- **擷取時間**: 2026-11-22
- **官方標題**: Sprite Renderer component reference

---

* [Unity Engine documentation](/en-us/engine/6000.0)
*
* [Unity 6.0 User Manual](/en-us/engine/6000.0/manual)
*
* [2D game development](/en-us/engine/6000.0/manual/unity2d)
*
* [Sprites](/en-us/engine/6000.0/manual/unity2d/sprite)

# Sprite Renderer component reference
Explore the properties you can use to customize how Unity renders a sprite in the scene.Read time 3 minutesLast updated 2 months agoExplore the properties you can use to customize how Unity renders a sprite in the scene.

| #### **Property** | #### **Description** |
| --- | --- |
| **Sprite** | Sets the sprite Unity renders. To select a sprite, drag a sprite asset from the **Project** window, or select the picker (**⊙**). |
| **Open Sprite Editor** | Opens the sprite texture in the **Sprite Editor** window. For more information, refer to [Sprite Editor window reference](/en-us/engine/6000.0/manual/unity2d/sprite/sprite-editor-window-reference). |
| **Color** | Tints the sprite with the selected color. Set the color to white to render without a tint. |
| **Flip** | Mirrors the texture along the x-axis or the y-axis. Enabling this property doesn't move or mirror the location of the GameObject. |
| **Draw Mode** | Determines how Unity scales the sprite texture. The options are:**Simple**: Scales the entire sprite uniformly. This is the default.**Sliced**: Stretches the center and edges of the sprite but keeps the corners at their original size. Use this option only if you [9-slice the sprite](/en-us/engine/6000.0/manual/unity2d/sprite/9-slice/9-slicing).**Tiled**: Repeats the sprite texture to fill the new dimensions of the sprite. Use this option only if you [9-slice the sprite](/en-us/engine/6000.0/manual/unity2d/sprite/9-slice/9-slicing). For more information, refer to the [Draw Mode properties](#draw-mode-tiled) section. |
| **Mask Interaction** | Set how a [sprite mask](/en-us/engine/6000.0/manual/unity2d/sprite/mask) affects this sprite. The options are:**None**: Ignores sprite masks.**Visible Inside Mask**: Renders only the parts of the sprite that overlap with the sprite mask.**Visible Outside Mask**: Renders only the parts of the sprite that don't overlap with the sprite mask. |
| **Sprite Sort Point** | Sets which point on the sprite Unity uses to calculate its distance on the camera, which affects [render order during sorting](/en-us/engine/6000.0/manual/unity2d/sprite/sort-sprites/2d-renderer-sorting). The options are:**Center**: Unity calculates the distance from the camera to the center of the sprite.**Pivot**: Unity calculates the distance from the camera to the **Pivot** position of the sprite. To set the **Pivot** position, refer to [Sprite Editor tab reference for the Sprite Editor window](/en-us/engine/6000.0/manual/unity2d/sprite/sprite-editor-window-reference/reference). |
| **Material** | Sets the material for the sprite. The default material is `Sprite-Lit-Default`. To set the material, drag a material from the **Project** window, or select the picker (**⊙**). |

### [](#draw-mode-properties)Draw Mode properties

The following properties are available when you set the **Draw Mode** to **Sliced** or **Tiled**.

| #### **Property** | #### **Description** |
| --- | --- |
| **Size** | Sets the size of the sprite. |
| **Tile Mode** | Sets how Unity repeats, or tiles, the texture across the resized sprite. This property is available only if you set **Draw Mode** to **Tiled**. The options are:**Continuous**: Doesn't stretch the texture. The tiles at the edges might use cropped parts of the texture.**Adaptive**: Stretches the center of the texture until the width or height reaches the **Stretch Value**, at which point it repeats. Each tile always uses the full texture. |
| **Stretch Value** | Sets the width or height at which the sprite texture stops stretching and repeats instead. A value of 1 for **Stretch Value** means the center of the sprite repeats when the sprite is twice its original size. A lower value means the sprite repeats less often. |

## [](#additional-settings)Additional Settings

| #### **Property** | #### **Description** |
| --- | --- |
| **Sorting Layer** | Sets which layer the sprite belongs to, which determines when Unity renders it. Unity renders layers in the order of the list in the [Tags and layers window](/en-us/engine/6000.0/manual/unity-editor/editor-settings-reference/comp-manager-group/class-tag-manager). Select an existing layer, or select **Add Layer** to add a new sorting layer. For more information, refer to [Change the sorting order of 2D GameObjects](/en-us/engine/6000.0/manual/unity2d/sprite/sort-sprites/2d-renderer-sorting). |
| **Order in Layer** | Sets which sublayer the sprite belongs to within its **Sorting Layer**. Unity renders lower values before higher values. For more information, refer to [Change the sorting order of 2D GameObjects](/en-us/engine/6000.0/manual/unity2d/sprite/sort-sprites/2d-renderer-sorting). |
| **Rendering Layer Mask** | Sets which rendering layers this GameObject belongs to. For more information, refer to [Rendering Layers in URP](/en-us/engine/6000.0/manual/lighting-overview/lighting/rendering-layers). |

## [](#additional-resources)Additional resources

* [Add a sprite mask](/en-us/engine/6000.0/manual/unity2d/sprite/mask/hide-reveal-parts-sprite-mask)

* [Sorting sprites](/en-us/engine/6000.0/manual/unity2d/sprite/sort-sprites)

* [9-slicing](/en-us/engine/6000.0/manual/unity2d/sprite/9-slice/9-slicing)

Copyright © 2026 Unity Technologies[Legal](https://unity.com/legal)[Privacy Policy](https://unity.com/legal/privacy-policy)[Cookies](https://unity.com/legal/cookie-policy)[Documentation Terms of Use](https://unity.com/legal/docs-terms)[Do Not Sell or Share My Personal Information](https://unity.com/legal/do-not-sell-my-personal-information)[Your Privacy Choices (Cookie Settings)](#)

"Unity", Unity logos, and other Unity trademarks are trademarks or registered trademarks of Unity Technologies or its affiliates in the U.S and elsewhere ([more info here](https://unity.com/legal/trademarks)). Other names or brands are trademarks of their respective owners.

Some pages are machine-translated for convenience, and may contain inaccuracies. In the event of conflicting information, the English version is authoritative.