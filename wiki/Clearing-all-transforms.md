There are different types of transforms, such as:
* Node transforms (e.g. NiNode)
* Static shape transforms (e.g. NiTriShape, BSTriShape, ...)
* Global-to-skin transforms (NiSkinData, not saved to file for FO4)
* Bone transforms (NiSkinData, BSSkin::BoneData) for each bone

Sometimes, when meshes are aligned in Outfit Studio **but transforms aren't dealt with** (cleared by the user or redone), they can **appear in a wrong spot in-game or become invisible** as you get closer, as the game might think they are "out-of-bounds" (not visible by the player, even though they're clearly on screen).

### One way to clear them is to:
1. Make sure the shapes appear correctly aligned with a clean reference mesh (such as the body) in Outfit Studio. If they do not, use the transform tool or "Shape -> Move" to align them.
2. Then, clear the global-to-skin transform by going into the [[Shape Properties]] ("Coordinates" tab) of each individual shape and setting the origin/rotation to 0,0,0 and the scale to 1.0. Make sure the "_Recalculate geometry's coordinates so it doesn't move_" is checked and click OK. Repeat this for each shape.
3. To update bone transforms and clear the static shape transforms, use the "Edit -> Reset Transforms" command once (it affects all shapes).