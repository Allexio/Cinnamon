# Allexio's Create Plus 

A Create-centred modpack made for me and a bunch of friends (and friends' friends).

We started with a vanilla+ base with Create as a "central" mod and a bunch of performance / cosmetic / QoL mods without changing the content much (except for Create).

We then added a few vanilla-friendly content packs to keep the game fresh for returning players.

In the end this will be a vanilla++ Fabric modpack that satisfies most people who want more of the latest version of Minecraft & Create without adding anything that detracts from the original experience.

# Client setup

## Voice Chat
This is a voice chat enabled server, using the [Plasmo Voice](https://modrinth.com/plugin/plasmo-voice) mod (alongside its compatibility patch for Sound Physics Remastered).

The default option is voice activation. This can be changed by pressing the ```V``` key and setting it up as you want.

By default there are two "ranges" of loudness for when you speak (think of it as screaming or whispering)
- 8 blocks (for whispering to someone without others hearing)
- 64 blocks (for talking to people comfortably on the server without having to stick to them like glue)

## Minimap

The minimap is disabled by default because I feel like it changes the vanilla game too much. You can still access the full map by pressing `M` and clients can re-enable the minimap individually.

# Server setup

## Creating the actual server (using docker)

Docker is a neat utility that allows you to run instanced servers for anything you want.
This allows you to then manage your instance very easily.

If you have a linux machine, chances are you have docker pre-installed.
On windows, you will have to download it separately.

I recommend using docker via [itzg's Minecraft docker image](https://github.com/itzg/docker-minecraft-server).

Here is an example dockerfile that should work out of the box:
(Don't forget to update the modpack server version)

If you do not know how to use a dockerfile, I strongly recommend you look it up because it is really going to simplify your life. 

```docker
version: "3"

services:
  mc:
    image: itzg/minecraft-server
    ports:
      - 25565:25565
      - 24454:24454/udp
    environment:
      EULA: "TRUE"
      VERSION: "1.20.1"
      TYPE: MODRINTH
      MODRINTH_LOADER: FABRIC
      OPS: "[REPLACE WITH LIST OF OPS]"
      MEMORY: "5G"
      MODRINTH_PROJECT: allexio-create+
      MODRINTH_VERSION: 0.9.10
      VANILLATWEAKS_SHARECODE: ilFuDN
    tty: true
    stdin_open: true
    restart: unless-stopped
    volumes:
      # attach a directory relative to the directory containing this compose file
      - ./data:/data

```

Notice how I am forwarding port **24454** for the UDP protocol.

This is for the voice chat mod.

## First time run of the server

When you run the server for the first time, if you want to use the soul link part of [Vanilla Refresh](https://modrinth.com/datapack/vanilla-refresh) (which I strongly recommend), you will have to:
1) Use the `/gamerule keepinventory` command from within the game (needs OP powers)
2) Run the `/function vanillarefresh:settings` command from within the game and navigate to the soul link feature and enable it.

# Full modlist / Credits

Modpack curated, configured & managed by [Allexio](https://modrinth.com/user/allexio).
Many thanks to [Comp500](https://modrinth.com/user/comp500) for the [Packwiz](https://packwiz.infra.link/) utility !

Format:
- [Mod name] (author name) one-line description of the mod
  - _Any modification of default settings or warnings about the specific mod._

## Additional Content / Features

### Create & Friends

- [Create Fabric](https://modrinth.com/mod/create-fabric) ([tropheusj](https://modrinth.com/user/tropheusj)) is the fabric port of the [Create](https://modrinth.com/mod/create) mod we all know and love.
- [Create Slice & Dice](https://modrinth.com/mod/slice-and-dice) ([Possible_Triangle](https://modrinth.com/user/possible_triangle)) adds a way to make [Farmer's Delight](https://modrinth.com/mod/farmers-delight-fabric) recipes with [Create](https://modrinth.com/mod/create-fabric) automation. Also sprinklers.
- [Create: Steam 'n' Rails](https://modrinth.com/mod/create-steam-n-rails) ([IThundxr](https://modrinth.com/user/IThundxr)) adds a cool new monorail system and many other enhancements to the [Create](https://modrinth.com/mod/create-fabric) rail system.
- [COMING SOON] -- Not added yet -- [Create Enchantment Industry Fabric](https://modrinth.com/mod/create-enchantment-industry-fabric) ([MarbleGateKeeper](https://modrinth.com/user/MarbleGateKeeper))

### Storage

- [Iron Chest](https://modrinth.com/mod/cyberanner-ironchest) ([Cyberanner](https://modrinth.com/user/cyberanner)) adds extra variants of chests that hold more items.
  - _Be warned, they will become normal chest size when placing them on moving contraptions._
- [Extended Drawers](https://modrinth.com/mod/extended-drawers/) ([MattiDragon](https://modrinth.com/user/MattiDragon)) allows you to automate item storage using chest groups.
  - _Increased base drawer capacity from 1024 to 2048._

### New blocks / items

- [Chipped](https://modrinth.com/mod/chipped) ([Terrarium](https://modrinth.com/user/Terrarium)) adds cosmetic variants of many block types, each craftable with their own crafting table.
- [Farmer's Delight](https://modrinth.com/mod/farmers-delight-fabric) ([Zifiv](https://modrinth.com/user/Zifiv)) adds new crafting recipes for different kinds of food
- [Supplementaries](https://modrinth.com/mod/supplementaries) ([MehVahdJukaar](https://modrinth.com/user/MehVahdJukaar)) adds many items, blocks, and mechanics associated with them. Mostly cosmetic, but some really neat useful blocks as well.
- [Randomium Ore](https://modrinth.com/mod/randomium-ore) ([MehVahdJukaar](https://modrinth.com/user/MehVahdJukaar)) adds a new ore called randomium that can give you ANY obtainable block in the game, mods included.
- [Nature's Compass](https://modrinth.com/mod/natures-compass) ([Chaosyr](https://modrinth.com/user/Chaosyr)) adds a compass to help players find the biomes they want.
  - _Made it so players start with this in their inventory._
- [Portal Linking Compass](https://modrinth.com/mod/portal-linking-compass) ([Maxoduke](https://modrinth.com/user/Maxoduke)) adds a compass to help with nether portal linking.

### Social

- [plasmo-voice](https://modrinth.com/plugin/plasmo-voice) ([kpids](https://modrinth.com/user/kpids)) adds a really cool and customisable voice chat to the game.
  - _Disabled the default `M` keybinding for muting so it doesn't conflict with the map. Feel free to rebind this as you want._
- [pv-addon-soundphysics](https://modrinth.com/mod/pv-addon-soundphysics) ([kpids](https://modrinth.com/user/kpids)) makes the voice chat use the sound physics from [Sound Physics Remastered](https://modrinth.com/mod/sound-physics-remastered).
- [Sit](https://modrinth.com/mod/bl4cks-sit) ([bl4ckscor3](https://modrinth.com/user/bl4ckscor3)) allows you to sit on slabs.

### Sound

- [Sound Physics Remastered](https://modrinth.com/mod/sound-physics-remastered) ([henkelmax](https://modrinth.com/user/henkelmax)) adds sound reverb, blocks block sound.
  - _There is currently a known issue where sound is not heard underwater._
- [Presence Footsteps](https://modrinth.com/mod/presence-footsteps) ([Sollace](https://modrinth.com/user/Sollace)) better footsteps sounds that depend on what you walk on.
  - _Default volume lowered because it was drowning out other sounds. Can be modified client-side._

### Extra functionality

- [Mine Treasure](https://modrinth.com/datapack/mine-treasure) ([Frozytime](https://modrinth.com/user/Frozytime)) gives you treasure randomly when you mine.
- [Fabric Waystones](https://modrinth.com/mod/fwaystones) ([LordDeatHunter](https://modrinth.com/user/LordDeatHunter)) adds waystones to the game that allow you to teleport in between them.
  - _These are unbreakable and cannot be crafted._
  - _They cost a number of levels to teleport to stop people from abusing this system and instead creating comprehensive railway systems._
- [Armourer's Workshop](https://modrinth.com/mod/armourers-workshop) ([SAGESSE-CN](https://modrinth.com/user/SAGESSE-CN)) lets users make custom armors.

## World Generation / New Structures

### Biomes

- [Terralith](https://modrinth.com/mod/terralith) ([Stardust](https://modrinth.com/user/Stardust)) adds biomes to the overworld.
- [Incendium](https://modrinth.com/mod/incendium) ([Stardust](https://modrinth.com/user/Stardust)) adds biomes to the nether.
- [Nullscape](https://modrinth.com/mod/nullscape) ([Stardust](https://modrinth.com/user/Stardust)) adds biomes to the end.

### Structures

- [ChoiceTheorem's Overhauled Village](https://modrinth.com/mod/ct-overhaul-village) ([ChoiceTheorem](https://modrinth.com/user/ChoiceTheorem)) adds structures.
- [CTOV - Farmer Delight Compat](https://modrinth.com/datapack/ctov-farmers-delight-compat) ([ChoiceTheorem](https://modrinth.com/user/ChoiceTheorem)) compat patch so CTOV structures include some [Farmer's Delight](https://modrinth.com/mod/farmers-delight-fabric) plants.
- [Repurposed Structures - Fabric](https://modrinth.com/mod/repurposed-structures-fabric) ([TelepathicGrunt](https://modrinth.com/user/TelepathicGrunt)) adds structures.
- [Legacies and Legends](https://modrinth.com/mod/legacies-and-legends) ([Rebel459](https://modrinth.com/user/Rebel459)) adds structures, soundtracks, lore notes.

### Worldgen

- [Tectonic](https://modrinth.com/datapack/tectonic) ([Apollo](https://modrinth.com/user/Apollo)) overhauls terrain generation to add cool caves, cliffs and neat little (or big) things

## Quality of Life

- [Xaero's World Map](https://modrinth.com/mod/xaeros-world-map) ([TheXaero](https://modrinth.com/user/thexaero)) adds a world map, accessible by pressing the `M` key.
- [Xaero's Minimap](https://modrinth.com/mod/xaeros-minimap) ([TheXaero](https://modrinth.com/user/thexaero)) adds the ability to add waypoints and see monsters and mobs on the map.
  - The minimap component is actually disabled by default. Clients can re-enable it if they want.
- [ToolTipFix](https://modrinth.com/mod/tooltipfix) ([kyrptonaught](https://modrinth.com/user/kyrptonaught)) fixes tooltips going off-screen.
- [Colorize](https://modrinth.com/mod/colorize) ([PanSzelescik](https://modrinth.com/user/PanSzelescik)) allows you to colour blocks with `right-click` when you hold a tint in your hand.
- [Roughly Enough Items (REI)](https://modrinth.com/mod/rei) ([Shedaniel](https://modrinth.com/user/shedaniel)) adds a pane to the right of your crafting screen that allows you to look up items and recipes.
- [BetterF3](https://modrinth.com/mod/betterf3) ([Treyruffy](https://modrinth.com/user/treyruffy)) adds additional info and colours to your F3. Fully customisable client-side.
- [FallingTree](https://modrinth.com/mod/fallingtree) ([Rakambda](https://modrinth.com/user/Rakambda)) makes trees fall down when you cut any wood block of them with an axe.
- [Why Stacks of 16](https://modrinth.com/mod/why-stacks-of-16) ([LaidBackSloth](https://modrinth.com/user/LaidBackSloth)) makes all stacks 64 instead of some being arbitrarily 16.
- [Double Doors](https://modrinth.com/mod/double-doors) ([Serilum](https://modrinth.com/user/Serilum)) makes all doors/hatches open/close when you interact with one of a connected group.
- [Weaker Spiderwebs](https://modrinth.com/mod/weaker-spiderwebs) ([Serilum](https://modrinth.com/user/Serilum)) makes spiderwebs break when you go through them.
  - _Time set to 1 second._
- [Starter Kit](https://modrinth.com/mod/starter-kit) ([Serilum](https://modrinth.com/user/Serilum)) allows players to start with a default kit of equipment when they spawn in the server.
  - _Set to be 16 bread and a [Nature's Compass](https://modrinth.com/mod/natures-compass)._
- [Better Spawner Control](https://modrinth.com/mod/better-spawner-control) ([Serilum](https://modrinth.com/user/Serilum)) allows you to completely disable spawners by sticking torches all around them.
- [Fish on the Line](https://modrinth.com/mod/fish-on-the-line) ([Serilum](https://modrinth.com/user/Serilum)) allows you to equip a bell offhand when fishing and whenever something is on the line it'll ring.
- [Edibles](https://modrinth.com/mod/edibles) ([Serilum](https://modrinth.com/user/Serilum)) allows you to eat potion ingredients directly for a (very) temporary buff.
- [Softer Hay Bales](https://modrinth.com/mod/softer-hay-bales) ([Serilum](https://modrinth.com/user/Serilum)) makes hay bales fully negate fall damage.
- [Village Bell Recipe](https://modrinth.com/mod/village-bell-recipe) ([Serilum](https://modrinth.com/user/Serilum)) allows you to craft village bells.
- [Bigger Sponge Absorption Radius](https://modrinth.com/mod/bigger-sponge-absorption-radius) ([Serilum](https://modrinth.com/user/Serilum)) makes sponges absorb more.
- [Fall Through Slime](https://modrinth.com/mod/fall-through-slime) ([Serilum](https://modrinth.com/user/Serilum)) allows you to fall through slime blocks if you don't move.
- [Scaffolding Drops Nearby](https://modrinth.com/mod/scaffolding-drops-nearby) ([Serilum](https://modrinth.com/user/Serilum)) makes scaffolding pieces fall next to the one you initially break.
- [Biome Spawn Point](https://modrinth.com/mod/biome-spawn-point) ([Serilum](https://modrinth.com/user/Serilum)) makes world spawn point be in a specific biome
  - _Biome spawn point is set to a floating spring island. Have fun and enjoy the views._
- [Inventory Profiles Next](https://modrinth.com/mod/inventory-profiles-next) ([blackd](https://modrinth.com/user/blackd))
  - _Disabled audio warnings when about to break._
  - _Disabled inventory profiles._
  - _Disabled low-tier item saving._
  - _I wanted to keep the QoL features of this mod without overcrowding the UI. This is all customisable by clients._
- [Zoomify](https://modrinth.com/mod/zoomify) ([isxander](https://modrinth.com/user/isxander)) alows you to zoom in game.
- [Mouse Tweaks](https://modrinth.com/mod/mouse-tweaks) ([YaLTeR](https://modrinth.com/user/YaLTeR))
- [Vanilla Refresh](https://modrinth.com/datapack/vanilla-refresh) ([limesplatus](https://modrinth.com/user/limesplatus)) includes a bunch of vanilla+ QoL additions.
  - _Sitting is disabled to avoid conflicts with [Carry On](https://modrinth.com/mod/carry-on)_.
  - _Entity HP indicator disabled because it was too obnoxious._
  - _Soul Links are NOT enabled by default but I recommend you enable them!!_
- [Carry On](https://modrinth.com/mod/carry-on) ([Tschipp](https://modrinth.com/user/Tschipp)) allows you to carry objects by holding your crouch key and then right-clicking.
  - _Spawners can not be moved for balancing reasons._
- [Better Mount HUD](https://modrinth.com/mod/better-mount-hud) ([Lortseam](https://modrinth.com/user/Lortseam))
- [Accurate Block Placement Reborn](https://modrinth.com/mod/accurate-block-placement-reborn) ([schwar](https://modrinth.com/user/schwar)) allows you to hold right-click to place blocks without any server-based limitations.
- [Bridging Mod](https://modrinth.com/mod/bridging-mod) ([CloudG360](https://modrinth.com/user/CloudG360)) allows you to place blocks where you can't normally see (behind/below other blocks)
- [Better Statistics Screen](https://modrinth.com/mod/better-stats) ([TheCSDev](https://modrinth.com/user/TheCSDev))
- [Jade](https://modrinth.com/mod/jade) ([Snownee](https://modrinth.com/user/Snownee)) tells you what the hell you're looking at. Also more information than you would otherwise know.
- [Better Ping Display [Fabric]](https://modrinth.com/mod/better-ping-display-fabric) ([vladmarica](https://modrinth.com/user/vladmarica)) adds a numerical ping indicator for players in the tab menu.

## Performance

- [Sodium](https://modrinth.com/mod/sodium) ([Jellysquid3](https://modrinth.com/user/jellysquid3))
- [Lithium](https://modrinth.com/mod/lithium) ([Jellysquid3](https://modrinth.com/user/jellysquid3))
- [Starlight](https://modrinth.com/mod/starlight) ([spottedleaf](https://modrinth.com/user/spottedleaf)) adds server-side performance enhancements linked to lighting.
- [Dynamic FPS](https://modrinth.com/mod/dynamic-fps) ([juliand665](https://modrinth.com/user/juliand665)) makes it so that when your game is not focused, it renders at a much lower framerate.
- [Entity Culling](https://modrinth.com/mod/entityculling) ([tr7zw](https://modrinth.com/user/tr7zw)) adds better entity culling when they are not visible to players.
- [Memory Leak Fix](https://modrinth.com/mod/memoryleakfix) ([fxmorin](https://modrinth.com/user/fxmorin)) fixes some memory leak scenarios.
- [Debugify](https://modrinth.com/mod/debugify) ([isxander](https://modrinth.com/user/isxander)) fixes bugs in Minecraft.
- [Concurrent Chunk Management Engine (Fabric)](https://modrinth.com/mod/c2me-fabric) ([ishland](https://modrinth.com/user/ishland)) allows better chunk performance.
- [Krypton](https://modrinth.com/mod/krypton) ([astei](https://modrinth.com/user/astei)) adds server performance improvements.
- [Iris & Oculus Flywheel Compat](https://www.curseforge.com/minecraft/mc-mods/iris-flywheel-compat) ([leon_mout](https://legacy.curseforge.com/members/leon_mout/projects))

## Graphical Additions

- [More Mobs](https://modrinth.com/datapack/more-mobs) ([Tschipcraft](https://modrinth.com/user/Tschipcraft)) adds custom head variants for common mobs. All immersive and cosmetic-only.
- [Spawn Animations](https://modrinth.com/datapack/spawn-animations) ([Tschipcraft](https://modrinth.com/user/Tschipcraft)) adds cool mob spawn animations when they spawn. Imagine a zombie digging out of the dirt. 
- [Glowing Torchflower](https://modrinth.com/mod/glowing-torchflower) ([NikitaCartes](https://modrinth.com/user/NikitaCartes)) makes **torch**flowers.... glow. (it's in the name, Mojang!)
- [Continuity](https://modrinth.com/datapack/continuity) ([tr7zw](https://modrinth.com/user/tr7zw)) makes some block textures "connect" when palced next to each other.
- [Not Enough Animations](https://modrinth.com/mod/not-enough-animations) ([tr7zw](https://modrinth.com/user/tr7zw)) adds some animations to make third-person point of view (or looking at other players) less weird and static.
- [3D Skin Layers](https://modrinth.com/mod/3dskinlayers) ([tr7zw](https://modrinth.com/user/tr7zw)) makes the second layer of minecraft skins a bit more 3D.
- [Falling Leaves](https://modrinth.com/mod/fallingleaves) ([randommcsomethin](https://modrinth.com/user/randommcsomethin)) makes leaves fall from leaf blocks.
- [Iris Shaders](https://modrinth.com/mod/iris) ([coderbot](https://modrinth.com/user/coderbot)) allows you to have shaders.
- [Show Me Your Skin](https://modrinth.com/mod/show-me-your-skin) ([enjarai](https://modrinth.com/user/enjarai)) allows users to show their skin, even when they have armor equipped.
- [Visuality](https://modrinth.com/mod/visuality/) ([PinkGoosik](https://modrinth.com/user/PinkGoosik)) adds little effects for example when you hit a mob.
- [Eating Animation](https://modrinth.com/mod/eating-animation) ([theoness1](https://modrinth.com/user/theoness1)) adds an animation when you eat.
- [cat_jam](https://modrinth.com/mod/cat_jam) ([shmove](https://modrinth.com/user/shmove)) makes cats nod their head to the music of jukeboxes.
- [FootprintParticle](https://modrinth.com/mod/footprintparticle) ([Rivmun](https://modrinth.com/user/Rivmun)) adds footprint particles when you walk on stuff.

## Modding Utilities / Libraries
Don't ask me what any of these do. They're most likely here because they're needed for other things.
- [Appleskin](https://modrinth.com/mod/appleskin) ([Squeek502](https://modrinth.com/user/squeek502))
- [Fabric Language Kotlin](https://modrinth.com/mod/fabric-language-kotlin) ([modmuss50](https://modrinth.com/user/modmuss50))
- [Fabric API](https://modrinth.com/mod/fabric-api) ([modmuss50](https://modrinth.com/user/modmuss50)) is the thing we all need to run fabric mods.
- [YetAnotherConfigLib](https://modrinth.com/mod/yacl) ([isxander](https://modrinth.com/user/isxander))
- [Indium](https://modrinth.com/mod/indium) ([comp500](https://modrinth.com/user/comp500)) is an add-on for Sodium that allows mods to use advanced rendering effects.
- [Moonlight Lib](https://modrinth.com/mod/moonlight) ([MehVahdJukaar](https://modrinth.com/user/MehVahdJukaar)) needed library for [Supplementaries](https://modrinth.com/mod/supplementaries).
- [Collective](https://modrinth.com/mod/collective) ([Serilum](https://modrinth.com/user/Serilum)) is needed for all of [Serilum](https://modrinth.com/user/Serilum)'s mods.
- [Athena](https://modrinth.com/mod/athena-ctm) ([Terrarium](https://modrinth.com/user/Terrarium)) is needed for [Chipped](https://modrinth.com/mod/chipped).
- [Architectury API](https://modrinth.com/mod/architectury-api)
- [Searchables](https://modrinth.com/mod/searchables) ([jaredlll08](https://modrinth.com/user/jaredlll08))
- [Controlling](https://modrinth.com/mod/controlling) ([jaredlll08](https://modrinth.com/user/jaredlll08))
- [modmenu](https://modrinth.com/mod/modmenu) ([Prospector](https://modrinth.com/user/Prospector)) allows clients to easily configure their mods.
- [Patchouli](https://modrinth.com/mod/patchouli) ([Vazkii](https://modrinth.com/user/Vazkii)) allows mod authors to write up custom books with mod tutorials.
- [Cloth Config API](https://modrinth.com/mod/cloth-config) ([Shedaniel](https://modrinth.com/user/shedaniel))
- [libIPN](https://modrinth.com/mod/libipn) ([blackd](https://modrinth.com/user/blackd)) is needed for [Inventory Profiles Next](https://modrinth.com/mod/inventory-profiles-next).

Thanks for using the modpack !
