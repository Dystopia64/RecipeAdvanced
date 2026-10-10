# RecipeAdvanced 1.0.6 — free edition

A crafting plugin for Paper. Java 21, exactly one dependency — `paper-api`.

This release follows 1.0.2 directly. 1.0.3 to 1.0.5 were built but never
published, so everything written for them is here too.

The three it exists for: saving a recipe no longer stalls the server, the
recipe tree is ordered so an armour set stays together, and a recipe switched
off by an admin stays off across a restart.

## Added

**A recipe that makes several things now looks like one.** In a recipe list
every tile is a single item, so a craft that hands out three read as a craft
that hands out one. Such a tile now cycles through its outputs — each in turn,
about one a second — and spells all of them out in its tooltip. This holds in
both lists: `/recipeadvanced` and the `/recipes` tree. The same list appears
on the result in the station window before you click, and in the cauldron. On
a recipe page the extras sit beside the main result instead of being made
silently and mentioned nowhere.

**A recipe says where it is made.** The arrow between ingredients and result
is now the station itself — the workbench's own block, the lodestone of a
built station, the furnace or the stonecutter of a vanilla one. The arrow said
only that one thing becomes another, which the layout had already said; the
station is the thing a player has to go and find.

**A cauldron recipe is drawn as a cauldron.** It used to be six slots floating
in an empty window: nothing said which pot, how full it had to be, or over
what fire, all of which the recipe already knows and the player has to match
before anything cooks. Every page that shows a cauldron recipe — this plugin's
own, the `/recipes` tree, and the editor — now carries the pot's own gauge,
fluid and fire, arranged as the cauldron menu arranges them. The block sits
one row higher there, because the bottom row of those windows is buttons.

**A recipe of ours is drawn in its station's own slots.** The `/recipes` tree
describes a foreign recipe as rows of ingredients, which is all the Bukkit API
gives it. Ours were shown the same way, so a cauldron lost its funnel shape
and, with rows capped at five, its sixth ingredient outright.

**A station can answer to an item from another plugin.** A workbench built on
a CraftEngine item did nothing when the player crafted that item and placed
it: stations are recognised by a marker written into the item this plugin
hands out, and an item obtained any other way carries no marker. A definition
may now name a foreign id — the button in the workbench editor, or
`custom-item` in `workbenches.yml` — and the station answers to that item
however the player came by it. Namespaces are optional, so
`custom_blocks:altar` and `altar` both match.

**Block states no longer have to match when a station is built.** A shape made
of stairs or logs used to demand that every one of them face exactly as the
author's did, which turns building a station into nudging blocks rather than
following a plan. Only the kind of block matters now; the station's own
rotation and mirroring still work as before. A toggle in the builder restores
the strict behaviour for shapes where facing is the point.

## Fixed

- **Saving a recipe stalled the server.** Pressing save in the editor rebuilt
  the whole vanilla registry: every recipe the plugin owns taken out of the
  server and put back, to publish a change to one of them. The server runs its
  own `finalizeRecipeLoading` inside every `addRecipe`, rebuilding ingredient
  tables and reloading advancement data for every player online, so the real
  cost was one full reload per recipe on the list — a server with sixty of
  them dropped to 17 TPS on every save. Only the saved recipe is re-registered
  now, so a save costs the same whether the server has five recipes or five
  hundred.
- **A recipe switched off by an admin came back on every restart.** The
  removals were made while plugins were enabling and did not last: another
  plugin finishes its own startup a few seconds later, rebuilds the recipe
  registry from the data packs, and takes every disabled recipe back out of
  the bin with it. Measured on a server with CraftEngine — gone at enable,
  still gone when the server announced it was ready, back half a minute after
  that — and only `/ra reload`, run late enough, made it stick. The removals
  are now re-asserted if anything undoes them, so no reload is needed.
- **A deleted recipe stayed craftable.** It vanished from the plugin's list
  and from disk, but the copy the server had been given was never taken back,
  so it kept working at the furnace or the smithing table until a restart.
- **A vanilla ingredient was a dead end.** Clicking an iron ingot in a recipe
  said it had no recipe — a strange thing for a recipe book to say. The
  lookup only searched this plugin's own recipes and the ones other plugins
  added; vanilla was left out, so a chain stopped at the first item we had not
  written ourselves. It walks all the way down to raw materials now.
- **A craft announced itself by its id.** «Crafted s_knife» — the id is a key,
  not a name, and a recipe nobody renamed had nothing else to say. It is
  announced as the thing it made instead.
- **A cauldron of lava burned what it brewed.** The result is spawned inside
  the block it came out of, which for a lava cauldron means inside the lava:
  it took fire damage on its first tick and was gone before it had risen out
  of the pot. The experience orb went the same way.
- **The `/recipes` tree scattered armour sets.** Everything was ordered by
  registry key, which for another plugin's set usually starts with the piece —
  `boots_ruby`, `boots_sapphire` — so the page came out as every pair of
  boots, then every helmet, with the sets shuffled through each other. Foreign
  recipes are ordered by the name on the item now, which keeps a set together,
  and from its first letter, so a resource pack's leading glyph no longer
  separates an item from its own set. This plugin's own recipes are ordered by
  their id instead: an admin groups their recipes by naming them
  `hunter_helmet`, `hunter_boots`, and that grouping lives in the id — it
  rarely survives into the name on the tile, which may be a plain vanilla one
  or may put the set word last. Our recipes were also appended after the
  sorted foreign ones rather than among them, and so always trailed the page.
- **An item that comes out second was a dead end.** Walking from an item to
  the recipe that makes it only looked at the main result, so a secondary
  output reported "no recipe — obtained another way" while the recipe sat two
  slots away.
- **Brewing stand recipes could not be made at all.** The stand vets its own
  slots — the ingredient slot takes only what vanilla knows how to brew with —
  so a custom ingredient would not go in and the click simply did nothing.
  Placement is now handled by the plugin for items a recipe names. A recipe
  also describes one ingredient and one bottle, applied to every bottle in the
  stand, the way vanilla brews; it used to spell out all three bottle slots
  and matched only when all three were full.
- **The anvil would not hand over a result that costs nothing.** Vanilla
  refuses to release a result at zero levels: the item was drawn in the slot
  and clicking did nothing.

## Changed

Creating or editing a custom workbench needs the full version. Stations
written earlier keep working in the free one — they load, they open for
players, and their items can still be handed out.

## Not in the free version

- multiblock stations built out of blocks, with their own menu, holograms and
  particles;
- the 4x4, 5x5 and 6x6 workbenches;
- building a station of your own.

## Installation

Drop the jar into `plugins/`, restart the server. Permissions:
`recipeadvanced.admin` for the editor and commands, `recipeadvanced.use` to
open crafting menus and `/recipes`.
