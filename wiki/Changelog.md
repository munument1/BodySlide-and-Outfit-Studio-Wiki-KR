## 5.8.1
### Improvements:
- **BS (BodySlide):** Added a "Preview Always Detached" setting.
- **BS:** Added Starfield material texture support to BodySlide preview.
- **OS (Outfit Studio):** Highlight bones with weights in copy bone weights dialog.

### Fixes:
- **General:** Ignore skin-tinted shapes with clipping fixer (such as private parts).
- **General:** DPI-aware default window sizes for BS/OS.
- **BS:** Fixed crash when switching outfits with preview hidden.
- **BS:** Persist preview attachment and hidden state correctly.
- **BS:** Detect modifier keys before batch build dialogs.
- **BS:** Enforce minimum left pane width in UI to try to keep group filter visible.
- **OS:** Preserve and maintain reference info for the project's base shape.

## 5.8.0
### New Features:
- **BS (BodySlide):** Expanded Starfield support with Build Morphs output to morph.dat and project settings for the Starfield morph path and morph target shape.
- **Starfield hint:** BodySlide support is not as useful in SF. The in-game morphing with the morph.dat file is better. Using Outfit Studio is enough.
- **BS:** Preview now lives inside the main window, but can be popped out into its own window, or be launched directly from the command line (-preview). See Wiki.
- **BS:** Added an automatic clipping fixer with a strength control for previews and builds.
- **BS:** Added favorites for outfits and presets (star icon button).
- **BS:** Batch-build conflicts can be compared in a 3D preview popup.
- **BS:** Added option to load reference body in preview (for new projects only).
- **BS:** Added "Lock Shape" button in preview to create a slider preset from the currently previewed weight.
- **BS:** Added a way to edit group assignments in existing presets.
- **OS (Outfit Studio):** Expanded Starfield support with internal or external mesh export options and Starfield material and texture preview support.
- **OS:** New automation system with shareable XML scripts, many built-in steps, and headless command-line execution. See https://github.com/ousnius/BodySlide-and-Outfit-Studio/wiki/Automation-Dialog.
- **OS:** Added a clipping-fix tool plus conform-time clipping fixing and smoothing controls.
- **OS:** New weight-copy dialog with preview and bone selection.
- **OS:** Added slider-data location management so data can be inspected and switched between local and external storage.
- **OS:** Added full shader field and shader flag editing, along with broader extra-data editing in shape properties.
- **OS:** Added undo support for shape deletion.
- **OS:** Added project notes saved inside .osp files.
- **OS:** Added XML mask import/export.
- **OS:** Added bone and node editing with transform gizmo with undo/redo support.
- **OS:** Added pose editing with transform gizmo.
- **OS:** Support for loading native HKX poses from Skyrim LE/SE and Fallout 4.
- **OS:** Support for loading ScreenArcherMenu poses from YAML and JSON formats.
- **OS:** New modeling tools: Edge Slide with UV correction, rope selection in UV editor, and UV template export.
- **OS:** New viewport tools: Frame Selected, hover highlighting for shapes in the tree, and per-partition and per-segment visibility toggles.

### Improvements:
- **General:** Added long-path awareness on Windows 10 and 11 when enabled in Windows and improved DPI handling.
- **General:** Made data loading less dependent on the current working directory (Linux).
- **General:** Improved crash logging with stack traces.
- **General:** Improved performance for large slider-data files, conforming, clipping correction, and several rendering paths.
- **BS:** Made the Output Path setting easier to reach and cleaned up preset and group handling in the UI.
- **BS:** Command-line group builds now honor saved Build Selection choices.
- **OS:** Open files into an already running instance.
- **OS:** Improved partition/segment editing behavior for triangle assignment.
- **OS:** Weight-copy now respects masks on reference shape (source).
- **OS:** Highlight bad edges during mesh refinement.
- **OS:** Reduced wireframe z-fighting.
- **OS:** Allow mesh and slider editing in the Bones tab while posing.
- **OS:** Sync pose panel bone selection with active bone.
- **OS:** "Add Project" now keeps added slider data external by default.
- **OS:** Project files (*.osp) now store information about the reference shape used.

### Fixes:
- **BS:** Fixed saved zap choices not always updating correctly.
- **OS:** Fixed several clipping and rendering issues.
- **OS:** Added toggle to make near-plane depth clipping visible for fixing meshes.
- **OS:** Added customizable point rendering behavior (Config.xml gains PointSizeMin/PointSizeMax/PointSizeScale settings).
- **OS:** Fixed smooth weight and mask brush problems on vertices that share the same position.
- **OS:** Fixed slider target-name conflicts and target handling for non-reference shapes.
- **OS:** Fixed lone partition triangles sometimes displaying incorrectly or moving to the wrong partition.
- **OS:** Fixed a crash in the convert dialog when no shapes are available.
- **BS:** Fixed morph files being generated for unintended games.
- **BS:** Fixed morph checkbox visibility, category clearing and stale outfit selection when switching target games.
- **OS:** Use NiStencilProperty for double-sidedness in shape properties on FO3/NV.
- **OS:** Fixed Starfield mesh rotation, bone positioning, and NIF export issues.

### Other Changes:
- Removed 32-bit executables.
- Removed the "x64" suffix from .exe file names. Please update your mod manager shortcuts!
- Updated several third-party libraries.
- Updated German translation. Please help with more languages: https://github.com/ousnius/BodySlide-and-Outfit-Studio/wiki/Localization
- Dev stuff: Modernized the build, packaging, CI, and optional Catch2 test setup.

### Credits:
- DJLegends for work on Starfield support
- SulfurNitride for some fixes and initial Linux improvements
- Gibbed for Fallout 4 and Starfield material and CDB decoding
- MaximusMaxy for Starfield material and CDB code

## 5.7.1
### New Features:
- **General**: Enable Windows DPI awareness in manifest (PerMonitorHighDPIAware).
- **BodySlide**: Added preset filter.
- **BodySlide**: Added buttons to jump to slider categories in the list.
- **BodySlide**: New output conflict dialog with (just) slightly better UX.
- **OS**: Load Reference: Option to not append new sliders that are not already in the list.
- **OS**: Added vertex color picker and mask similar vertex colors.
  - Press 'V' key in bones tab to pick a vertex color from a mesh.
- **OS**: Split edges while holding shift to disable curvature/smoothing.
- **OS**: Added green pencil icon for sliders with data for one of the selected shapes.
- **OS**: Added configurable colors for vertex points in settings.
- **OS**: Added max project history count to config file (attribute "ProjectHistory.maxcount").
### Improvements:
- **General**: Stability and performance improvements.
- **General**: Made default background color setting darker.
- **General**: Updated Chinese translation (@Eyre11)
- **BodySlide**: Auto expand filter group/outfits fields to be wider.
- **OS**: Improve rendering of points on meshes in vertex view. Fade size based on depth.
- **OS**: Fill current shape name in rename/duplicate/separate shape dialogs.
- **OS**: Improved number entry in uniform scale/inflate dialog.
- **OS**: Improved label of Invert X/Y in UV edit.
### Fixes:
- **General**: Fix several Unicode file name and UI issues.
- **OS**: Fixed reference templates with multiple shapes having slider data localized.
- **OS**: Delete shape with identical name on reference load to prevent issues.
- **OS**: Various fixes for renaming shapes with special slider data.
- **OS**: Fixes for pose reset and export when unpresent bones are posed.
- **OS**: Fixed swapping left/right (L/R) bones for meshes without the other bone.
- **OS**: Fixed head part .tri files being exported without slider data for reference shape.
- **OS**: Fixed texture path cleanup with multiple "textures\" occurrences.
- **OS**: Fixed issue with vertex colors on merge/undo for sources without color data.
- **NIF**: Make "Keep zapped shapes" option set "Hidden" flag on shape only (prevent game crashes).
- **NIF**: Fixed child blocks of BSShaderPPLightingProperty/NiMaterialProperty not always being removed.
- **NIF**: Fixed brush collision with mesh after moving a slider.
### Deprecations:
- **OS**: Removed FBX SDX from 32-bit builds of Outfit Studio (support was removed).

## 5.7.0
### New Features:
- **General**: Added support for the new BA2 archive versions of FO4 and SF.
- **BodySlide**: List only outfits with zap options using 'Filter -> Has Zap Options'.
- **BodySlide**: Open the 'ShapeData' folder of the current outfit in file explorer using 'Filter -> Browse outfit folder...'.
- **OS**: Brush settings are now remembered between sessions. A 'Reset' button has been added.
- **OS**: Inflate or deflate a mesh or slider along its normals.
- **OS**: Mask the UV editor selection in the main viewport (select by UV).
- **OS**: Added 'Slider -> Clone Slider' to clone existing sliders.
- **OS**: Added 'Edit -> Disable Normals Calculation' to lock all mesh normals.
  - Unlike 'Lock Normals', this does not lock normals in BodySlide.
  - This option remains active between Outfit Studio sessions (stored in config).
- **OS**: Allow adjustment of the seam smoothing angle for mesh normals on a per-shape basis.
- **OS**: Added project option to keep fully zapped shapes in the BodySlide-built NIF file.
  - Useful when the shape order and count matters, like for retextures using texture sets.
- **OS**: Added project option to prevent writing body morph .tri files when building.
- **OS**: Utilize 'SliderMinimum' and 'SliderMaximum' config settings in Outfit Studio.
- **OS**: Show a gradient on meshes when hovering over a slider while holding the CTRL key.
- **OS**: Support multiple reference data folders for new projects.
  - References with external extra sliders (second data folder) would lose the link to slider data when saved as new projects. This affected The Wasteland Body (TWB).
  - Both data folders are linked to the reference shape in the resulting outfit project now, so the link is not lost.
- **OS**: Partial Starfield support:
  - Import NIF and mesh files (export and skinning not supported).
  - Import/export morph.dat files (custom normals and vertex colors not supported).
  - Searches for mesh files in BA2 archives.
  - No loading of materials or textures.

### Improvements:
- **General**: Enhanced startup performance with faster BSA/BA2 loading.
- **BodySlide**: Enabled multi-selection in the group filter dialog using the spacebar.
- **OS**: Account for gradient masking when conforming to sliders.
  - Lower mask values now blend the old morph with the new one based on the mask factor.
  - This allows partial adjustments or the use of multiple references.
- **OS**: Improved X-mirroring for the move brush on centered vertices.
- **OS**: Multi-select slider checkboxes by holding the Shift key.
- **OS**: Apply posing to unpresent bones when selecting a saved pose.
- **OS**: Improved XYZ mirroring of shapes:
  - Added an option to swap left/right (L/R) bones when mirroring along the X-axis.
  - Mirroring shapes is now included in the undo history.
- **OS**: Retain masks when using 'Shape -> Set Reference'.
- **OS**: Remove empty diffs after using the undiff brush for cleaner slider data.
- **OS**: Set the environment mapping shader flag when changing shader type in shape properties.
- **OS**: Automatically check the 'Show Pose' checkbox when changing poses or values.
- **OS**: Changed the hotkey for deleting sliders from 'Delete' to 'CTRL+Delete'.

### Fixes:
- **General**: Resolved various NIF-related issues with FO76 and older Oblivion files.
- **BodySlide**: Fixed zap toggles of saved zap choices not applying during batch builds.
- **BodySlide**: Prevent headpart/CharGen .tri files from being replaced by body morph files during the build process.
- **OS**: Fixed mesh actions unintentionally adding new data, like vertex colors.
- **OS**: Fixed incorrect shape order when exporting only selected shapes.
- **OS**: Fixed a rare crash in the brush collision code.
- **OS**: Fixed crash when adding shader to geometry types that cannot have a shader.
- **OS**: Fixed locked normal indices (NiIntegersExtraData) being ignored for NiTriShapeData.
- **OS**: Fixed archive blacklisting in Outfit Studio for better startup performance.
- **OS**: Oblivion: Use NiSkinInstance over BSDismemberSkinInstance and hide unused 'Partitions' tab.

