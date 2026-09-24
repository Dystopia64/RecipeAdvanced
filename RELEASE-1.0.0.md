# RecipeAdvanced 1.0.0 — free edition

A crafting plugin for Paper 26.1.2. Java 21, exactly one dependency —
`paper-api`. Nothing else to install.

## What it does

**An editor inside the game.** `/ra editor` — recipes are built with the mouse,
no YAML. The ingredient goes into a slot, the result into its own; everything
adjustable is a button.

**Vanilla stations.** Crafting table, furnace, blast furnace, smoker, campfire,
anvil, grindstone, brewing stand, smithing table, stonecutter, cauldron.
Recipes become real server recipes and work in the ordinary vanilla window,
not in an imitation of one.

**The furnace, fully under control.** Cook time, experience granted, and a
whole stack smelting instead of one item at a time.

**The smithing table carries enchantments** from the old item to the new one,
instead of refusing to craft anything enchanted.

**The cauldron.** Water, lava or powder snow level shown with coloured glass,
the right fire required underneath, brewing with a duration and particles,
fluid consumed, and the result floating up out of the pot. The brew belongs to
the block: you can walk away, log out and come back.

**Custom workbenches on blocks.** Any block can be bound to its own crafting
menu.

**One recipe, one file** in `plugins/RecipeAdvanced/recipes/`, in folders.
`/ra save <folder> <recipe>` moves a recipe, Tab suggests existing folders.

**`/recipes` — a single tree for everything.** Your recipes and CraftEngine's
in one list with folders. From a recipe you can walk into the recipe of its
ingredient: you see an enchanted sword, click the ingot, and see where the
ingot comes from.

**Items from other plugins.** CraftEngine, ExecutableItems, ExecutableBlocks,
Oraxen, ItemsAdder and MMOItems — as ingredients and as results.

**Recipe conditions.** Permission, world, time of day, experience, drop chance,
extra items in the output.

**`/ra verify`** walks every recipe and says what is wrong with it, before the
players find out.

## Not in the free version

- multiblock stations built out of blocks, with their own menu, holograms and
  particles;
- the 4x4, 5x5 and 6x6 workbenches.

Those classes are not in the free jar at all — not a flag, but absent code.

## Installation

Drop the jar into `plugins/`, restart the server. Permissions:
`recipeadvanced.admin` for the editor and commands, `recipeadvanced.use` to
open crafting menus and `/recipes`.
