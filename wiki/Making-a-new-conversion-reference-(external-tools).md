## Introduction
Conversion references consist of one or more sliders that morph a mesh **from one shape to another**.

This guide outlines how to create your own conversion reference by **using external 3D software**. Following this, you can recreate the shape you want to convert **from**, which can then be used to convert **both ways**.

Before following this guide, you should see if the normal Outfit Studio method works well enough for you: [[Making a new conversion reference]]

## Step-by-step example
To use this method, you will **need 3D software** such as Blender or 3ds Max. Unfortunately I can't explain how to use these programs here as it's out of scope, sorry. :wink:

For this example, we are going to say that our base body is CBBE. That means, we are going to create a conversion reference that goes from CBBE to another body (and back, if needed).

1. Load the **NIF file of the other body** into Outfit Studio and export it as an OBJ file using the **Shape -> Export -> To OBJ** menu item.

2. Load the **CBBE Body** [[reference template|Reference Templates]] (or similar) into Outfit Studio and export it as an OBJ file using the **Shape -> Export -> To OBJ** menu item.

3. **Import both of these OBJ files** into your preferred 3D software. Bodies like CBBE can used as a bridge to convert between various body types in our references, which is why it's being used here.

4. Use **Shrinkwrap modifiers** or any similar methods of your 3D software to wrap the CBBE (base body) shape around the other body (not the other way around!).

    Make sure to **manually align** the body shape a bit beforehand. This will ensure better wrapping accuracy.

    You want all parts of the anatomy to line up properly before applying the wrapping. You're recreating the exact shape of the other body, but using the mesh of the base body.

    #### Blender Shrinkwrap example
    ![Shrinkwarp](http://i.imgur.com/HvEksIQ.png)

5. Export the resulting shaped base body (the one that was wrapped around the other body) as an OBJ file.

    Make sure both the **vertex count and vertex order stay the same** by checking the export options of your program.

6. ![New Project](http://i.imgur.com/KxNNU2K.png) Create a **new project** in Outfit Studio using the same reference you used in step 2.

7. Create a new slider using the **Slider -> New Slider** menu item.

8. ![Edit Mode](http://i.imgur.com/qiGhRPw.png) Click the edit button of the new slider and use the **Slider -> Import Slider Data -> Import OBJ** feature with the morph you exported out of the 3D software.

    This creates the "CBBE -> Other Body" slider data from the difference of the two.

9. **Save the project** (CBBE -> Other Body) using **[[File -> Save Project As|Saving a project]]**. For conversion references, the output paths and file names don't matter, as they're not used in BodySlide.

10. (Optional) To create the **reversed conversion reference**, set the slider you have to 100% and use **File -> Make Conversion Reference** again. Name the slider the opposite way, for example "Target Body -> CBBE".

11. (Optional) **Save the reversed project** (Other Body -> CBBE) using **[[File -> Save Project As|Saving a project]]**. the output paths and file names don't matter, as they're not used in BodySlide.

12. You can now use the newly created conversion reference(s) in Outfit Studio to morph outfits from body to body.