## 5.6.3
### New:
- **OS**: Added way to add multiple custom bones in a parent chain at once.
- **OS**: Added "Double Sided" checkbox to shape properties.
- **OS**: Include loaded loose file name in window title.

### Fixes:
- **BodySlide**: Fixed toggles for zaps that are zapped by default.
- **OS**: Fixed OBJ and FBX import preview not rendering (issue with UI framework).
- **OS**: Fixed stuttering in UV editor and import previews.

## 5.6.2
### New:
- **BodySlide**: Added a slider filter to search by name or category.
- **OS**: Allow editing some shape properties for multiple selected shapes.

### Fixes:
- **BodySlide**: Fixed preview not clearing the previous outfit.
- **OS**: Fixed UV editor not rendering anymore (issue with UI framework).

## 5.6.1
### New:
- **BodySlide**: Zap options are now remembered for each outfit (including batch builds).
- **OS**: Implemented disabling of undo history for masking actions (see settings).
- **Rendering**: Perspective view option is now stored in the settings.

### Improvements:
- **OS**: Allow merging geometry with mismatching cut offsets (FO4).
- **OS**: Made color brush respect the current mask.

### Fixes:
- **BodySlide**: Fixed slider names when multiple files are adding to one category.
- **OS**: Fixed slider data corruption when merging sliders with mismatching reference.
- **OS**: Fixed applying a pose causing slight distortion on the mesh.
- **OS**: Fixed loading NiSkinData w/o vertex weights but Num Vertices > 0.
- **OS**: Fixed block pointers sometimes not updating when cloning.
- **OS**: Fixed brush strength of smooth mask brush (shift key).
- **OS**: Fixed slider effect/checkbox not being set when having many sliders.
- **Rendering**: Fixed alpha testing being rendered for all meshes.

### Other Changes:
- Updated Turkish translation. (@predaturk)

## 5.6.0
### New:
- **General**: Added support for NIF file version 155. (@ousnius)
- **General**: Added support for reading material file version 20 (BGSM/BGEM). (@ousnius)
- **OS**: Improved smooth brush algorithms (balanced pair circle+parabola fit). (@sts1skj)
- **OS**: Added special FO4 segment slots to dropdown (pipboy cap = slot 160). (@ousnius)
- **OS**: New feature "Copy Partitions/Segments" from reference shape. (@sts1skj)
- **OS**: Added preview for OBJ/FBX import with new options: (@ousnius)
  - Invert U/V, Scale, Rotate X/Y/Z.
  - Show vertex and triangle counts, red text if too many.
  - Allow deleting single shapes with DEL.
  - Green shape selection highlight in preview.
- **OS**: Added separate translate/rotate/scale dialogs to UV editor. (@ousnius)
- **OS**: New dialog "Symmetrize Vertices" for X-mirroring position, weights and sliders. (@sts1skj)
- **OS**: New feature "Mask Symmetric Vertices" for masking mirrored vertices with identical data. (@sts1skj)
- **OS**: New feature "Mask Symmetric Triangles" for masking mirrored triangles with identical data. (@sts1skj)
- **OS**: New dialog "Check For Bad Bones" that lists inconsistent bone transforms with options for fixing them. (@sts1skj)
- **OS**: New submenu "Bad Bones" in the bone context menu with two options for fixing bad bones. (@sts1skj)
- **OS**: New tool "Move Vertex" for moving/snapping/welding/merging individual vertices. (@sts1skj)
- **OS**: New options for restricting brushes to mesh plane and normal. (@sts1skj)
- **OS**: Mirrored display of brush circle with X-mirror on. (@sts1skj, @ousnius)
- **OS**: Added option to retain weights/sliders in conversion wizard. (@ousnius)

### Improvements:
- **BodySlide**: Improved output label and conflicts popup menu. (@ousnius)
- **OS**: Better brush falloff due to new cubic falloff formula. (@sts1skj)
- **OS**: Added scale to the pose parameters and removed old bone scale slider. (@sts1skj)
- **OS**: Made "Apply Pose To Mesh" undoable. (@sts1skj)
- **OS**: Made "Apply Pose To Mesh" update position diff sliders too. (@sts1skj)
- **OS**: Allow 4 decimals and max value of 10 in brush settings to be entered manually. (@sts1skj, @ousnius)
- **OS**: Prevent switching to segments or partitions tab with multiple meshes selected. (@sts1skj, @ousnius)
- **OS**: Made Mask More/Less, Invert/Clear Mask and Mask Weighted undoable. (@sts1skj, @ousnius)
- **OS**: Made "Show Bones" show posed bones when "Show Pose" is on. (@sts1skj)
- **OS**: Copy ALL shader properties and children with "Copy from shape". (@ousnius)
- **OS**: OBJ Import: Do more to preserve original vertex order. (@sts1skj)
- **OS**: OBJ Import: Correctly handle faces with more than 4 vertices. (@sts1skj)
- **OS**: OBJ Import: Prevent duplication of vertices when normals or UVs are duplicated in the file. (@sts1skj)
- **OS**: OBJ/FBX Import: Added option to update normals when merging data with an existing shape. (@sts1skj)
- **OS**: FBX Import: Split vertices with multiple UVs/normals. (@sts1skj, @ousnius)
- **OS**: Allow resizing New/Load/Save Project and Load Reference dialogs. (@ousnius)
- **OS**: Slight performance improvements while brushing. (@sts1skj, @ousnius)

### Fixes:
- **General**: Various fixes to NIF library (nifly). (@ousnius, @sts1skj)
- **General**: Fixed "no image" texture spreading to meshes that shouldn't have it. (@ousnius)
- **General**: Fixed model space normal map rendering with model rotation. (@ousnius)
- **General**: Fixed some rendering issues with alpha blending. (@ousnius)
- **OS**: Fixed freezes on some systems when ending a brush stroke. (@ousnius)
- **OS**: Fixed undesired shape translation when importing OBJ (mostly FO4). (@sts1skj)
- **OS**: Fixed custom bones not appearing with "Show Bones" on. (@sts1skj)
- **OS**: Fixed incorrect bone display in FO3/NV with "Show Bones" on. (@sts1skj)
- **OS**: Fixed bug where applying/undoing/redoing a mesh edit would trash the masks. (@sts1skj)
- **OS**: Fixed "Connected Only" brush option sometimes unwelding vertices. (@sts1skj)
- **OS**: Fixed rare issue where brushes wouldn't hit vertices that they should hit. (@sts1skj)
- **OS**: Fixed normals flickering in some cases while brushing. (@sts1skj, @ousnius)
- **OS**: Fixed single normals sometimes not recalculating correctly while brushing. (@sts1skj)
- **OS**: Fixed display of weight and mask value in status bar. (@ousnius)
- **OS**: Fixed bug where sometimes high brush strength values do nothing. (@sts1skj)
- **OS**: OBJ Import: Handle negative OBJ vertex/UV/normal indices correctly. (@sts1skj)
- **OS**: FBX Import/Export: Fixed swapping X/Y/Z for normals. (@sts1skj)
- **OS**: Fixed texture set not being created with "Add Shader" in shape properties. (@sts1skj)
- **OS**: Fixed issues with skipping copy weights/conform dialogs in conversion wizard. (@ousnius)
- **OS**: Several fixes/cleanups related to mesh coordinate transforms. (@sts1skj)

### Other Changes:
- **General**: Updated third party libraries (wxWidgets, GLI/GLM, SOIL2, half, Miniball). (@ousnius)
- **OS**: Removed unnecessary "Global Brush Collision" tool option. (@sts1skj, @ousnius)

