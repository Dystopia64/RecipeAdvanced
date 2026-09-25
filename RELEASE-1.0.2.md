# RecipeAdvanced 1.0.2 — free edition

A crafting plugin for Paper. Java 21, exactly one dependency — `paper-api`.

## Added

**Everything is translatable now.** 1234 lines of text — menus, commands,
station names, particle names, the result of `/ra verify` — live in
`lang/<code>.yml` instead of being written into the code. English and Russian
are complete; Ukrainian, German and Spanish cover what a player sees and fall
back to English on the administration screens.

`/ra lang` reports the active language, how many lines loaded and names any
that did not.

**Other plugins' recipes are opt in.** Installing a content pack no longer
fills `/recipes` with hundreds of entries in folders you did not choose:

| Command | What it does |
|---|---|
| `/ra ext list` | every foreign namespace on the server, with recipe counts |
| `/ra ext add <namespace> [folder]` | publish one, optionally into a folder |
| `/ra ext all [folder]` | publish everything at once |
| `/ra ext folder <namespace> <folder>` | move a whole category |
| `/ra ext remove <namespace>` | take it back out of the book |

## Changed

**Nothing ships with content.** A fresh install used to come with a demo
recipe, three workbenches and three folders. What belongs in a server's recipe
book is the owner's decision.

**Building a station of your own is a full-edition feature.** Stations written
earlier keep working in the free edition — they load, they open, their items
can still be handed out — but creating or editing one needs the full version.

## Fixed

- **The anvil would not hand over a result that costs nothing.** Vanilla
  refuses to release a result whose level cost is zero: the item is drawn in
  the slot and clicking does nothing. Recipes with no experience cost ran
  straight into that.
- **Eighty three menu lines were missing.** A configuration reads a dot as a
  path separator, so `editor.xp` and `editor.xp.furnace` could not both exist
  in one file — the second turned the first into a section and its text was
  gone. Menus showed "Missing message" where a label belongs.
- **The editor's navigation column was invisible**: closed pages were drawn as
  a grey pane against a black pane background. Each page now keeps its own
  icon, and the open one glows.
- **Page names never changed language.** They were resolved once, when the
  class was first touched — before the language files are read — and stayed
  that way through every reload.
- Recipes written for the 4x4/5x5/6x6 workbenches, copied from a full edition
  server, quietly became ordinary furnace recipes in the free one.
- The recipe and workbench editors offered grids and a station type that
  cannot open in this edition; picking one saved a recipe that opened nowhere.
- In the `/recipes` tree, every folder printed "click to open" twice.
- The furnace and cauldron slot labels were never translated at all.

## Not in the free version

- multiblock stations built out of blocks, with their own menu, holograms and
  particles;
- the 4x4, 5x5 and 6x6 workbenches;
- building a station of your own.

Those classes are not in this jar — not a flag, but absent code.

## Installation

Drop the jar into `plugins/`, restart the server. Permissions:
`recipeadvanced.admin` for the editor and commands, `recipeadvanced.use` to
open crafting menus and `/recipes`.
