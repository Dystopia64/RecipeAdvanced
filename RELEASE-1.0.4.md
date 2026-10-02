# RecipeAdvanced 1.0.4 — free edition

A crafting plugin for Paper. Java 21, exactly one dependency — `paper-api`.

This release follows 1.0.2 directly; 1.0.3 was built but never published, so
everything written for it is here.

## Added

**A recipe that makes several things now looks like one.** In the recipe list
every entry is a single item, so a craft that hands out three read as a craft
that hands out one. Such an entry now cycles through its outputs — each in
turn, about one a second — and spells all of them out in its tooltip. The same
list appears on the result in the station window before you click, and in the
cauldron.

**The recipe page shows every output.** The extras sit beside the main result
instead of being made silently and mentioned nowhere.

**A station can answer to an item from another plugin.** A workbench built on a
CraftEngine item did nothing when the player crafted that item and placed it:
stations are recognised by a marker written into the item this plugin hands
out, and an item obtained any other way carries no marker. A definition may now
name a foreign id — the button in the workbench editor, or `custom-item` in
`workbenches.yml` — and the station answers to that item however the player
came by it: crafted here, crafted in CraftEngine, given by a command, taken in
creative. Namespaces are optional, so `custom_blocks:altar` and `altar` both
match.

**Block states no longer have to match when a station is built.** A shape made
of stairs or logs used to demand that every one of them face exactly as the
author's did, which turns building a station into nudging blocks rather than
following a plan. Only the kind of block matters now; the station's own
rotation and mirroring still work as before. A toggle in the builder restores
the strict behaviour for shapes where facing is the point.

## Fixed

- **An item that comes out second was a dead end.** Walking from an item to the
  recipe that makes it only looked at the main result, so a secondary output
  reported "no recipe — obtained another way" while the recipe sat two slots
  away.
- **Brewing stand recipes could not be made at all.** The stand vets its own
  slots — the ingredient slot takes only what vanilla knows how to brew with —
  so a custom ingredient would not go in and the click simply did nothing.
  Placement is now handled by the plugin for items a recipe names. A recipe
  also describes one ingredient and one bottle, applied to every bottle in the
  stand, the way vanilla brews; it used to spell out all three bottle slots and
  matched only when all three were full.
- **The anvil would not hand over a result that costs nothing.** Vanilla
  refuses to release a result at zero levels: the item was drawn in the slot
  and clicking did nothing.

## Changed

Creating or editing a custom workbench needs the full version. Stations written
earlier keep working in the free one — they load, they open for players, and
their items can still be handed out.

## Not in the free version

- multiblock stations built out of blocks, with their own menu, holograms and
  particles;
- the 4x4, 5x5 and 6x6 workbenches;
- building a station of your own.

## Installation

Drop the jar into `plugins/`, restart the server. Permissions:
`recipeadvanced.admin` for the editor and commands, `recipeadvanced.use` to
open crafting menus and `/recipes`.
