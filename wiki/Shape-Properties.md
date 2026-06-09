## What are shape properties?

Open **Shape -> Properties** in Outfit Studio, or double-click a shape in the shape list, to edit mesh-specific metadata such as shader settings, geometry flags, extra data, and coordinate transforms.

You can also open the dialog with multiple shapes selected. In that case Outfit Studio switches to a batch-edit workflow:

* The dialog title shows how many shapes are selected.
* The **Geometry** tab becomes the default tab.
* Single-shape tabs such as **Extra Data** and **Coordinates** are disabled.
* Batch operations that can safely affect every selected shape ask for confirmation before they run.

The dialog currently has four tabs: **Shader**, **Geometry**, **Extra Data**, and **Coordinates**.

[![Shader](http://i.imgur.com/R4ao6aKb.png)](http://i.imgur.com/R4ao6aK.png)
[![Geometry](http://i.imgur.com/50BYgYZb.png)](http://i.imgur.com/50BYgYZ.png)
[![Extra Data](http://i.imgur.com/SGoo36jb.png)](http://i.imgur.com/SGoo36j.png)
[![Coordinates](https://i.imgur.com/ApCWZwqb.png)](https://i.imgur.com/ApCWZwq.png)

## Shader

The **Shader** tab controls the material/shader block attached to the current shape.

### Basic fields

* **Name / Material** stores the shader name on older games. On Fallout 4 it is treated as the assigned `.bgsm` or `.bgem` material path. On Starfield it is treated as the assigned `.mat` material path.
* The **...** button next to the field opens a material picker when the target game supports external material files.
* **Type** changes the shader type for supported lighting shaders. The available list depends on the shader class and game.
* **Shading** is shown for Fallout 3 / New Vegas post-processing lighting shaders and lets you switch between hard and smooth shading.
* **Specular Color**, **Specular Strength**, **Specular Power**, **Emissive Color**, **Emissive Multiple**, and **Alpha** expose the common lighting/material values currently supported by the dialog.
* **Vertex Colors** toggles vertex-color usage on the shader. Enabling vertex alpha also enables vertex colors automatically.
* **Double Sided** toggles double-sided rendering. Fallout 3 / New Vegas store this through the stencil property instead of the usual shader flags, so the behavior is game-specific.

### Buttons

* **Add** creates a default shader/material setup for shapes that do not already have one.
* **Remove** removes the shader block from the selected shape or shapes.
* **Textures...** opens the texture-set editor for the current shader.
* **Copy from shape...** clones the shader and texture assignment from another shape in the same project.

### Shader flags

The **Shader Flags** collapsible section exposes the full game-specific flag lists for:

* Skyrim-family lighting shaders
* Fallout 4-family lighting shaders
* Fallout 3 / New Vegas shader properties

The dialog keeps the common checkboxes such as **Vertex Colors**, **Vertex Alpha**, and **Double Sided** synchronized with the relevant flag bits where that makes sense for the target game.

### Advanced shader properties

The **Advanced** collapsible section is no longer just a placeholder. It now exposes the advanced properties that Outfit Studio can edit directly for the current shader type.

Common fields include:

* **UV Offset** and **UV Scale**
* **Texture Clamp Mode**
* **Refraction Strength**
* **Environment Map Scale**

Additional fields appear only when they apply to the current shader type, for example:

* **Skin Tint Color**
* **Hair Tint Color**
* **Parallax Max Passes** and **Parallax Scale**
* **Inner Layer Thickness**, **Parallax Refraction Scale**, **Inner Layer Tex Scale**, and **Parallax Envmap Strength** for multilayer parallax
* **Sparkle Parameters** for sparkle snow shaders
* **Eye Cubemap Scale** and left/right reflection centers for eye shaders

Fallout 4-format lighting shaders also expose the newer material fields such as:

* **Wet Material**
* **Subsurface Rolloff**
* **Rimlight Power** and **Backlight Power**
* **Grayscale To Palette**
* **Fresnel Power**
* **Wetness Spec Scale**, **Wetness Spec Power**, **Wetness Min Var**, **Wetness Fresnel Power**, **Wetness Metalness**
* **Wetness Env Map Scale** where that value exists in the file format

Starfield hides the legacy shader-type, specular, shader-flags, and advanced panes because those controls do not map cleanly to Starfield materials.

### Transparency

The **Transparency** collapsible section manages the shape's alpha property.

Supported controls include:

* **Threshold**
* **Vertex Alpha**
* **Alpha Test**
* **Alpha Blend**
* **Src Blend** and **Dest Blend**
* **Test Function**
* **No Sorter**
* **Add** / **Remove** to create or delete the alpha property itself

If the selected shape already has an alpha property, the transparency pane expands automatically when the dialog opens.

## Geometry

The **Geometry** tab exposes mesh-format flags that are safe to batch-edit across multiple selected shapes. When several shapes are selected, the checkboxes use three states so you can see whether the current selection already matches.

* **Full Precision** toggles full-precision vertex storage when the selected mesh format supports changing that flag.
* **Sub Index** converts between `BSTriShape` and `BSSubIndexTriShape`. When enabling it, Outfit Studio creates a default segment layout for the new sub-indexed shape.
* **Skinned** adds or removes skinning data. Turning it off removes the current skinning setup; turning it back on recreates default skinning data.
* **Dynamic** converts between `BSTriShape` and `BSDynamicTriShape` on formats that support that distinction.

Availability depends on both the game format and the selected shape type. If a checkbox is disabled, the current mesh cannot be converted that way.

## Extra Data

The **Extra Data** tab edits `NiExtraData` blocks attached to the shape. This tab is available only for single-shape editing.

Outfit Studio currently supports creating and editing all of the following types directly from the dialog:

* `NiStringExtraData`
* `NiIntegerExtraData`
* `NiFloatExtraData`
* `NiBooleanExtraData`
* `NiVectorExtraData`
* `NiColorExtraData`
* `NiIntegersExtraData`
* `NiStringsExtraData`
* `NiFloatsExtraData`
* `BSDistantObjectLargeRefExtraData`

Each entry has:

* A **Remove** button
* A **type** selector
* A **name** field
* A value editor suited to that data type

Simple string, integer, float, and boolean values can be edited inline. Vector, color, and list-based extra data use dedicated editor dialogs:

* Vector and color entries open an **Edit...** dialog with per-component fields.
* Color entries also include a color picker preview.
* Integer, string, and float lists open a grid editor with **Add Row** and **Remove Row** controls.

Unknown extra-data block types are not exposed through this dialog.

## Coordinates

The **Coordinates** tab edits the transform from the shape's local space to global space. This is the stored scale, translation, and rotation difference between the mesh data and the shape's world placement.

You can edit:

* **Scale**
* **X / Y / Z** translation
* **X / Y / Z** rotation

When you change any of these values, Outfit Studio enables **Recalculate geometry's coordinates so it doesn't move**. If you keep that box checked, the mesh vertices are transformed so the shape stays in the same place visually while the stored transform changes.

This tab is only available when a single shape is selected.

## Notes

* The dialog is no longer limited to just a few high-level shader values. The current advanced shader and extra-data editors are usable enough for many common tasks that previously required switching to NifSkope.
* Fallout 3 / New Vegas still have a few engine-specific quirks, especially around vertex alpha and double-sided rendering.
* Reference-loading, texture assignment, and material-file behavior still depend on the target game's file format, so always test the result in the game or in NifSkope if you are changing unusual shader combinations.