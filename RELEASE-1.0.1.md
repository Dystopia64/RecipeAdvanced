# RecipeAdvanced 1.0.1 — free edition

A crafting plugin for Paper. Java 21, exactly one dependency — `paper-api`.
Nothing else to install.

## Added

**Languages.** Chat and every menu a player sees now ship in **English,
Russian, Ukrainian, German and Spanish**. Pick one with `language:` in
`config.yml`. The files live in `lang/` inside the plugin folder and are yours
to edit — an update never overwrites them. To add a language, copy one of them
to `lang/<code>.yml`, translate it and point `language` at it.

English is the default on a fresh install. A server that had already reworded
the `messages:` section of `config.yml` keeps its own wording.

`/ra lang` reports the active language, how many lines loaded, and names any
that did not.

**Other plugins' recipes are opt in.** Installing a content pack no longer
fills `/recipes` with hundreds of entries filed into folders you did not
choose. Nothing from another plugin appears until you say so:

| Command | What it does |
|---|---|
| `/ra ext list` | every foreign namespace on the server, with recipe counts |
| `/ra ext add <namespace> [folder]` | publish one, optionally into a folder |
| `/ra ext all [folder]` | publish everything at once |
| `/ra ext folder <namespace> <folder>` | move a whole category |
| `/ra ext remove <namespace>` | take it back out of the book |

Folders may be nested — `Food/Plants` works. Changes take effect immediately
and are written to `config.yml`.

## Changed

**Nothing ships with content any more.** A fresh install used to come with a
demo recipe, three workbenches and the folders "Equipment", "Farm" and
"Other". What belongs in a server's recipe book is the owner's decision. The
files are still there, with comments explaining the format, and no entries.

## Fixed

- **Every menu line read "Missing message".** Keys like `gui.tree.window` look
  flat, but the YAML loader treats a dot as a path separator and files them as
  nested sections; reading only the top level returned a section instead of a
  string. Menus in 1.0.0 were unaffected — the keys arrived with this release —
  but the bug would have shipped with it.
- **The anvil would not hand over a result that costs nothing.** Vanilla
  refuses to release a result whose level cost is zero: the item is drawn in
  the slot and clicking does nothing. Recipes with no experience cost ran
  straight into that. The displayed cost is now at least one level; what the
  player is actually charged is still whatever the recipe says.
- A recipe that matches but produces nothing now says so in the server log,
  naming itself and the reason, instead of leaving an empty slot that looks
  like a broken plugin.
- In the `/recipes` tree, every folder printed "click to open" twice.
- Recipes written for the 4x4/5x5/6x6 workbenches, copied over from a full
  edition server, quietly fell through to the vanilla recipe registry and
  became ordinary furnace recipes. They are now skipped, and the count is
  named in the log at startup.
- The recipe editor and the workbench editor offered the 4x4/5x5/6x6 grids and
  the plugin's own station type even though they cannot open in this edition.
  Picking one saved a recipe that opened nowhere; those stops are now skipped.

## Known limitations

- The administration menus — the recipe editor, the workbench editor and the
  other staff-only screens — are still Russian-only. Translating them is in
  progress.
- Foreign recipes are published a namespace at a time; there is no way to hide
  a single recipe belonging to another plugin.

## Installation

Drop the jar into `plugins/`, restart the server. Permissions:
`recipeadvanced.admin` for the editor and commands, `recipeadvanced.use` to
open crafting menus and `/recipes`.
