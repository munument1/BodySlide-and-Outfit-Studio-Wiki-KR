## BodySlide Command-Line Arguments

### Synopsis

```
BodySlide [--groupbuild <groups>] [--targetdir <path>] [--preset <name>] [--trimorphs] [--preview <files>]
```

### Options

| Short | Long | Type | Description |
|-------|------|------|-------------|
| `-gbuild` | `--groupbuild` | `string` | Comma-separated list of group names to build on launch. When specified, BodySlide performs a group build and exits. |
| `-t` | `--targetdir` | `string` | Output directory for the build. Defaults to the configured game data path. A path separator is appended automatically if missing. |
| `-p` | `--preset` | `string` | Preset to use for the build. Defaults to the last used preset. |
| `-tri` | `--trimorphs` | switch | Enables tri morph output for the build. |
| `-preview` | `--preview` | `string` | Comma-, semicolon-, or pipe-separated list of file paths (`.nif` or `.osp`) to open in preview mode. When specified, BodySlide opens a preview window directly without showing the main frame. See [Preview Mode](#preview-mode) for details. |

### Usage Examples

**Build a single group with the default preset:**
```
BodySlide --groupbuild "MyGroup"
```

**Build multiple groups to a custom directory with tri morphs:**
```
BodySlide --groupbuild "CBBE,CBBE Vanilla Outfits" --targetdir "C:\Output" --preset "CBBE Curvy" --trimorphs
```

**Preview NIF files:**
```
BodySlide --preview "mesh1.nif,mesh2.nif"
```

**Preview all slider sets from an OSP project file:**
```
BodySlide --preview "project.osp"
```

**Preview specific slider sets from an OSP file:**
```
BodySlide --preview "project.osp?SetName1?SetName2"
```

**Mix OSP projects with extra NIF files:**
```
BodySlide --preview "project.osp?MySet,extra.nif"
```

### Preview Mode

The `--preview` option supports both `.nif` and `.osp` (BodySlide project) files. File behavior depends on the extension and whether explicit slider-set names are provided.

The outer file list is split on commas, semicolons, or pipes. Inside a single `.osp` entry, `?` separates the project path from one or more explicit slider-set names.

**NIF files**

Plain `.nif` paths are loaded directly into the preview window as meshes.

**OSP files**

`.osp` files are BodySlide project files that contain one or more slider sets. The `?` character is used as a separator to specify which slider sets to load from an `.osp` file:

```
path/to/file.osp?SetNameA?SetNameB
```

| Syntax | Behavior |
|--------|----------|
| `file.osp` | All slider sets in the file are discovered and presented in a dropdown for selection. |
| `file.osp?Set1` | Only the named slider set is loaded. |
| `file.osp?Set1?Set2` | Multiple named sets are loaded together (multi-project mode). |

### Notes

- The `--groupbuild` option triggers a batch build of all outfits belonging to the specified groups and closes the application when finished.
- The `--preview` option is mutually exclusive with normal operation; the main BodySlide window is not shown.
- The `--targetdir` and `--preset` options are only meaningful when used with `--groupbuild`.

## Outfit Studio Command-Line Arguments

### Synopsis

```
OutfitStudio [--project <name>] [--single-instance <yes|no>] [--automation <script>] [<file> ...]
```

### Options

| Short | Long | Type | Description |
|-------|------|------|-------------|
| `-proj` | `--project` | `string` | Name of the project to load on launch. |
| `-single` | `--single-instance` | `string` | Force single-instance behavior. `yes` sends files to an already-running instance; `no` always opens a new instance. If omitted, the application uses its default/configured behavior. |
| `-a` | `--automation` | `string` | Run an automation script by name (without the `.xml` extension) in headless mode. |
| | *(positional)* | `string` | One or more file paths to open. Multiple files can be specified. When `--automation` is used, these become batch inputs for batch-mode scripts instead. |

### Usage Examples

**Open files in a new instance:**
```
OutfitStudio --single-instance no model.nif
```

**Open a project by name:**
```
OutfitStudio --project "MyProject"
```

**Send files to an already-running instance:**
```
OutfitStudio --single-instance yes mesh.nif
```

**Open multiple files:**
```
OutfitStudio file1.nif file2.nif file3.obj
```

**Run automation script:**
```
OutfitStudio --automation "ConvertFromBodyAtoB" file1.nif file2.nif
```

**Run a folder-scan automation against a directory:**
```
OutfitStudio --automation "ProcessFolder" "D:\Meshes"
```

### Notes

- Positional file arguments are optional and support multiple files.
- When `--single-instance yes` is used and an instance is already running, files are forwarded to it via IPC (DDE on Windows, TCP elsewhere).
- The `--project` option specifies which project within the loaded files to select.
- When `--automation` is used, positional arguments are treated as batch inputs: file paths or directories for **Folder Scan**, or slider set project names for **Slider Sets**.
- Non-batch automation scripts ignore positional arguments.
