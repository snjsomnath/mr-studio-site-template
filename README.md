# Our table

This repository is one MR Studio table: the place, the data and the layers our team shows on the
projected model, the controller and visitors' phones. It holds no MR Studio code. The app does the
rest, and updating MR Studio means installing a newer app; nothing here changes.

Made from the MR Studio site template. Replace "Our table" in this file and in `site.json` with your table's name.

## Open it

1. Install MR Studio from the [releases page](https://github.com/snjsomnath/mr-studio/releases) (Windows or macOS).
2. Clone or download this repository.
3. In MR Studio, **File › Open…** and pick this folder (the one with `site.json`).
4. Move the table to your place: **Design › Table size and place…**, or start again with the wizard
   (**File › New table…**) and copy what it makes over this folder's `site.json` and `data/`.

The [author's guide](https://github.com/snjsomnath/mr-studio/tree/main/docs/guide) goes from here to
a presented table: bringing in your place, adding layers, the controller and phones, presenting,
calibrating the projector and sharing.

## What is in here

| Path | What it is |
| --- | --- |
| `site.json` | The table: where it is, its size, its layers, the controller's words. The editor writes it; you rarely edit it by hand |
| `data/` | The table's files: buildings, streets, trees, pictures, videos, your own datasets. **Add › Data file** in the editor puts them here |
| `layers/` | Your own code layers, if you write any (`mrstudio layer new . my-layer`). Most tables need none |
| `.github/workflows/check.yml` | Checks the table on every push, so a broken `site.json` is caught before it reaches the studio computer |

Not kept in git (see `.gitignore`): `.cache/` (map pictures the table keeps for offline use) and
`scene/` (what `mrstudio prepare` writes for inspection). Both are made again when needed.

## Share it with the studio computer

Either push here and pull on the studio computer, or use **Share** (top right in the editor) to
email the table as one `.mrstable` file, which the studio computer opens with **Update it**.

## Keys and passwords

Never commit a key. Map keys and sign-ins live in the app's **Sources** manager, in this
computer's keychain, and an exported table carries none.

## The check

`.github/workflows/check.yml` installs the `mrstudio` command line and runs `mrstudio validate .`.
It uses the version in `mrstudio.version`, which the app writes when it changes the table, so
keep that file in the repository. A table without one is checked with `MRSTUDIO_VERSION`. A
studio computer with an older app says which version to install when it opens the table. The first run takes a few minutes to build the command line; later runs reuse it.

## Something missing in MR Studio

A table should not need a change to the app. When it does (a building block a layer of ours
needs, a fault in the app), open an issue in
[snjsomnath/mr-studio](https://github.com/snjsomnath/mr-studio/issues). To send the change
yourself, read its [CONTRIBUTING.md](https://github.com/snjsomnath/mr-studio/blob/main/CONTRIBUTING.md) first.
