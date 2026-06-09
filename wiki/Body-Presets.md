# Managing Presets

Presets are saved BodySlide slider settings. Instead of setting every slider by hand each time, you can choose a preset from the **Preset** dropdown and apply a saved body or outfit shape.

Preset files are XML files stored in the `SliderPresets` folder of your BodySlide installation or project path. A single XML file can contain one preset or several presets.

Presets do not contain meshes, textures, or a complete body mod. They only contain slider values, so they work correctly only with outfits and bodies that use the same or compatible sliders.

## How Presets Appear In BodySlide

BodySlide does not show every installed preset for every outfit. The **Preset** dropdown is filtered by the currently selected **Outfit/Body**.

Each outfit or body belongs to one or more groups, which are defined by XML files in the `SliderGroups` folder. Each preset is also assigned to one or more groups. A preset appears when it shares a group with the selected outfit or body.

For example, a CBBE preset should usually be assigned to the broad `CBBE` group. Any CBBE outfit that also belongs to that group can then show the preset.

In most cases, do not assign a preset to every outfit mod group in the list. Assign the master body group instead. Add outfit-specific groups only when the preset is intentionally meant to appear only for those specific outfits.

If a preset is assigned only to an outfit mod group and not to the main body group, it may appear for that mod's outfits but disappear for other compatible outfits. This is one of the most common reasons users cannot find an installed preset.

The **Filter presets...** box only searches the presets that are already visible for the selected outfit or body. Clearing the preset filter will not show presets whose groups do not match.

The **Filter groups...** box and **Choose groups...** menu filter the **Outfit/Body** list. They do not directly assign groups to a preset, but they can affect which outfit or body is selected, which then changes which presets are visible.

## Creating A Preset

1. Choose an **Outfit/Body** that uses the sliders you want to save.
2. Set the sliders to the shape you want.
3. Click **Save As...**.
4. Enter a preset name.
5. Select the groups that should use the preset.
6. Click **Save**.
7. In the file dialog, save the XML file in the `SliderPresets` folder.

When choosing groups, select the broad body group in normal cases. For example, a preset made for CBBE bodies and outfits usually needs the `CBBE` group, not every individual outfit group.

If you save to an existing preset XML file, BodySlide adds the new preset to that file. If the file already contains a preset with the same name, BodySlide replaces that preset in the file and keeps the other presets in the file.

## Editing Slider Values

To update the slider values of an existing preset:

1. Select an **Outfit/Body** where the preset appears.
2. Select the preset from the **Preset** dropdown.
3. Adjust the sliders.
4. Click **Save**.

The **Save** button updates the selected preset in its XML file. There is no confirmation step and BodySlide does not create a backup of the old slider values. If you are editing a downloaded preset or a preset you may want to restore later, make a copy of the XML file first.

## Editing Preset Groups

To change which groups a preset is assigned to:

1. Select an **Outfit/Body** where the preset appears.
2. Select the preset from the **Preset** dropdown.
3. Click the edit button next to the preset controls.
4. Check or uncheck the groups for the preset.
5. Click **Save**.

This updates the selected preset in its existing XML file.

If the preset does not appear anywhere useful, you can inspect or edit the XML file manually. The group assignments are near the start of each preset entry:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SliderPresets>
    <Preset name="My CBBE Preset" set="CBBE Body">
        <Group name="CBBE"/>
        <SetSlider name="Breasts" size="small" value="50"/>
        <SetSlider name="Breasts" size="big" value="75"/>
    </Preset>
</SliderPresets>
```

In this example, the preset is assigned to the `CBBE` group. Group names must match the BodySlide group name exactly.

The `set` attribute is the outfit or body that was selected when the preset was saved. It can help a preset appear for that exact slider set, but groups are the normal way to make a preset available across compatible outfits.

Adding a group can make a preset appear for more outfits, but it does not convert the preset to another body type. If the target body uses different slider names or different slider behavior, the preset may not work correctly even if it appears in the dropdown.

## Deleting A Preset

To delete a preset, select it in the **Preset** dropdown and click the delete button next to the preset controls. BodySlide asks for confirmation, then removes that preset entry from its XML file.

If the XML file contains multiple presets, deleting one preset does not remove the other presets from that file.

## Troubleshooting

### The Preset Does Not Appear

Check these common causes:

1. Make sure the preset XML file is installed in the `SliderPresets` folder for the BodySlide setup you are using.
2. Select an outfit or body that uses the same body type as the preset.
3. Clear the **Filter presets...** box.
4. Check whether the selected outfit or body belongs to the group assigned to the preset.
5. Open the preset XML file and confirm that the preset has the correct master body group, such as `CBBE` for CBBE presets.
6. Avoid duplicate preset names across different XML files. Duplicate names can make it unclear which preset BodySlide is loading.

If a preset XML contains only outfit-specific groups, add the appropriate master body group by using the preset group editor or by carefully editing the XML file.

### The Preset Appears For The Wrong Outfits

The preset is probably assigned to too many groups or to a group that contains those outfits. Edit the preset's group assignments and keep only the groups that should use it.

For shared body presets, this usually means keeping the master body group and removing unrelated outfit-specific groups.

### The Preset Appears But Does Not Change Some Sliders

Presets only store sliders that existed and had saved values when the preset was created. If the selected outfit or body uses different slider names, missing sliders, or a different body mod, some values may not apply.

Use a preset made for the same body and slider set whenever possible.

## Sharing Presets

When sharing a preset with other users:

1. Put the preset XML file in the `SliderPresets` folder structure expected by BodySlide mod managers.
2. Assign the preset to the broad body group it was made for.
3. Do not assign every outfit group unless the preset is intentionally limited to those outfits.
4. Use a unique preset name.
5. Tell users which body mod and sliders the preset requires.
6. If the XML file contains multiple presets, list the included preset names.

Good group assignments make presets easier to find and reduce confusion for users building outfits from many different mods.