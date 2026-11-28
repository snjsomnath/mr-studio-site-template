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
| `data/` | The table's files: buildings, streets, trees, pictures, videos, your own datasets. **Insert › Data file** in the editor puts them here |
| `layers/` | Your own code layers, if you write any (`mrstudio layer new . my-layer`). Most tables need none |
| `.github/workflows/check.yml` | Checks the table on every push, so a broken `site.json` is caught before it reaches the studio computer |
| `.gitlab-ci.yml` | The same check for a table kept on GitLab. Delete whichever of the two you do not use |

Not kept in git (see `.gitignore`): `.cache/` (map pictures the table keeps for offline use),
`scene/` (what `mrstudio prepare` writes for inspection) and `.cargo/` (where the GitLab check
keeps the command line). All three are made again when needed.

## Keep it on GitLab

GitLab has no "Use this template" button. Make the repository with **New project › Import
project › Repository by URL** and give it
`https://github.com/snjsomnath/mr-studio-site-template.git`. The `.gitlab-ci.yml` check then runs
on every push, as long as the group has CI runners.

Big files such as videos and hourly rasters belong in Git LFS (`git lfs track "data/**/*.mp4"`).
Check how much LFS space the group has first. GitLab's check fetches LFS files by itself.

## Share it with the studio computer

On the studio computer (MR Studio 0.59 or later), Home's **Get a table from a git repository…** (under Your tables) takes
this repository's address and keeps the table in its tables folder. When you push a new
version, the table's card there says **Update from the repository (N new)**. The studio
computer only follows: a table changed there is not updated over, and nothing updates while it
is on the screens. Signing in is git's own (Git Credential Manager, an SSH key, or a read-only
deploy token in the address), and Git LFS must be installed there for LFS files.

Without git, use **Share** (top right in the editor) to email the table as one `.mrstable` file,
which the studio computer opens with **Update it**.

## Keys and passwords

Never commit a key. Map keys and sign-ins live in the app's **Sources** manager, in this
computer's keychain, and an exported table carries none.

## The check

`.github/workflows/check.yml` (or `.gitlab-ci.yml` on GitLab) installs the `mrstudio` command line and runs `mrstudio validate .`.
It uses the version in `mrstudio.version`, which the app writes when it changes the table, so
keep that file in the repository. A table without one is checked with `MRSTUDIO_VERSION`. A
studio computer with an older app says which version to install when it opens the table. The first run takes a few minutes to build the command line; later runs reuse it.

## Something missing in MR Studio

A table should not need a change to the app. When it does (a building block a layer of ours
needs, a fault in the app), open an issue in
[snjsomnath/mr-studio](https://github.com/snjsomnath/mr-studio/issues). To send the change
yourself, read its [CONTRIBUTING.md](https://github.com/snjsomnath/mr-studio/blob/main/CONTRIBUTING.md) first.
