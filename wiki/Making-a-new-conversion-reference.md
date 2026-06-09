## Introduction
Conversion references consist of one or more sliders that morph a mesh **from one shape to another**.

This guide outlines how to create your own conversion reference by **making use of existing sliders**. Following this, you can recreate the shape you want to convert **from**, which can then be used to convert **both ways**.

## Step-by-step example
1. **Load up a [[reference template|Reference Templates]]** with sliders, for example the **CBBE Body** template. This will be the target body that you want to **convert to**.

2. Use the sliders to create a shape that looks closest to the source body. This is the shape to **convert from**. Don't forget that you can type in negative slider values or values above 100% as well.

3. When you're done, use the **File -> Make Conversion Reference** menu item and give the slider a name, such as "Other Body -> CBBE".

4. **Save the project** (Other Body -> CBBE) using **[[File -> Save Project As|Saving a project]]**. For conversion references, the output paths and file names don't matter, as they're not used in BodySlide.

    The individual text boxes all have tool tips that appear when hovering over them with the mouse. You can simply **enter a display name** and click the **To Project** button.

5. (Optional) If you need a **reversed conversion reference**, set the slider you made to 100% and use **File -> Make Conversion Reference** again. Name the slider the opposite way, for example "CBBE -> Target Body".

6. (Optional) **Save the reversed project** (CBBE -> Other Body) using **[[File -> Save Project As|Saving a project]]**. For conversion references, the output paths and file names don't matter, as they're not used in BodySlide.

    The individual text boxes all have tool tips that appear when hovering over them with the mouse. You can simply **enter a display name** and click the **To Project** button.

7. You can now use the newly created conversion reference(s) in Outfit Studio to morph outfits from body to body.