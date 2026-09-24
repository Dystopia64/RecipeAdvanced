# RecipeAdvanced

A crafting plugin for **Paper 26.1.2**. Java 21, single file, no external
dependencies.

**Download:** [Releases](../../releases/latest)

---

## Features

### In-game recipe editor

`/ra editor` — build recipes with the mouse, no YAML editing. Drop an
ingredient into a slot, the result into its own; everything else is a button.

### Vanilla stations

Crafting table, furnace, blast furnace, smoker, campfire, anvil, grindstone,
brewing stand, smithing table, stonecutter, cauldron. Recipes become real
server recipes and work in the ordinary vanilla window.

- **furnace** — set the cook time, the experience granted, and let a whole
  stack smelt instead of one item at a time;
- **smithing table** — carries enchantments from the old item over to the new
  one, instead of refusing to craft anything enchanted;
- **cauldron** — the water, lava or powder snow level is shown with coloured
  glass, the right fire has to burn underneath, brewing takes time, throws
  particles and consumes fluid, and the result floats up out of the pot.
  The brew belongs to the block: you can walk away, log out and come back.

### Custom workbenches on blocks

Bind any block to its own crafting menu.

### One recipe, one file

Recipes live in `plugins/RecipeAdvanced/recipes/`, one file each, arranged in
folders. `/ra save <folder> <recipe>` moves a recipe; Tab suggests existing
folders.

### `/recipes` — a single tree

Your recipes and other plugins' in one list with folders. From a recipe you can
walk into the recipe of its ingredient: you see an enchanted sword, click the
ingot, and see where the ingot comes from.

Another plugin's recipes appear only once you publish them — `/ra ext add
<namespace> [folder]`, or `/ra ext all` for the lot — and they go in the
folders you name, not the ones the content pack came with.

### Items from other plugins

CraftEngine, ExecutableItems, ExecutableBlocks, Oraxen, ItemsAdder and
MMOItems work as ingredients and as results. Detection is automatic; there is
nothing to configure.

### Recipe conditions

Permission, world, time of day, required experience, drop chance, extra items
in the output.

### Languages

Chat messages ship in English, Russian, Ukrainian, German and Spanish. Pick
one with `language: en` in `config.yml`. The files live in `lang/` inside the
plugin folder and are yours to edit — an update never overwrites them. To add
a language, copy one of them to `lang/<code>.yml`, translate it and point
`language` at it.

Menu text is currently Russian; translating it is in progress.

### Verification

`/ra verify` walks every recipe and reports what is wrong with it — before your
players find out.

---

## Installation

1. Drop the jar into `plugins/`.
2. Restart the server.

Permissions:

| Permission | For |
|---|---|
| `recipeadvanced.use` | players: open crafting menus and `/recipes` |
| `recipeadvanced.admin` | staff: the editor and the `/ra` commands |

---

## Commands

| Command | What it does |
|---|---|
| `/ra editor` | recipe editor |
| `/ra save <folder> <recipe>` | move a recipe into a folder |
| `/ra verify` | check every recipe |
| `/ra reload` | reload the configuration |
| `/recipes` | tree of every recipe on the server |

---

## Full version

Two things are missing from the free version:

- multiblock stations built out of blocks, with their own menu, holograms and
  particles;
- the 4x4, 5x5 and 6x6 workbenches.

That code is not in the free jar at all: the classes are not shipped, so there
is no flag to flip.

---

## Licence

Free to use on any server, commercial ones included. See [LICENSE](LICENSE).