## 5.5.2
### Fixes:
- **General**: Fixed crash when building/saving some NIF files. (@ousnius)
- **Outfit Studio**: Fixed not being able to reorder shapes (didn't save). (@ousnius)
- **Outfit Studio**: Further improved brush settings popup dismissal. (@ousnius)

## 5.5.1
### Fixes:
- **General**: Fixed language warning on startup. (@ousnius)

## 5.5.0
### Improvements:
- **General**: Performance optimizations and platform updates. (@daz001, @ousnius)
- **General**: Improved loading times of outfits/projects. (@daz001, @ousnius)
- **BodySlide**: Show conflicts for outfits with the same output path. (@Iloei)
- **BodySlide**: Batch Build options with already resolved conflicts are unchecked by default. (@ousnius)
- **BodySlide**: Added (de)selection text field to batch build override dialog. (@ousnius)
- **BodySlide**: Reintroduce regex outfit filtering as an option in the context menu. (@ousnius)
- **BodySlide**: "Save Preset" is now greyed out when there's no changes to sliders. (@ousnius)
- **BodySlide**: Added several hotkeys:
  - F5 = refresh outfit list from disk
  - PgUp = go to previous preset
  - PgDown = go to next preset
  - Ctrl+A = clear search filters
  - Ctrl+PgUp = go to previous outfit
  - Ctrl+PgDown = go to next outfit
  - Ctrl+O = open project in Outfit Studio
  - Ctrl+S = save changes to preset
  - Ctrl+Alt+S = save new preset
  - Ctrl+G = open group manager
  - Ctrl+P = open preview
- **Outfit Studio**: Improve brush settings popup (wider, text fields, better dismiss handling). (@ousnius)
- **Outfit Studio**: Added "Refine Mesh" command for increasing poly count to the shape menu. (@sts1skj)
- **Outfit Studio**: Added "File -> Convert / Replace Reference" wizard. (@daz001)
- **Outfit Studio**: Added import dialog with OSD/TRI files to allow choosing sliders. (@daz001)
- **Outfit Studio**: Added toggle for rendering vertex colors outside of "Colors" tab. (@daz001)
- **Outfit Studio**: Added "Alpha Test" and "Alpha Blend" toggles to the shape properties. (@daz001)
- **Outfit Studio**: Added "Merge Zaps" and "Merge Sliders" options to the Load Reference dialog. (@daz001)
- **Outfit Studio**: Added "Max Value" clamp slider for the vertex alpha brush. (@daz001)

### Fixes:
- **BodySlide**: Fixed changing slider using text field not marking slider as "changed" for builds. (@ousnius)
- **Outfit Studio**: Fixed saving project with subfolders in "SliderSets" (again). (@ousnius)
- **Outfit Studio**: Fixed slider data sometimes being partially lost when merging geometry. (@ousnius)
- **Outfit Studio**: Several fixes for merging sliders. (@daz001, @ousnius)
- **Outfit Studio**: Fixes for vertex collapse tool. (@ousnius)
- **Outfit Studio**: Fixed applying segments with empty segment(s) at the end (FO4). (@ousnius)
- **Outfit Studio**: Fixed order of "Recent Projects" list sometimes being inverted. (@ousnius)

### Other Changes:
- **BodySlide**: Activate rendering of vertex colors by default. (@daz001)
- **Outfit Studio**: Increased size of the shape textures dialog/grid. (@daz001)
- **Outfit Studio**: Improved interpolation of progress bars (@daz001)
- **Outfit Studio**: Disable specular strength field for FO3/NV. (@ousnius)
- **Outfit Studio**: Reduce lighting interpolation artifacts in rendering. (@Candoran2)

## 5.4.2
### Fixes:
- **BodySlide**: Fixed slider data not being applied for "Build" without having opened the preview.
- **Outfit Studio**: Fixed deletion of unused nodes.
- **Outfit Studio**: Fixed crash due to out-of-bounds slider data on certain references.
- **Outfit Studio**: Fixed checks for maximum vertex/triangle counts on OBJ import.
- **Outfit Studio**: Fixed coordinates display of highlighted point (vertex under brush).

## 5.4.1
### Improvements:
- **Outfit Studio**: Improved new brush settings popup. Location is now fixed by default. ESC or Space keys will close it.
- **Outfit Studio**: Added setting for opening brush popup near the mouse cursor.
- **Outfit Studio**: Added shortcuts for deleting vertices (Shift+Del) and separating vertices (Shift+S).
- **Outfit Studio**: Allow editing static shape transform in shape properties.

### Fixes:
- **Outfit Studio**: Fixed .osp location when saving projects with relative paths.
- **Outfit Studio**: Fixed crash when moving cursor too soon after loading project while holding the right mouse button.
- **Outfit Studio**: Fixed loading FO4 meshes with BSClothExtraData blocks.
- **Outfit Studio**: Fixed various issues with the pending changes indicator/dialog.
- **Outfit Studio**: Fixed texture plane in the UV editor.

## 5.4.0
### New Features:
- **General**: Added Oblivion as a target game.
- **Outfit Studio**: Added shortcut 'Ctrl+Space' to enter slider edit mode.
- **Outfit Studio**: Added shortcut 'Ctrl+Mouse Wheel' to quickly move between sliders.
- **Outfit Studio**: Added ability to name and save poses to XML files. Pose files can be shared with others.
- **Outfit Studio**: Store recently loaded projects for quick loading.
- **Outfit Studio**: Added search filter to the bones tab.
- **Outfit Studio**: Added ability to change the camera rotation center (shortcut 'Shift+R').
- **Outfit Studio**: Hold the 'ALT' key and right-click-drag a vertex to make it the camera rotation center.
- **Outfit Studio**: Added "Show Bones" (shortcut 'Shift+B') for rendering active bone connections.
- **Outfit Studio**: Added "solid" conforming mode for small solid parts.

### Improvements:
- **General**: Added French translation by Hana.
- **BodySlide**: Load slider data when preview is opened only (performance improvement).
- **BodySlide CLI**: /gbuild command can now contain multiple group names separated by a comma.
- **BodySlide CLI**: /targetdir was missing the last backslash on Windows (escaping issue).
- **BodySlide CLI**: UI and last active outfit aren't loaded anymore before building via CLI.
- **Outfit Studio**: Redesign brush settings as a popup window (shortcut 'Space' key).
- **Outfit Studio**: Added unsaved changes indicator and warning dialog.
- **Outfit Studio**: Respect mask on reference shape when conforming sliders.
- **Outfit Studio**: Added shortcuts '1' to '5' to the UV editor.
- **Outfit Studio**: Highlight UV seam edges while the UV editor is open.
- **Outfit Studio**: Remember last used standard tool when switching tabs.
- **Outfit Studio**: Added labels showing total and selected shapes bone counts.
- **Outfit Studio**: Added button to open slider properties in slider edit.
- **Outfit Studio**: Added undo/redo buttons to the toolbar.
- **Outfit Studio**: "Move/Rotate/Scale Shape" and moving a vertex with 'V' are now undoable.
- **Outfit Studio**: Added origin selection to "Rotate/Scale Shape" dialogs.
- **Outfit Studio**: "Rotate Shape" dialog can now be used on slider data.
- **Outfit Studio**: Added X/Y/Z mirror to the "Move Shape" dialog.
- **Outfit Studio**: Allow saving to sub dirs of "SliderSets" with the save project dialog.

### Fixes:
- **Outfit Studio**: Fixed rig for FBX exports (orientation = YZX).
- **Outfit Studio**: Fixed some rotations not being rendered correctly.
- **Outfit Studio**: Rendering fixes for alpha blending and culling.
- **Outfit Studio**: Fixed DEL key not working in some text fields.
- **Outfit Studio**: Sync mirror states of the main brushes.
- **Outfit Studio**: Fixed "Move Vertex" function for X axis values in slider edit.
- **Outfit Studio**: Fixed multiple zaps getting created with multiple shapes selected.
- **Outfit Studio**: Fixed "Mask Affected" crash when slider data mismatches vertex count.
- **Outfit Studio**: Prevent using transform tool with non-zero sliders outside of slider edit.
- **Outfit Studio**: Improve handling of seam/lock normals checkboxes for shape multi-select.

### Other Changes:
- **Outfit Studio**: Changed "Show Nodes" shortcut to 'Shift+N'.
- **Outfit Studio**: Changed shape visibility shortcut from 'G' to 'E' and added floor grid shortcut 'G'.
- **Outfit Studio**: Moved "Apply to Mesh" pose button and added more confirmation dialogs.
- **Outfit Studio**: Added confirmation dialogs for unapplied changes in partition/segment tab.

## 5.3.1
### Improvements:
- **General**: Added advanced "Project Path" setting to control where data (projects, presets, ...) is loaded from and saved to.

### Fixes:
- **Outfit Studio**: Fixed modifier keys and capslock not working in certain dialogs.
- **Outfit Studio**: Fixed floor and nodes not showing when loading project too early.

## 5.3.0
### Improvements:
- **General**: Added ability for modders to lock individual normals through a NiIntegersExtradata "LOCKEDNORM" in the NIF.
- **Outfit Studio**: Added slider filter (search bar).
- **Outfit Studio**: Added "Mask Weighted Vertices" for currently selected bones in the bones tab.
- **Outfit Studio**: Added basic node rendering (bones or other NiNodes). Can be activated in the toolbar.
- **Outfit Studio**: Added basic floor rendering. Can be activated in the toolbar.
- **Outfit Studio**: Added button to permanently apply a pose to meshes.
- **Outfit Studio**: Added outfit/project filter to Group Manager and Pack Projects dialogs.
- **Outfit Studio**: Added ability to copy shader/texture paths/alpha properties from another shape in the shape properties.
- **Outfit Studio**: Added warning when vertex or triangle count is exceeded from OBJ/FBX import.
- **Outfit Studio**: Changed OBJ import to always start out as static meshes. Copying or painting weights will make them skinned.
- **Outfit Studio**: Changed each brush to remember its own x-mirror setting now.
- **Outfit Studio**: Changed "Reset Transforms" to apply global transform to prevent some shapes from moving out of place.

### Fixes:
- **Rendering**: Fixed some textures not repeating correctly for coordinates outside of the 0-1 range.
- **Outfit Studio**: Fixed rare crashes while brushing and undoing.
- **Outfit Studio**: Fixed deleting/separating vertices on reference not making slider data local (corrupted sliders).
- **Outfit Studio**: Fixed wrong skinning when exporting only the selected shapes after having deleted vertices.
- **Outfit Studio**: Fixed duplicated/separated shapes not using newly painted or copied weights of the source.
- **Outfit Studio**: Limit normals updating while brushing for better performance on slower systems.
- **Outfit Studio**: Fixed gaps in segments causing the segmentation to be applied incorrectly (FO4).
- **Outfit Studio**: Fixed not being able to enter SSF file path correctly using the keyboard (FO4).
- **Outfit Studio**: Fixed some rare transforms causing invisible meshes.

## 5.2.0
### Improvements:
- **Outfit Studio**: Added axis selection to conform along specific axes only.
- **Outfit Studio**: Added "No Squeeze" conform option.
- **Outfit Studio**: Improved close confirmation of group manager.
- **Outfit Studio**: Added checks for applying geometry transforms for OBJ and FBX import/export.
- **Outfit Studio**: Reference templates that load multiple shapes now keep all slider data external.
- **Outfit Studio**: Don't copy slider data into the project when toggling subindex/dynamic.
- **Outfit Studio**: Allow loading multiple files from the command line.

### Fixes:
- **Outfit Studio**: Fixed inconsistent weighting in-game after using the smooth weight brush without normalization.
- **Outfit Studio**: Fixed custom bone transforms not updating when changing global transform.
- **Outfit Studio**: Improved rounding precision for rendering bone transforms.
- **Outfit Studio**: Fixed shape renaming for FBX import.
- **Outfit Studio**: Fixed rare crashes after deleting shapes.

## 5.1.0
### Improvements:
- **BodySlide**: Remember last choices that were made in the batch build override dialog.
- **BodySlide**: Added double-click functionality to rename a group in the group manager.
- **Outfit Studio**: Implemented "Undiff Brush" to selectively remove slider data (move vertices towards base position).

### Fixes:
- **BodySlide**: Fixed several issues with encoded characters in game data path.
- **BodySlide**: Fixed loading presets from folders with UTF-16 encoded characters.
- **BodySlide**: Fixed command-line group build not having all presets available.
- **Outfit Studio**: Fixed UV editor only saving changes for the currently selected vertices.
- **Outfit Studio**: Fixed crash when changing the shape type of the reference.
- **Outfit Studio**: Fixed close vertices sometimes not welding.

## 5.0.7
### Improvements:
- **Outfit Studio**: Implemented "Copy Geometry" (merging shapes) with error checking (by sts1skj).
- **Outfit Studio**: UV Edit - Added box deselection while holding the Alt key.
- **Outfit Studio**: UV Edit - Added "Invert Selection".
- **Outfit Studio**: UV Edit - Added vertex selection tool (Alt to deselect).
- **Outfit Studio**: UV Edit - Added "Select Less/More" action (A and D keys) for UV islands.
- **Outfit Studio**: Implemented two toolbars and split up the existing tools.
- **Outfit Studio**: Partitions/segments now render as sub meshes for better color indication.
- **Outfit Studio**: Minor frame performance improvements.

### Fixes:
- **Outfit Studio**: Fixed various bugs of Split Edge (by sts1skj).
- **Outfit Studio**: Fixed trimming of FO4 material paths in the shape properties.
- **Outfit Studio**: Fixed crash with static meshes when adding triangles (Split Edge, Flip Edge).
- **Outfit Studio**: Fixed saving meshes with partitions that make use of strips.

## 5.0.6
### Fixes:
- **BodySlide**: Fixed preview crashing for meshes without UVs when using a slider.
- **Outfit Studio**: Fixed UVs and more being lost after vertex deletions for LE.
- **Outfit Studio**: Fixed slider corruption when using Split Edge after loading a reference.
- **Outfit Studio**: Fixed potential crashes when undoing changes (AABB tree data being lost).
- **Outfit Studio**: Fixed several conflicts between the UV editor and the main renderer.

## 5.0.5
### Fixes:
- **BodySlide**: Fixed crash when zapping with preview opened up.
- **Outfit Studio**: Fixed wireframe being affected by alpha treshold.
- **Outfit Studio**: Fixed several crashes when deleting vertices or using the new tools.
- **Outfit Studio**: Fixed X-Mirror not reactivating and its toolbar appearance.

## 5.0.4
### Improvements:
- **Outfit Studio:** Implemented new tools: Collapse Vertex, Flip Edge and Split Edge (see wiki for details) (by sts1skj)
  - Icons for the new tools were provided by Hana
  - Check the wiki for details on the new tools
- **Outfit Studio**: Added wireframe color selection to the settings (by ousnius)
- **Outfit Studio**: Remember last selected reference template and sort them alphabetically (by ousnius)
- **Outfit Studio**: Implemented new coordinates tab in the shape properties (by sts1skj)
- **Outfit Studio**: Copy skin transforms with weights (by sts1skj)
- **Outfit Studio**: Render FO4 skin-to-global transform and removed fake camera offset (by sts1skj)
- **Outfit Studio**: Turned "Delete Unreferenced Nodes" into a manual action (by ousnius)
- **Outfit Studio**: Implemented undo for delete vertices and separate vertices (by sts1skj)
- **Outfit Studio**: Don't delete empty partitions before export anymore (by sts1skj)

### Fixes:
- **General**: Fixed vertex deletion in segments (FO4 CBBE Reduced crash) (by ousnius)
- **Outfit Studio**: Fixed "Invert Selection" in Batch Build not working as intended (by ousnius)
- **Outfit Studio**: Fixed some helper child nodes getting removed (by ousnius)
- **Outfit Studio**: Fixed incorrect behavior of single clicks with the inflate/deflate brush (by sts1skj)

## 5.0.3
- General: Support UTF-16 paths for config files.
- Outfit Studio: Added menu item "Edit -> Remove Skinning" for disabling skinning for all shapes.
- Outfit Studio: Fixed crash when painting weights without having any bone selected.
- Outfit Studio: Fixed FBX import not setting up bones properly.
- Outfit Studio: Fixed crash when importing FBX into an empty project and then unloading it.
- Outfit Studio: Fixed rules for node output and added removal of unused nodes within a hierarchy.
- Outfit Studio: Fixed pose showing outside of bones tab to prevent mesh issues.

## 5.0.2
- Outfit Studio: Fixed weight painting not clamping the weights between 0 and 1 with normalize off.

## 5.0.1
- Outfit Studio: Fixed toolbar toggle buttons.
- Outfit Studio: Fixed transform tool not applying to slider edit.
- Outfit Studio: Added conversion of NiSkinInstance to BSDismemberSkinInstance when applying partitions.
- Outfit Studio: Added "Normalize Weights" checkbox and disabled live normalization by default.

## 5.0.0
- BodySlide: Enabled morphs checkbox for SSE VR (by ousnius)
- BodySlide: Added "Invert Selection" to the batch build context menu (by ousnius)
- BodySlide: Fixed missing UTF-8 conversions for outputting files (by ousnius)
- Outfit Studio: Added save/load of masks under names (not saved to project) (by ousnius)
- Outfit Studio: Added live weight normalization to the weight brushes (by sts1skj)
- Outfit Studio: Added icons to the bones list for toggling bone normalization (by sts1skj)
- Outfit Studio: Added mirrored weighting to a selected (or automatically matched) bone (by sts1skj)
- Outfit Studio: Added posing functionality (bones with parents, no true rig) (by sts1skj)
- Outfit Studio: Added support for editing sliders at any value (by sts1skj)
- Outfit Studio: Added slot selection for FO4 sub segments (by ousnius)
- Outfit Studio: Added some links to the toolbar (by ousnius)
- Outfit Studio: Added "loadAll" attribute to reference template definition files (load all shapes) (by ousnius)
- Outfit Studio: Added shared undo history for base and slider edits (by sts1skj)
- Outfit Studio: Added entering and leaving slider edit being its own undo step (by sts1skj)
- Outfit Studio: Improved smooth brush for better results and more reliability for seams (by sts1skj)
- Outfit Studio: Improved move brush to prevent moving into opposite direction and fixed X-center crossing (by sts1skj)
- Outfit Studio: Improved dialog for adding and editing custom bones (by sts1skj)
- Outfit Studio: Fixed manually entering slider values on Windows (by ousnius)
- Outfit Studio: Fixed sliders doubling on unsetting reference (by sts1skj)
- Outfit Studio: Fixed move brush corrupting slider data in rare cases (by sts1skj)

## 4.9.1
- Outfit Studio: Revert skin transform change and added a new menuitem "Edit -> Reset Transforms" instead.
- Outfit Studio: Updated reference skeletons for SK and SSE to fix wrong finger positioning.
- Outfit Studio: Slider data is now copied when duplicating a shape or setting a reference.
- Outfit Studio: Fixed rare cases where renaming a shape caused a loss of slider data.
- Outfit Studio: Fixed nodes with children but without weights being deleted.
- Outfit Studio: Fixed crash when conforming and copying weights multiple times.
- Outfit Studio: Fixes for converting between BSDynamicTriShape and BSTriShape.
- Outfit Studio: Added tooltips to the toolbar in the UV editor.

## 4.9.0
- BodySlide: Remember last "Build Morphs" selection in the config file.
- Outfit Studio: Added UV editor for manipulating and viewing texture coordinates (Shape -> UV -> Edit...).
- Outfit Studio: Reference templates now load from a folder "RefTemplates", allowing them to be shipped with mods.
- Outfit Studio: Shapes can be converted between BSDynamicTriShape/BSTriShape in the shape properties now.
- Outfit Studio: Don't render the overall skin transform anymore (not rendered in-game).
- Outfit Studio: Zero out root node, shape and overall skin transform for skinned meshes (not rendered in-game).
- Outfit Studio: Support for UTF-16 file paths when loading and saving OBJ files.
- Outfit Studio: Updated reference skeletons for SK and SSE.

## 4.8.0
- General: Now uses absolute paths for everything. The working directory no longer matters, just the .exe location.
- Outfit Studio: New dialog for packing projects up into a folder or archive (File -> Pack Projects).
- Outfit Studio: New conforming dialog with customization options for even movement and range.
- Outfit Studio: Fixed crash when deleting all vertices (no mask).
- Outfit Studio: Further prevent crashes for work after having deleted a shape.
- Outfit Studio: Further prevent crashes that can happen after undo/redo actions.
- Outfit Studio: Fixed crash when creating NiGeometryData without UVs.
- Outfit Studio: Fixed shape mirror not mirroring the normals/tangents as well.
- Outfit Studio: Fixed custom text size compatibility of the "Load Preset" dialog.

## 4.7.4
- General: Fixed multiple bugs of the last version caused by errors in the config storage.
- Outfit Studio: Fixed issues with loading and saving some .tri (head) files.
- Outfit Studio: Added batch export of all sliders to individual OBJ files.

## 4.7.3
- General: Render culling from NiStencilProperty for FO3/NV.
- General: Fixed crash with long strings in NIF files.
- General: Fixed NiPSysData link when saving in a lower version.
- General: Updated third party libraries (SOIL2, TinyXML-2, GLI, GLM, LZ4).
- General: Added Turkish translation by predaturk.
- Outfit Studio: Added import and export of .tri (head) files used by the game (not body morphs).
- Outfit Studio: Always restore previous shape selection and visibility when performing certain actions.
- Outfit Studio: Changed hotkey 'G' to toggle visibility mode of all selected shapes.
- Outfit Studio: Fixed bones being removed from within a hierarchy when saving without reference.
- Outfit Studio: Fixed pivot position not being initialized properly when turning on transform mode.

## 4.7.2
- General: Updated Chinese translation.
- Outfit Studio: Added a highlight to bone names that have weights for the selected shape(s).
- Outfit Studio: Fixed crash when toggling sub indices on a shape.
- Outfit Studio: Fixed crash with invalid meshes when entering slider edit.
- Outfit Studio: Fixed NIF export of selected shapes only.

## 4.7.1
- BodySlide: Added an optional output path setting for builds.
- Outfit Studio: Limit bones per partition to 80 for SSE.
- Outfit Studio: Inject new bone nodes into the right position of the hierarchy.
- Outfit Studio: Fixed crash when adding a shape while in segment mode.
- Outfit Studio: Fixed move and scale menus marking all vertices as modified in slider edit.
- Outfit Studio: Refresh only affected meshes on mirror or UV inversion.

## 4.7.0
- BodySlide: Fixed low weight checkbox of zaps not applying to batch builds.
- BodySlide: Prevent progress bar lockups during batch build.
- Outfit Studio: Added a pivot mode that shows a point that can be moved and makes it the center of mesh operations like rotation and scale.
- Outfit Studio: Added mirroring of meshes on the XYZ axis.
- Outfit Studio: Added 'Add Project' feature that merges shapes and slider data into the current project.
- Outfit Studio: Added new tab 'Colors' for editing vertex colors and vertex alpha when enabled on the shape.

## 4.6.2
- BodySlide: UV morphs now get stored in TRI files for RaceMenu SE in-game morphing.
- Outfit Studio: Prevent the creation of multiple sliders with the same name.

## 4.6.1
- BodySlide: Show 'Build Morphs' checkbox for SSE (RaceMenu BodyMorph).
- Outfit Studio: Mask brush now sets the mask to values of 0 or 1 only (fully unmasked or masked).
- Outfit Studio: Fixed crash by reloading partitions/segments after deleting/separating vertices.
- Outfit Studio: Fixed cursor/brush collision with mesh in certain cases (hidden meshes, multi select).
- Outfit Studio: Fixed not being able to use the mask/weight brush when slider values are set.

## 4.6.0
- BodySlide: Added a button located next to the outfit name for loading a project directly into a new Outfit Studio process.
- BodySlide: Double-clicking entries in the group manager now moves them into or out of the selected group.
- Outfit Studio: Implemented a new "Mask Less/More" feature under the "Tool" menu (hotkeys are A and D) for decreasing or increasing the current mask. This works the same as "Select Less/More" in Blender or "Shrink/Grow" in 3ds Max.
- Outfit Studio: Default values of zaps are now set up with a checkbox in the slider properties dialog, instead of two value fields.
- Outfit Studio: Deleting a slider now clears the slider toggles with it as well. Previously the toggle data was kept.
- Outfit Studio: Fixed OBJ import not loading all types of group setups correctly.
- Outfit Studio: Fixed OBJ import merging vertices by UVs/normals the wrong way. Meshes should keep their hard and smooth edges correctly now.
- Outfit Studio: Fixed issues with importing meshes from OBJ/FBX that exceed max vertex/triangle counts. Instead, an empty mesh is created now.
- Outfit Studio: Fixed crash when exporting OBJ without vertices, UVs or normals.
- Outfit Studio: OBJ export now sets a default smoothing group for loading into Blender.
- Outfit Studio: Implemented a "Shape -> Lock Normals" toggle to keep mesh normals intact during both OS and BS. Outfit Studio makes sure not to smooth normals before they can be locked. This is useful for meshes where keeping custom normals is absolutely needed. This toggle is saved to the project files.
- Outfit Studio: Fixed smooth/lock normals toggles not saving if a shape had no slider data to it.
- Outfit Studio: Fixed partitions tab showing colors of last selected bone.
- Outfit Studio: Eliminated the need for blank skeletons (the SkeletonBlank_*.nif files).
- Outfit Studio: Fixed loading OBJ into empty project adding bogus bones. These came from the blank skeleton files that were loaded into the project behind the hood.

## 4.5.4
- General: Added Skyrim VR as a target game.
- General: Fixed more Unicode conversion issues with shape and slider names.
- General: Fixed crash when choosing FO4 cloth data with Unicode characters in the path.
- General: Fixed warning with certain monitors due to ICC profile present in the OutfitStudio.png file.
- Outfit Studio: Fill default partition correctly when creating skinning.
- Outfit Studio: Fixes for bones/weights sometimes not being deleted from the NIF correctly.

## 4.5.3
- General: Fixed slider data not loading when one of multiple OSD files isn't found.
- Outfit Studio: Fixed 'merge sliders' sometimes not adding slider data when loading references.
- Outfit Studio: Fixed enter key activating the offset button in the 'Move Shape' dialog.
- Outfit Studio: Fixed crash when adding or cloning shapes without shader properties.

## 4.5.2
- General: Fixed issue that caused new textures to not appear (changing material or texture).
- General: Strings from NIFs above the maximum string index are loaded properly now.
- General: Enabled crash reports that go to the temp folder.
- Outfit Studio: Creating skinning now adds a default partition (FO3NV/SK/SSE).
- Outfit Studio: "Clear Slider Data" and "Delete Slider" now works on all selected sliders.
- Outfit Studio: Allow hidden sliders to be selected for toggles in the slider properties.
- Outfit Studio: Added Behemoth segment types to the selection (FO4).

## 4.5.1
- General: Fixed depth buffer not working in previews for AMD drivers (bug in v4.5).

## 4.5
- General: Separated BodySlide and Outfit Studio into their own executable files.
- General: Fix attempt for previews not working for users with HDR monitors.
- General: Better handling for NIF files without any root nodes.
- BodySlide: Presets without any changed sliders now load and save regardless.
- BodySlide: "Refresh Outfits" now reloads the currently active outfit as well.
- Outfit Studio: .osp and .nif files can be loaded directly into OS now ("Open With" in Windows Explorer).
- Outfit Studio: Reload shader/materials/textures when closing the shape properties dialog.
- Outfit Studio: Allow toggling the visibility state of multiple selected shapes at once.
- Outfit Studio: NiFloatExtraData blocks can be edited and added in the shape properties now.
- Outfit Studio: Don't refresh shape list when deleting vertices or inverting UVs anymore.
- Outfit Studio: Ignore vertex weights of 0.0 when loading NIFs using NiSkinData (FO3NV/SK/SSE).

## 4.4.2
- General: Fixed crash when attempting to load sliders without actual data.
- BodySlide: Outfit and preset selection is now sorted by alphabet instead of per file.
- Outfit Studio: Changed "Set Base Shape" to also apply to the base shape itself and keep slider data.
- Outfit Studio: Fixed segment type selection in the segments tab (FO4).
- Outfit Studio: Fixed default partition for OBJ import of NiTriShape (Oldrim, FO3NV).

## 4.4.1
- General: Added FO4 VR as a target game entry.
- General: Improved rendering performance by reducing string operations.
- General: Slider data (e.g. Load Project) loads two times as fast now.
- General: Textures from BA2 archives are now decompressed 25 times as fast as before (FO4).
- General: The "Specular" flag in material files is now properly read for rendering (FO4).
- General: Fixed handling for NIF files without a root node at index 0.
- General: Mesh normals are removed from NIFs with model space maps instead of ones skin tint now.
- General: Fixed shape order for rigged FO3/NV meshes (FO3/NV).
- General: Fixed partition flags for FO3/NV meat caps (FO3/NV).
- General: Files with names that use UTF-16 characters can now be loaded.
- General: All XML files are now saved and loaded with UTF-8 encoding.
- IMPORTANT: Files with encoding that isn't UTF-8 HAVE TO be re-encoded to UTF-8 manually using Notepad++. This is often the case for files that include Chinese characters and were saved on Chinese computers. Starting now, future saved files will all be in UTF-8 by default.
- Outfit Studio: Added proper list of segment names to segments tab (FO4).
- Outfit Studio: Added new shortcut CTRL+E for "Export NIF".
- Outfit Studio: Added new shortcut CTRL+ALT+E for "Export NIF with reference".
- Outfit Studio: "Unweighted Vertices" dialog now says which shapes are affected.
- Outfit Studio: Duplicating a shape now selects the new shape.
- Outfit Studio: Now shows an error when trying to copy weights without a reference.

## 4.4
- General: Invalid triangles in NIF files are now removed on load.
- General: The "Smooth Seam Normals" toggle is now stored in project files.
- General: Reduced the mesh color variation brightness with textures turned off.
- General: Fixed alpha blending for the alpha value in shaders.
- General: Fixed loading material files not beginning with "materials" (FO4).
- General: Uncompressed general (GNRL) BA2 archives can now be loaded (FO4).
- General: BC4 and SRGB DDS texture files can now be loaded from DX10 BA2 archives (FO4).
- BodySlide: Added button to delete single entries from project/preset files.
- BodySlide: Note that deleting entries won't delete their NIF or OSD files.
- BodySlide: Added a save prompt to the group manager.
- Outfit Studio: Now always keeps all slider data when renaming shapes.
- Outfit Studio: Added the current project name to the window title.
- Outfit Studio: Automatically create skinning when copying weights to static meshes.
- Outfit Studio: Refactored the way the weight brush operates and fixed weight cache.
- Outfit Studio: Fixed bone/weight assignment for new bone entries.
- Outfit Studio: FBX import uses the bone transforms of the current reference shape now.
- Outfit Studio: NiTriStrips(Data) blocks are always converted to NiTriShape(Data) now.
- Outfit Studio: Fixed a few crash issues with NiTriStrips(Data) with this conversion.
- Outfit Studio: Fixed crash when dropping invalid files onto sliders.
- Outfit Studio: Fixed crash when dragging the visible icon instead of the shape entry.
- Outfit Studio: Fixed triangle order for OBJ slider import with certain meshes.
- Outfit Studio: Renaming shapes doesn't drop the loaded textures any longer.

## 4.3.4
- General: NIF files now have their blocks sorted correctly (nodes before shapes).
- Outfit Studio: Fixed crash when using connected-only mode of brushes and more.
- Outfit Studio: Fixed crash when setting reference after renaming it.

## 4.3.3
- Outfit Studio: Fixed conforming not working on shapes that have transforms (bug in 4.3.2).
- Outfit Studio: Fixed crash when toggling Sub Index in the shape properties.

## 4.3.2
- General: All new shaders for FO4 that support normal, specular, glowmaps and more.
- General: Added cubemap/environment map rendering and soft lighting for all games.
- General: Fixed alpha channel of BC7 texture files not rendering due to third party library.
- General: Added 16x MSAA as the default (previously 8x). Fallbacks of 8x/4x/no AA still exist.
- General: Node and shape transforms are now used in the renderer, mostly useful for static meshes.
- General: Fixed a bug where closing the preview broke the OS rendering or viceversa.
- Outfit Studio: Fixed crash when entering slider edit after "Make Conversion Reference".
- Outfit Studio: Fixed crash when clearing project while partitions tab is active.
- Outfit Studio: Duplicating a shape now keeps the same parent within the same NIF.
- Outfit Studio: Meshes in OBJ files with both group and object aren't loaded twice anymore.
- Outfit Studio: FBX import now finds meshes that aren't under the root node of the file.
- Outfit Studio: Prevent unnecessary normals on SK/SSE face tinted meshes after export.
- Outfit Studio: Clear parallax texture paths and flags for SSE optimization.
- Misc: Filled the blacklist of BSA archives for FO3 and FONV in the config.
- Misc: Lots of code refactoring for stability improvements.

## 4.3.1
- General: Fixed handling of block pointers, which could corrupt links in NIF files.
- General: Make triangle deletion for NiTriShapeData/NiTriStripsData work again, which caused crashes (Oldrim, FO3NV).

## 4.3
- General: Added a customizable renderer background color to the settings.
- General: Fixed triangle deletion (e.g. zaps) for SSE.
- General: Reset BSMeshLODTriShape to a default LOD size after removing triangles (FO4).
- General: Increased far clip distance from 100 to 1000 for rendering larger meshes (matches Blender default).
- General: Lots of code refactoring with stability improvements.
- BodySlide: Last preview window position and size is now stored in the config file.
- BodySlide: Fixed already default slider values being saved to presets regardless.
- BodySlide: Allow extended selection for the checkboxes in the batch build and settings dialogs.
- Outfit Studio: Pressing the DEL key lets you delete a slider currently in edit mode.
- Outfit Studio: Renaming both shapes and sliders now keeps all slider data intact.
- Outfit Studio: Loading existing projects now keeps the original shape order including reference.
- Outfit Studio: Added 'Sub Index' toggle between BSTriShape and BSSubIndexTriShape (FO4).
- Outfit Studio: Fixed crash when choosing a single texture in the 'Load Outfit' dialog.
- Outfit Studio: Fixed loading of loose texture files after assigning them in the shape properties.
- Outfit Studio: Now always zeroes all sliders before applying a loaded preset.
- Outfit Studio: Increased scroll rate of the slider view.
- Outfit Studio: Current width of the slider panel is stored in the config now.

## 4.2.3
- General: Updated Chinese and German translations.
- General: Fixed vertex deletion for SSE meshes.
- General: Disabled loading the BA2 archives of the FO4 texture pack. You can enable it in the settings.
- BodySlide: Fixed zap toggle feature for Skyrim and SSE.
- Outfit Studio: Fixed OBJ export for faces with and without UV maps.
- Outfit Studio: Now keeps previously local slider data when merging references.
- Outfit Studio: Remove empty skin partitions when applying them.
- Outfit Studio: Fixed skin partitions when exporting only right-click-selected shapes to NIF.
- Outfit Studio: Fixed error message on OBJ export with one shape (just the message appeared wrong).

## 4.2.2
- General: Implemented a language selection in the settings dialog.
- General: Fixed meshes with connect points getting corrupted on save in both BS and OS (FO4).
- Outfit Studio: Added 'Delete Vertices' feature for deleting unmasked vertices directly in OS.
- For BodySlide projects that need parts of the body removed, a zap is still the preferred non-destructible method.
- Outfit Studio: Added 'Separate Vertices' feature for splitting up one shape into two using a mask.
- Outfit Studio: 'File -> Import -> From NIF/OBJ/FBX...' can import multiple files at once now.
- Outfit Studio: 'File -> Export -> To NIF/OBJ/FBX...' now export all shapes of the project into one file.
- Outfit Studio: You can now export only the currently selected shapes to one NIF/OBJ/FBX file via right-click.
- Outfit Studio: 'Merge sliders' when loading a ref now works as intended (replaces ref, adds sliders).
- Outfit Studio: Allow unsetting or directly deleting the reference shape.
- Outfit Studio: Added 'File -> Unload Project' menu item.
- Outfit Studio: Duplicating a shape now also copies its controllers and interpolators with it.
- Outfit Studio: Any unreferenced blocks are now deleted on NIF export.
- Outfit Studio: Handle NiSkinData properly when it has vertex weights turned off.
- Outfit Studio: Fixed some triangle index comparisons when updating skin partitions or segments.
- Outfit Studio: Meshes can now be changed to full precision even without having normals/tangents (FO4).
- Outfit Studio: Fixed a visual bug where deleted shapes would stay visible until the next frame.

## 4.2.1
- General: Fixed crash when loading textures in the ATI2 format (often FO4 normal maps).
- General: Fixed invisibility issues in the rendering for AMD drivers by temporarily disabling cubemaps.
- General: Fixed some buffer issues when loading textures from BSA archives (SK).
- General: Fixed wrong rendering when adding a new mesh while textures or lighting were disabled.
- BodySlide: Now sets the consistency type to mutable for all meshes built with morphs enabled (SK).

## 4.2
- General: Rewritten all shaders to make use of normal and specular maps for a more accurate and detailed preview.
- General: New lighting with three directional lights, one frontal light and an ambient factor.
- General: Only Skyrim preview renders normal and specular maps right now. FO4 has the new lights.
- General: Improved alpha rendering. The blending/testing modes and threshold are now taken into account.
- General: UV offset/scale properties are now taken into account in the shaders.
- General: Fixed crash related to NiTriStripsData when calculating normals.
- Outfit Studio: Fixed copying extra data and collision references properly when copying a shape.
- Outfit Studio: Increased size of the "Load Preset" dialog and made it re-sizable.
- Outfit Studio: Fixed crash for meshes without vertices/triangles.
- Outfit Studio: Fixed minor issue related to NIF files of versions prior to SK.

## 4.1.3
- General: Fixed texture path correction for some very rare cases.
- General: Improved quality of normal smoothing on meshes. Not customizable just yet.
- BodySlide: Made group selection in the group manager more clear (disabling panels).
- Outfit Studio: Improved SK -> SSE NIF optimization stability.
- Outfit Studio: Duplicating a shape is faster now when there are many loaded.

## 4.1.2
- BodySlide: Fixed batch build causing texture coordinates to go crazy after v4.1.1.
- BodySlide: Fixed activating zaps causing a crash after v4.1.1.

## 4.1.1
- BodySlide: Ungrouped sets now show all presets instead of no presets. You should still create proper groups, though!
- Outfit Studio: Added UV slider/zap functionality. Diffs are created via OBJ import after a slider was set to UV mode. Instead of morphing the geometry, they move the texture coordinates.
- Outfit Studio: Fixed loading of custom references that were created using existing references.
- Outfit Studio: Minor NIF format fixes.

## 4.1
- Outfit Studio: Bone weights for FO4 and SSE meshes are now normalized more accurately.
- Outfit Studio: Added SSE optimization for NIF files. A dialog will ask you to convert them.
- Outfit Studio: Fixed partition painting for SSE.
- Outfit Studio: Stability and performance improvements.

## 4.0
- General: Skyrim Special Edition support!
- General: Support for NIF meshes and BSA archives of SSE.
- General: Show a target game selection dialog the first time you launch the program.
- Outfit Studio: OBJ/FBX import now creates default partitions for the body slot (FO3NV/SK).
- Outfit Studio: Improved handling of skin transforms and creating new bone bounding spheres.
- Outfit Studio: Allow dragging and dropping multiple files into the frame at once.
- Outfit Studio: Show warning if the version of the loaded NIF doesn't match the target game.
- Outfit Studio: Changed skeleton root from "NPC" to "NPC Root [Root]" for Skyrim.
- Outfit Studio: Removed "File -> Apply Overall Skin Transform" menu item, not needed anymore.
- Outfit Studio: When saving a project, remove _0 and _1 from default target file name for SK.
- Outfit Studio: Moved reference templates from the Config.xml to a new RefTemplates.xml file.
- Outfit Studio: Copying weights now ignores masked vertices and they keep their old weights.
- Outfit Studio: Enabling vertex edit doesn't cause non-existent clipping to appear anymore.
- Outfit Studio: Updated reference skeletons for all games.

## 3.8
- General: Complete rewrite of the renderer to make use of modern techniques.
- BodySlide: Removed multi-threaded batch build for the 32-bit executable. Only 64-bit now.
- Outfit Studio: Vastly improved the quality of the bone weight copy (see below).
- Outfit Studio: Added a weight copy options dialog and improved the default values.
- Outfit Studio: Added new knobs for scaling to the transform tool, both uniform and not.
- Outfit Studio: The S key doesn't scale shapes while the transform tool is active anymore.
- Outfit Studio: Improved segment painting performance.
- Outfit Studio: Manually deleting a slider now removes its data as well.
- Outfit Studio: Fixed BSSkin::Instance target reference not being set properly (FO4).
- Outfit Studio: Default consistency type when importing OBJ/FBX is mutable now (FO3NV/SK).
- Outfit Studio: Fixed multiple issues with BSFadeNode roots in NIF files.

## 3.7.5
- General: Updated Chinese and German translations.
- General: Updated wxWidgets, GLI and TinyXML-2 libraries.
- BodySlide: Skin partition slots weren't removed correctly after a full zap of one (FO3NV/SK).
- BodySlide: Group manager now has a Close button instead of OK and Cancel buttons.
- Outfit Studio: Skin partitions are now triangulated if they were stripified (crash fix, FO3NV/SK).
- Outfit Studio: Extra Data tab of the shape properties now has a working scrollbar.

## 3.7.4
- BodySlide: Skin partition flags are now updated after zaps (FO3NV/SK).
- Outfit Studio: Added feature to toggle zaps based on other zaps (see slider properties).
- Outfit Studio: Removed maximum bones per skin partition (only SK).
- Outfit Studio: Conforming shapes to sliders doesn't affect zaps anymore.
- Outfit Studio: Prevent selecting or brushing on shapes set to be invisible.

## 3.7.3
- General: Improved visibility of the lines in wireframe mode.
- Outfit Studio: Added "Partitions" tab that lets you add, delete and edit skin partitions (FO3NV/SK).
- Outfit Studio: Removed "Build Skin Partitions" menu item. This is done with the "Skinned" checkbox now.
- Outfit Studio: Fixed string issue with some block types that could potentially break the NIF.
- Outfit Studio: Fixed undo and redo functionality and changed redo hotkey to Ctrl+Y.
- Outfit Studio: Added "FBX Import Options" dialog, currently with "Invert U" and "Invert V".
- Outfit Studio: You can now apply shape scaling to sliders as well.
- Outfit Studio: Fixed a bug with segments that had more than 65535 triangles (FO4).
- Outfit Studio: Fixed crash when loading a new shape while a bone is selected.

## 3.7.2
- BodySlide: Prevent crash by limiting batch build with 32-bit executable to 2 CPU threads.
- BodySlide: Delete matching .tri files when building without morphs enabled.
- BodySlide: Fixed .tri morphs link for low weight NIF of Skyrim batch builds.
- Outfit Studio: Prevent selecting other shapes while a brush is active.
- Outfit Studio: Fixed crash when attempting to calculate tangents for shapes without UVs.

## 3.7.1
- General: Fixed shader initialization for some graphics drivers.
- Outfit Studio: Fixed a bug that could create invalid string references.

## 3.7
- General: Loose material files now have priority over the ones in archives.
- General: Updated Chinese and German translations.
- BodySlide: Enabled morphs checkbox for FO4 (.tri morph files for use in-game).
- BodySlide: Implemented an improved override selection dialog for batch building.
- BodySlide: Heavily improved the batch build speed and made it multi-threaded.
- BodySlide: Now closes after a command-line group build has been completed.
- Outfit Studio: Implemented the new "Segments" tab for painting FO4 segmentation.
- Outfit Studio: Implemented material file chooser dialog for the shape properties.
- Outfit Studio: Implemented a feature to directy export/import OSD files of projects.
- Outfit Studio: Implemented improved algorithm for calculating bounding spheres.
- Outfit Studio: Mesh bounding spheres are always being updated now.
- Outfit Studio: Fixed multiple issues with the weight brush and bone scale preview.
- Outfit Studio: Fixed a bug where brush actions would happen without hitting a shape.
- Outfit Studio: Fixed crash when loading bone data with empty references.
- Outfit Studio: Slightly lowered the default focus of the mask brush by a bit.

## 3.6
- General: Moved resource files, shaders and images into new folder structures.
- Outfit Studio: Shapes can now be scaled in a non-uniform way (XYZ separately).
- Outfit Studio: Fixed deletion of NiSkinInstances and shader controllers.
- Outfit Studio: Fixed crash when looking for a bone that doesn't exist in the NIF.
- Outfit Studio: Vastly improved performance when moving sliders with many shapes.

## 3.5
- General: Added support for loading language catalogues from "lang\<lang>\BodySlide.mo".
- General: You can enable the translation for your system language in the settings dialog if available.
- General: Added German translation.
- General: Added Chinese translation.
- General: Fixed UTF8 naming issues for outfits, presets and sliders.
- Outfit Studio: Added new option to the shape geometry properties to enable/disable skinning.
- Outfit Studio: Unweighted vertices warning doesn't appear for unskinned shapes anymore.
- Outfit Studio: Unused NiNodes of bones are now removed from the NIF upon deletion.
- Outfit Studio: Added "Slider -> Mask Affected Vertices" feature
- Outfit Studio: Added "Shape -> Update Bounding Sphere" feature to calculate center and radius of shapes.
- Outfit Studio: Added UV updating option to FBX and OBJ import for existing shapes.
- Outfit Studio: Fixed some references being loaded with multiple shapes instead of one.
- Outfit Studio: Improved tangent/bitangent quality for Skyrim.
- Outfit Studio: Fixed rendering way too often when using the weight brush.
- Outfit Studio: Fixed crash when loading a new project while transform mode is enabled.

## 3.4
- General: Fixed OpenGL contexts not being compatible with some drivers.
- General: Minimizing BodySlide does not minimize Outfit Studio anymore.
- General: Updated the FO4 Maya bone fix script.
- BodySlide: Added command-line arguments for building groups on launch.
  - Example usage: BodySlide.exe -gbuild "CBBE Vanilla Outfits" -p "CBBE Curvy" -t "C:\temp\\"
- Outfit Studio: Added a vertex selection mode for modifying the current mask.
- Outfit Studio: Transform (and vertex) mode can (now) be used in combination with any brush.
- Outfit Studio: Parts of the transform tool the mouse hovers over are now highlighted.
- Outfit Studio: Added hotkeys "Q" for vertex selection and "F" for transform mode.
- Outfit Studio: The size of the transform tool now changes dynamically with the camera zoom.
- Outfit Studio: Added "Full Precision" geometry check box to the shape properties for FO4.
- Outfit Studio: Added "NiIntegerExtraData" to the extra data tab of the shape properties.
- Outfit Studio: Fixed the splitter panels being resized wrongly along the frame.

## 3.3
- General: Changing settings now reloads archives properly.
- General: Changing the target game now recommends a default skeleton.
- General: The settings dialog can't be opened while Outfit Studio is active anymore.
- General: Stopped the texture pools of BS and OS conflicting with each other (black textures).
- General: Fixed crash when clicking both the left and right mouse button at the same time.
- General: Added Maya scripts for fixing the rig of FBX exports to the "res" folder.
- General: The 3D views now load/generate mipmaps to reduce texture artifacts.
- General: The 3D views can now load all texture compression formats (DXT1-5, BC1-7).
- General: Fixed Z-Buffer for the 3D views, which appeared as clipping, even though there was none.
- General: Fixed color profile warnings in the log.
- Outfit Studio: Added a transform tool (3D widget) to move/rotate shapes more easily.
- Outfit Studio: Holding down S key and scrolling while the transform tool is active will scale shapes.
- Outfit Studio: Added "Shape -> UV -> Invert X/Y" feature.
- Outfit Studio: Material file paths for FO4 can now be edited in the shape properties.
- Outfit Studio: Fixed FO4 crash that could happen for some zapped shapes.
- Outfit Studio: Added support for a few more block types (mostly for statics).
- Outfit Studio: Added "File -> Import -> Import NIF" feature.
- Outfit Studio: Added menu items to import/export BSClothExtraData blocks to HKX files.
- Outfit Studio: Added "Save Preset" feature to OS.
- Outfit Studio: Added "Remove Bone From Selected" feature to bone context menu.
- Outfit Studio: Fixed weighting not staying on a shape if it wasn't weighted to the bone before.
- Outfit Studio: Made bone context menu work without having to click on the name of a bone.
- Outfit Studio: Made it possible to add a custom bone to the project that's not in the ref skeleton.
- Outfit Studio: Fixed weighting colors only showing for the active shape, not all selected shapes.
- Outfit Studio: Fixed FBX import/export ignoring bones that aren't in the reference skeleton.
- Outfit Studio: Fixed crash for FBX import/export for shapes without normals or UVs.
- Outfit Studio: Double-clicking on a shape now opens its shape properties dialog.
- Outfit Studio: Stopped the RGB FaceGen shader flag from being a default for OBJ/FBX imports.
- Outfit Studio: Fixed "Save Project As" dialog not showing the loaded game data path for upper-case paths.
- Outfit Studio: Now saves the last size of the slider panel to the config file.
- Outfit Studio: Improved cursor/brush stroke performance.
- Outfit Studio: Fixed bone scaling preview for Skyrim.
- Outfit Studio: Fixed window parenting of some message boxes.

## 3.2
- General: Made the updating of mesh normals asynchronous for brush strokes and in the preview.
- General: Fixed crash when attempting to load certain material files.
- General: All text should now be readable with Windows font scaling or themes.
- BodySlide: Fixed preview not reloading properly if the NIF stayed the same but was zapped.
- Outfit Studio: You can now select and edit multiple shapes at the same time with brushes.
- Outfit Studio: Added a new toggle "Global Brush Collision" for toggling active/selected meshes collision.
- Outfit Studio: NiExtraData blocks can now be edited in the shape properties (NiStringExtraData for now).
- Outfit Studio: Fixed "Load Project" not setting the reference shape properly for non-external references.
- Outfit Studio: Loading old .xml projects now adjusts the slider set file name to .osp automatically.
- Outfit Studio: Fixed slider data imports for FO4 sometimes introducing noise due to lower precision.
- Outfit Studio: Fixed various issues/crashes with the faces section of the OBJ import.
- Outfit Studio: Fixed OBJ/FBX import and FBX export for FO3NV.
- Outfit Studio: Renamed/shortened a few menu items.

## 3.1c
- General: Fixed the loading of loose material files that aren't in BA2 archives.
- General: Added toggle for the batch build override dialog to the settings.
- BodySlide: Added additional mouse camera controls to the preview window.
- Outfit Studio: Exporting slider data to OBJ works as intended again now.
- Outfit Studio: Fixed OBJ import crash because of #comments in the faces section.
- Outfit Studio: Fixed OBJ import not loading triangles properly for some faces sections.
- Outfit Studio: Fixed BSSkinInstance target reference for OBJ/FBX import.

## 3.1b
- General: Now saves the last window state to the config file (maximized window or not).
- BodySlide: Batch building now notifies you of any overrides and asks you which one to build.
- BodySlide: Renamed "Save Preset" button to "Save Preset As...".
- BodySlide: Added new button "Save Preset" that transfers the changed slider values to the preset file.
- BodySlide: Fixed preset drop down selection after saving a new preset to file.
- BodySlide: Now immediately updates the normals when opening a new preview.
- BodySlide: Now immediately activates zaps from presets in the preview.
- Outfit Studio: Added new hotkeys for the view modes (Shift+1 to 5).
- Outfit Studio: Added two buttons to the tool bar: "X-Mirror and "Edit Connected Only".
- Outfit Studio: Fixed BSEffectShaderProperty export.
- Outfit Studio: Now allows multiple BSClothExtraData to be selected for export at once.
- Outfit Studio: Fixed crash when attempting to edit a slider after swapping between projects.
- Outfit Studio: Fixed slider edit mode not closing after swapping between projects.
- Outfit Studio: Fixed name copying for alpha properties.
- Outfit Studio: Fixed crash when copying weights while there are no bones loaded.

## 3.1a
- General: Fixed crash for a very specific type of .BSA archive (empty folder name).
- General: Added a warning that shows if there's no read/write permission for the game data path.
- General: Fixed log output for fatal and unhandled exceptions, properly lock the program thread.

## 3.1
- BodySlide: Slider categories are now sorted by order, not by alphabet.
- Outfit Studio: Fixed crash when saving a project without sliders or shapes loaded.
- Outfit Studio: Removed "Apply the shape changes?" dialog and always apply immediately.
- Outfit Studio: Fixed various bugs with adding bones to a project through the UI.
- Outfit Studio: Weights of bones not present in the ref. skeleton can now be viewed and edited.
- Outfit Studio: Fixed NiNode alignment for meshes will a full skeleton hierarchy (Skyrim HDT PE).
- Outfit Studio: Fixed FBX import/export for Skyrim as the target game.
- Outfit Studio: Fixed shader name and wet material reference copying.
- Outfit Studio: Fixed various .OBJ bugs.
  - Fixed loading OBJs that don't have an object name in them.
  - Fixed OBJs without UVs crashing FO4 shape creation.
  - "template/OutfitTemplate_Wet.bgsm" is the default wet shader now.
  - Don't link any default material .bgsm to the shader name yet.

## 3.0a
- General: Now looks for material files (BGSM/BGEM) and loads their diffuse textures.
- General: Fixed NIF corruption if the root children contained an empty reference.
- General: Fixed camera panning for a certain zoom level.
- BodySlide: Fixed zaps not being updated properly in the preview while it's open.
- Outfit Studio: Added selection for which BSClothExtraData to use on export/save.
- Outfit Studio: Updated BSEffectShaderProperty support.
- Outfit Studio: Fixed copying of NiAlphaProperty values.
- Outfit Studio: Fixed weight brush when a dialog box appeared while holding ALT.
- Outfit Studio: Removed progress dialog and added a progress bar instead.
- Outfit Studio: Now refreshes the outfit list in BodySlide automatically when saving a new project.
- Outfit Studio: Fixed absolute paths for Shape Data Folder in Save As dialog.
- Outfit Studio: Cleaned up the New Project, Load Reference and Load Outfit dialogs.

## 3.0
- General: Fallout 4 support!
- General: Support for loading textures from BA2 archives.
- General: Added 64-bit executable build.
- General: Added archive selection and more improvements to the settings dialog.
- General: New file formats .osp and .osd:
  - .osp files contain the slider sets/projects (XML format).
  - .osd files contain the slider data merged into one file (binary format).
- BodySlide: Sliders now have a separate display name stored in the category file(s).
- Outfit Studio: Added FBX import and export support (Autodesk FBX SDK).
- Outfit Studio: Added drag and drop support for NIF, FBX and OBJ files.
- Outfit Studio: Added drag and drop support for BSD and OBJ slider files.
  - Drop on a slider to update it or hold the CTRL key to create a new slider.

## 2.8d
- BodySlide: Fixed preview window update when using certain zaps.
- Outfit Studio: Fixed bug of v2.8c when loading the weighting.

## 2.8c
- General: Added logging functionality.
- General: Starting this version, the program is now licensed under the GPLv3+.
- BodySlide: Fixed layout bugs for single-weighted sets (slider frame and preview window).
- Outfit Studio: Merged reference shape and outfit shapes list into the same tree.
- Outfit Studio: The reference shape is highlighted with bold, green text now.
- Outfit Studio: Shapes can now be reordered in the list with a drag and drop.
- Outfit Studio: Exported NIF files now have their shapes in the same order as Outfit Studio.
- Outfit Studio: Added transparency settings to the shape properties dialog.
- Outfit Studio: Added menu item to set a new reference shape.

## 2.8b
- BodySlide: Fixed Group Manager using old groups or not saving in some cases.
- Outfit Studio: Added "Export Slider Data -> Export OBJ" feature (previously .BSD only).

## 2.8a
- BodySlide: Now shortly renders an empty preview when switching sets.
- Outfit Studio: Fixed TRI morphs import for unpacked TRI files (such as SAM).

## 2.8
- BodySlide: Merged preview windows and added a weight slider.
- BodySlide: Now updates preview window when switching sets, instead of closing it.
- BodySlide: Slightly reduced memory and video memory usage.
- Outfit Studio: Added a new properties dialog for shapes, currently for shader/texture editing (WIP).
  - Shader type, specular color/strength/power, emissive color/multiplier and texture paths.
- Outfit Studio: Fixed loading projects with externally referenced shape data.
- Outfit Studio: Fixed "Save Project As" sometimes removing textures and/or masks.
- Outfit Studio: Fixed zapping sometimes causing TRI morphs to not link to a shape properly.
- Outfit Studio: Fixed OBJ shape import applying wrong transform matrix.

## 2.7h
- General: Lots of under-the-hood code refactoring.
- Outfit Studio: Support for BSEffectShaderProperty and various shader animation controllers.

## 2.7g
- General: Fixed texture paths with backslash at the very front.
- Outfit Studio: Fixed outfit name not updating after the project has been saved under a new name.
- Outfit Studio: Added hotkey (F2) for renaming shapes. Changed deleting shapes from CTRL+Del to Del.

## 2.7f
- BodySlide: Batch building now uses the currently active slider values as well.
- BodySlide: Fixed copy slider values buttons affecting hidden sliders.
- BodySlide: The preview is now equally as bright as the Outfit Studio view.
- BodySlide: Fixed "Remove Group" in Group Manager being disabled by default.
- Outfit Studio: Added "Slider -> Export TRI Morphs" feature to Outfit Studio.

## 2.7e
- General: Minor performance improvements. 
- BodySlide: Fixed crashing preview windows caused by rendering at the wrong times. 
- BodySlide: Added buttons to copy slider values to either low or high weight. 
- Outfit Studio: Removed dialogs for virtual shape offset and scale (just the virtual ones). 
- Outfit Studio: Added a minus and plus button to slider edit mode that scales slider data (not the shape).

## 2.7d
- BodySlide: Fixed uncompressed files within BSAs not loading (textures in preview).
- BodySlide: Now rescans BSAs when Game Data Path was changed in the settings dialog.
- Outfit Studio: Fixed "Add Group" button of group manager being disabled by default.
- Outfit Studio: Fixed bones sometimes not or wrongly being erased from NiSkinData.

## 2.7c
- BodySlide: Added new settings dialog.
- Outfit Studio: Fixed weight brush bug introduced in 2.7.

## 2.7b
- Outfit Studio: Fixed conforming and weight copying bug introduced in 2.7. 
- Outfit Studio: "Load Slider Preset" function now shows all presets, no matter the set or group names. 
- Outfit Studio: Fixed weights and masks not being shown if no texture was found.

## 2.7
- BodySlide: Now scans BSA files for textures and loads them, if they weren't found as loose files.
- BodySlide: Added a group manager for editing and creating group files.
- BodySlide: Changed texture path trimming behavior again. Always only "textures" at the front.
- Outfit Studio: Added "Slider -> Import TRI Morphs..." feature.
- Outfit Studio: Integrated brush settings into the main frame.
- Outfit Studio: Disabled axis-crossing for conforming and weight copying.
- Outfit Studio: Improved weight brush performance.
- Outfit Studio: Changes to the way duplicate shapes are renamed.
- Outfit Studio: Added working directory before the ShapeData path for loading projects with Mod Organizer.
- Outfit Studio: Reference not needed for saving a project anymore.
- Outfit Studio: Shader controllers are not dropped anymore.
- Outfit Studio: Fixed various bugs related to using "Keep other shapes" when loading an outfit.
- Outfit Studio: Normals for skin shaded shapes in the outfit list aren't generated anymore.
- Outfit Studio: Added all conversion references to the template list, as shape names can now be defined.
- Outfit Studio: Fixed crash when hovering mouse over mesh too early.
- Outfit Studio: OBJ import correctly flips UVs again now.
- Outfit Studio: Fixed OBJ export for NiTriStripsData.
- Outfit Studio: Fixed minor issues with shape selection tree.

## 2.6
- BodySlide: Added "About" dialog with library info and licences.
- Outfit Studio: Move, scale and rotate shape dialogs now use sliders.
- Outfit Studio: Added preview to "Rotate Shape" dialog.
- Outfit Studio: Weight brush now has X-Mirror disabled by default.
- Outfit Studio: Added "Front/Back/Left/Right" view buttons that adjust the camera.
- Outfit Studio: Added perspective/orthographic projection toggle.
- Outfit Studio: Added field of view slider.
- Outfit Studio: Added more accurate zooming by holding the middle mouse button and shift key.
- Outfit Studio: Added light settings tab. The same settings are applied in the BodySlide previews.
- Outfit Studio: Added "Fixed Weight Brush" check box when in the bones tab.
- Outfit Studio: Added support for FO3/NV NIFs. You can't convert them between games, though!
- Outfit Studio: Added "Target Game" entry to the Config.xml.
- Outfit Studio: Refactored the NIF code, possibly including some fixes.
- Outfit Studio: Removed registry warning if the game data path has been manually set already.
- Outfit Studio: Renamed "Copy Name" button to "To Project" in the save project dialog.
  - Does not affect the "Output File Name" and "Output Data Path" text controls anymore.
  - Label now says "_0/_1.nif" or ".nif" depending on low/high or single-weighted outputs.
- Outfit Studio: Bone weighting preview is now cleared before saving/exporting.
- Outfit Studio: Updated progress bar texts.
- Outfit Studio: Added error for unsupported NIF file versions.
- Outfit Studio: Now using the TinyXML-2 library (previously 1)

## 2.5
- CBBE: Fixed "BigTorso" slider causing a wrist seam.
- Unified UNP: Adjusted belly weighting for UUNP HDT and UUNP Special.
- Outfit Studio: Added multi-select functionality to shape list (e.g. "Move Shape" for all selected ones).
- Outfit Studio: Added "File -> Apply Overall Skin Transform". Disable to try out different offset loading.
- Outfit Studio: Added "File -> Export -> Export NIF With Reference". Exports full project, instead of just outfit.
- Outfit Studio: Fixed "Save Project" keeping deleted bone nodes of reference shape.
- Outfit Studio: Fixed "SliderSets" folder not being created if non-existent.
- Outfit Studio: Fixed crash on out-of-range zap index from old slider data.
- Redone OpenGL canvas with wxGLCanvas from wxWidgets.

## 2.4
- CBBE: Fixed "CBBE Vanilla" and "CBBE Vanilla NeverNude" mesh seams.
- Unified UNP: Improved, cleaned and unified the weighting of the 4 body types.
- Outfit Studio: Fixed Save Project always clearing the mask, even though there were no unweighted vertices.
- Outfit Studio: Load Project now loads shapes with slider data that is in a different folder, instead of removing them.
- Outfit Studio: Fixed "Show Mask" toggle affecting the visibility of the bone weights as well.
- Outfit Studio: Added "Transfer Selected Weights" menu item:
  - Transfers the weights of the selected bones from reference to chosen shape 1:1.
  - Requires same vertex count and order of source and target shape.
- Outfit Studio: Added "Apply Sliders?" message to the "Load Slider Preset" dialog as well.
- Outfit Studio: Added a brush that smooths bone weighting, accessed by pressing the SHIFT key while weight painting.
- Outfit Studio: Added NiTriStrips support (apart from "Build Skin Partitions").
- Outfit Studio: Added NiSkinPartition support.
- Outfit Studio: Added a bone scaling preview slider to the bones tab.

## 2.3
- BodySlide: Added "RaceMenu Morphs" build feature for in-game sliders. Requires RaceMenu and a matching morphs plugin.
- Outfit Studio: Added tons of conversion references for CBBE -> X -> CBBE (in UNPConvert.xml) and restructured them.
- Outfit Studio: Updated the XPMS Extended reference skeleton to version 2.50.
- Outfit Studio: Edited the reference skeleton to hopefully fix hand/finger scales when exported.
- Outfit Studio: Fixed crash when renaming shapes with unusual slider data naming, usually very old or manually edited.
- Outfit Studio: Added value display showing the mask factor of the current vertex while the mask brush is active.
- Outfit Studio: Added value display showing the position of the current vertex while any transform brush is active.
- Outfit Studio: Added single vertex movement dialog that shows when the 'V' key is pressed.
- Outfit Studio: Merged "Missing Bone" messages on a per-shape basis and added a few new error messages.
- Outfit Studio: Added ability to close the Move/Rotate/Scale Shape and brush settings dialogs with the enter key.
- Outfit Studio: Fixed "Duplicate Shape" and "Coalesce sliders" dialogs not being cancelable.
- Outfit Studio: Adjusted default brush settings and reorganized the brush settings dialog.
- Outfit Studio: Implemented automatic trimming of "Data\textures\" in texture set paths of shapes (for BS too).
- Outfit Studio: Added new button "Apply Diffuse" for the "Set Textures" dialog to apply texture changes to the view.
- Outfit Studio: Implemented automatic appending of file extensions in the "Save Project As" dialog (not visible).
- Outfit Studio: Fixed moving shapes in slider edit mode to work as intended.
- Outfit Studio: Added "Copy Selected Weights" to the shape context menu as well.
- Outfit Studio: Fixed resizing the brush with the 'S' key going over the limits.
- Outfit Studio: Changed hotkeys for brush size/strength adjustments to: Shift + +, Shift + -, Ctrl + +, Ctrl + -
- Outfit Studio: Bones that are not in the reference skeleton will not be removed when a weight copy is done anymore.
- Outfit Studio: The duplicate reference shape in the outfit shape list is now automatically deleted when loading a project.
- Outfit Studio: Loading projects with only one slider set in the XML file skips the selection dialog now.
- Outfit Studio: Made the load and save project file picker dialogs default to the "BodySlide\SliderSets" folder.
- Outfit Studio: Increased slider knob size (OS).

## 2.2d
- Outfit Studio: updated the XPMS Extended reference skeleton to version 2.33. 
- Outfit Studio: fixed "Brush -> Clear Mask" clearing weight colors as well (instead of only the mask). 
- Outfit Studio: weights are now only copied to unmasked vertices. Masked vertices keep their old weights. 
- BodySlide: fixed category UI alignment of single-weighted slider sets. 
- Now requires "Microsoft Visual C++ 2013 Redistributable (x86)" instead of 2012. Get it from Microsoft if it's not installed. 
- No longer Windows XP compatible (BodySlideWXP.exe removed).

## 2.2c
- BodySlide: fixed activating a zap after a preview window has been opened once causing a crash
- BodySlide: fixed what's getting batch built sometimes not representing the selection in the dialog
- BodySlide: widened the body/outfit drop down list by a bit
- Outfit Studio: fixed absolute path issues in the Save Project As dialog and cleaned it up some
- Outfit Studio: fixed weight painting colors sometimes not getting removed from rendering
- Outfit Studio: making or loading a new project now clears all memory of the previous project
- Outfit Studio: added some message boxes telling you to select a shape before doing stuff first

## 2.2b
- Outfit Studio: fixed brushes not always rendering properly
- BodySlide: fixed crashes with certain slider sets (e.g. CBBE Feet)

## 2.2a
- BodySlide: fixed low preview not updating properly

## 2.2
- added basic texture alpha rendering for meshes
- fixed OpenGL panel of Outfit Studio getting focused even though the BodySlide frame is active
- fixed trying to render meshes without at least one triangle
- BodySlide: added slider categories UI for CBBE, customizable under "BodySlide\SliderCategories"
- BodySlide: fixed shapes without at least one triangle not getting deleted on build
- Outfit Studio: fixed crash when using "Copy Selected Weights" while a reference shape is selected
- Outfit Studio: fixed unweight and unmask brushes not using the strength settings of the weight/mask brushes
- Outfit Studio: updated the XPMS Extended reference skeleton to version 2.14 (same as 2.13)

## 2.1c
- Outfit Studio: updated the XPMS Extended reference skeleton to version 2.13

## 2.1b
- Outfit Studio: updated the XPMS Extended reference skeleton to version 2.11
- Outfit Studio: black spots issue - implemented fix for more precise tangent spaces calculation

## 2.1a
- reverted "Smooth Seam Normals" selection back to the way it worked in 2.0.0.10
- removed auto-fill from "Save Project As" dialog, but improved default value filling
- fixed that you could save projects without a valid reference shape loaded
- renamed default names and UI items for making new zaps (removed the "slider" because it's not a slider in BS)

## 2.1
- added and made the XPMS Extended (XPMSE) skeleton the default reference
- fixed bones from previous outfit carrying over to the others
- added numeric value display to OS, showing the weight factor of the current vertex to the current bone
- added a warning about unweighted vertices to the export/save that puts those under a mask automatically
- fixed a crash when loading a reference shape that didn't have a BSLightingShaderProperty
- it is now possible to create new sliders with spaces in their names in Outfit Studio
- fixed crash when using "Move Shape" in an empty project
- fixed some internal name assignments for slider sets and groups in BodySlide
- fixed slider sets not assigned to any group being hidden in the BodySlide outfit list
- changed unused check box in OS into a check/uncheck all sliders feature (for conforming)
- added slider range setting to Config.xml for BodySlide UI (SliderMinimum and SliderMaximum)
- fixed empty reference shape when loading a project that only had one shape in it
- fixed some focus problems with the BodySlide frame and scrolling slider view
- slider names in BodySlide now scale dynamically and are centered
- added non-virtual "Scale Shape" feature (actually modifies the vertices)
- added "Clean" and "Batch Clean" features that remove target files and can be used by holding down the ALT key
- fixed not being able to delete some shapes that didn't have a (normal) shader
- fixed various issues with special characters in file names
- fixed crash for templates that don't have a shape called "BaseShape"
- fixed crash for zap sliders in single-weighted slider sets (GenWeights=false)
- disabled "Smooth Seam Normals" by default for all outfit shapes (enabled for bodies)
- fixed some incorrect values when saving presets
- fixed opening slider properties causing loss of slider data
- fixed math of Outfit Studio frame position values stored in Config.xml
- fixed brush settings getting outside of their minimum and maximum values
- fixed weight brush being selectable outside of weight edit mode
- renamed move/offset/scale features for less confusing names (non-virtual and virtual edits)
- added live preview for Move Shape and Scale Shape dialogs (non-virtual and virtual)
- fixed weighting colors/masks not showing up and darkened textures for some GPU (shader syntax error)
- fixed "Do you want to apply your changes?" dialog causing other shapes to be reset
- added "Rotate Shape" feature to Outfit Studio
- added check box "Keep other shapes" to "Load Outfit" dialog, making mashups possible
- added "select all" and "select none" to the batch build dialog
- added double-sided rendering when enabled in shader (brushes not working with it yet)
- made it possible to remove masks by holding the ALT key and add masks in weight edit mode
- weight painting now honors the current mask, and so does copying bone weights
- fixed one of the issues causing black spots for shapes with two faces in an opposite direction
- changed OS mouse controls: LMB = paint, MMB/Shift+RMB = pan, RMB = rotate
- added Config.xml option to enable LMB panning mouse controls again for OS
- fixed duplicating a shape resetting changes (vertices, weights, texture settings)
- integrated conversion references and fixes that were previously uploaded separately (7B, CHSBHC, ADEC, CBPE)
- added "Group Aliases" to the Config.xml, allowing a merge of several preset groups into one for compatibility
- made CB++ presets compatible with CBAdvanced outfits and the other way around using group aliases
- made "Save Project" become available after a slider set was loaded
- fixed "Save Project" breaking slider set files (.nif file name)
- changed default values of sliders made using "New Zap Slider" to 100% for low and high
- fixed crash when importing .obj files without UV's into OS (UV's are important)
- fixed "Save Project" dialog not getting filled with current project information
- fixed crash when saving shapes that don't have BSDismemberSkinInstance nodes

## 2.0.0.10
- fixed a crash when setting base shape with outfit tree header selected
- added new exe BodySlideWXP.exe to test compatability with Windows XP (worked)
- corrected an issue with saving low-weight presets
- fixed an issue where adding a new slider to a reference loaded from a NIF wouldn't correctly use the morph data
- fixed a corruption in an output NIF when a skin shaded shape also had normals
- set BodySlide.exe to require admin rights on launch

## 2.0.0.9c
- minor package change, put BodySlide folder inside Data/CalienteTools for NMM compatibility

## 2.0.0.9b
- Beta version! Releasing to the public! Warning: may never get out of beta, and there are likely major problems, use at your own risk! :)
- fixed an issue that caused batchbuild to ignore the disabled outfits when building
- fixed an Outfit Studio problem that occurred when an outfit NIF had multiple shapes with the same name. Duplicated named shapes are now renamed to something unique.
- combined CalienteBody with CB++, it's now called CalienteBodyAdvanced, with 50+ sliders!