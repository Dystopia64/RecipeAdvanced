# RecipeAdvanced

**Recipes you build with the mouse, not with YAML.**

A crafting plugin for Paper. One file, no external dependencies, no
configuration needed to get started.

---

## The editor

`/ra editor` opens the whole plugin. Put an ingredient in a slot, put the
result in its own, press save. Everything adjustable — cook time, experience,
drop chance, conditions — is a button, not a config key.

## Vanilla stations that actually work

Crafting table, furnace, blast furnace, smoker, campfire, anvil, grindstone,
brewing stand, smithing table, stonecutter, cauldron.

Recipes you write become **real server recipes** and open in the ordinary
vanilla window. Not a chest menu pretending to be a furnace — the furnace.

- **Furnace** — set the cook time and the experience, and let a whole stack
  smelt instead of one item at a time.
- **Smithing table** — carries enchantments from the old item to the new one
  instead of refusing to craft anything enchanted.
- **Cauldron** — the water, lava or powder snow level is shown with coloured
  glass, the right fire has to burn underneath, brewing takes time and throws
  particles, fluid is consumed, and the result floats up out of the pot.
  The brew belongs to the block: walk away, log out, come back.

## Custom workbenches

Bind any block to its own crafting menu, with its own recipes, particles and
permissions.

## `/recipes` — one tree for the whole server

Your recipes and other plugins' in a single list with folders. From a recipe
you can walk into the recipe of its ingredient: you see an enchanted sword,
click the ingot, and find out where the ingot comes from.

## Items from other plugins

CraftEngine, ExecutableItems, ExecutableBlocks, Oraxen, ItemsAdder and
MMOItems work as ingredients and as results. Detection is automatic — nothing
to configure, nothing to install alongside.

## Recipes as files

One recipe, one file, in folders under `plugins/RecipeAdvanced/recipes/`.
`/ra save <folder> <recipe>` moves a recipe; Tab suggests existing folders.
No thousand-line master file to search through.

## Conditions

Permission, world, time of day, required experience, drop chance, extra items
in the output.

## Languages

Chat and menus ship in **English, Russian, Ukrainian, German and Spanish**.
Pick one with `language:` in `config.yml`. The files live in `lang/` and are
yours to edit — updates never overwrite them. Adding a language is copying a
file and translating it.

*(Administration menus are still Russian-only; translating them is in
progress.)*

## Verification

`/ra verify` walks every recipe and reports what is wrong with it — before
your players find out.

---

## Installation

Drop the jar into `plugins/` and restart. That is all.

| Permission | For |
|---|---|
| `recipeadvanced.use` | players: crafting menus and `/recipes` |
| `recipeadvanced.admin` | staff: the editor and `/ra` commands |

## Commands

| Command | What it does |
|---|---|
| `/ra editor` | the recipe editor |
| `/ra save <folder> <recipe>` | move a recipe into a folder |
| `/ra verify` | check every recipe |
| `/ra reload` | reload the configuration |
| `/recipes` | tree of every recipe on the server |

---

## Free and full editions

This is the **free edition**, and it is free for any server, commercial ones
included.

Two things are only in the full edition:

- **multiblock stations** — build a structure out of blocks, click it, and get
  your own crafting menu, with holograms, particles, and placement that works
  at any rotation;
- **the 4x4, 5x5 and 6x6 workbenches**.

That code is not in this jar at all. The classes are not shipped, so there is
no flag to flip and nothing to unlock — what you download is the free edition
end to end.

---

## Terms

Free to use on any number of servers, commercial ones included, with no time
limit. Please link here rather than re-hosting the file, so people get the
current version. The source is not published, and the plugin may not be
decompiled or modified.

Full terms: https://github.com/Dystopia64/RecipeAdvanced/blob/main/LICENSE

---

Bug reports and questions go to the issue tracker.
