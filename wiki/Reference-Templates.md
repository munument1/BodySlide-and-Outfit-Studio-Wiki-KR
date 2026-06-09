## What are reference templates?

Reference templates are reusable shortcuts for loading a known slider set as a reference in Outfit Studio. They are not project files by themselves. A template only tells Outfit Studio which slider-set file, set name, and optionally which shape to load.

Templates are used by:

* The **Load Reference** dialog in Outfit Studio
* Conversion workflows such as **Convert Body / Reference**
* The **Load Reference** step in the Automation dialog, where choosing a template auto-fills the source file, set, shape, and `Load all shapes` option

## Where templates are loaded from

Outfit Studio loads reference templates from both of these locations inside the BodySlide folder:

* `RefTemplates.xml`
* Every `.xml` file inside the `RefTemplates` folder

This lets mod authors ship extra template packs without forcing users to merge everything into one file.

## XML format

Use the following structure:

```xml
<RefTemplates>
    <Template sourcefile="SliderSets/CBBE.osp" set="CBBE Body" shape="CBBE">CBBE Body</Template>
    <Template sourcefile="ConversionSets/VanillaToCBBE.osp" set="Vanilla To CBBE" loadAll="true">Vanilla To CBBE</Template>
</RefTemplates>
```

Each `<Template>` element supports these values:

* **Text content** is the display name shown in the template list.
* **sourcefile** points to the `.osp` file that contains the slider set. Relative paths are resolved from the BodySlide folder. Absolute paths also work, but relative paths are usually better for distributable template packs.
* **set** is the slider-set name inside that `.osp` file.
* **shape** is the shape that should become the reference when loading a single reference shape.
* **loadAll** changes the behavior from “load one reference shape” to “add all shapes from this slider set”. When `loadAll="true"`, the `shape` attribute is ignored.

## Defining good templates

### Single-reference templates

Use these when you want a known base/reference shape.

```xml
<Template sourcefile="SliderSets/CBBE.osp" set="CBBE Body" shape="CBBE">CBBE Body</Template>
```

If `shape` is omitted, Outfit Studio falls back to the first shape found in the referenced NIF. That can work, but explicitly naming the intended shape is safer.

### Load-all templates

Use these when the template should import every shape from the selected slider set instead of choosing one base shape.

```xml
<Template sourcefile="ConversionSets/VanillaToCBBE.osp" set="Vanilla To CBBE" loadAll="true">Vanilla To CBBE</Template>
```

This is useful for conversion sets and other multi-shape references.

## Packaging and organization

* Templates can stay in the root `RefTemplates.xml` file, or you can split them across multiple XML files in the `RefTemplates` folder.
* Keeping mod-specific templates in separate files makes updates easier and avoids merge conflicts.
* The template name is just a display label, so use unique names to avoid confusing duplicate entries in the picker.

## Keeping templates hidden from BodySlide users

If you want a project to be available as a reference template in Outfit Studio but not show up as a normal BodySlide project, keep the referenced `.osp` outside the usual `SliderSets` lineup that end users browse directly. For example, conversion-only projects can live in a separate folder such as `ConversionSets` while still being referenced by template XML.

## Related pages

* [[Conversion references and using them]]
* [[Automation Dialog]]