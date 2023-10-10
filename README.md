# Allexio's Create Plus 

A Create-centred modpack made for me and a bunch of friends (and friends' friends).

We started with a vanilla+ base with Create as a "central" mod and a bunch of performance / cosmetic / QoL mods without changing the content much (except for Create).

We then added a few vanilla-friendly content packs to keep the game fresh for returning players.

In the end this will be a vanilla++ Fabric modpack that satisfies most people who want more of the latest version of Minecraft & Create without adding anything that detracts from the original experience.

# Features

## Create & Friends

Create is an amazing mod that lets you *create* moving contraptions that will help with automating mundane minecraft chores. Think Factorio or Satisfactory, but in Minecraft.

The modpack comes with Create (duh) alongside a few Create add-ons such as:
- Create Steam & Rails (Adds many things related to trains including some really neat monorails!)
- Create Slice & Dice (Adds a few recipes from Farmer's delight and some really cool sprinklers)
- [SOON] Create Enchantment Industry (Adds the possibility to liquefy XP and do some fun enchanting with it)

## Extra Content (that is not Create-related)

### New Items/Blocks/Entities
- Famer's Delight (Adds new ingredients and recipes to make some neat foodstuffs)
- Supplementaries (Adds plenty of new little bits & bobs from signs that point the way to villages to trees that turn into ash when they burn down)
- Chipped (Adds nice block variants for planks, cobble, etc.)

### World Generation
- Terralith
- Tectonic
- Legacies and Legends (Adds new structures, music, lore bites)
- ChoiceTheorem's Overhauled Village (Adds new structures)
- Repurposed Structures (Adds new structures)
- Fabric Waystones (Adds teleport locations in *most* villages)

We want teleport to be a late game option or a last resort.
We want people to create extensive railway networks to link up with their friends.
We balanced Waystones being in game by:
- Making it cost a few levels to teleport. We want people to build railways with Create/Steam & Rails, not just teleport for free accross the map. If you make proper XP management with Create Enchantment industry, then you deserve to be able to teleport more than others. This will be balanced further in a later patch.

# Client setup

## Voice Chat
This is a voice chat enabled server, using the *Plasmo Voice* mod (alongside its compatibility patch for Sound Physics Remastered).

The default option is voice activation. This can be changed by pressing the V key and setting it up as you want.

By default there are two "ranges" of loudness for when you speak (think of it as screaming or whispering)
- 8 blocks (for whispering to someone without others hearing)
- 64 blocks (for talking to people comfortably on the server without having to move near them)

# Server setup

I recommend using docker via [itzg's docker image](https://github.com/itzg/docker-minecraft-server).

Here is an example dockerfile that should work out of the box:
(Don't forget to update the modpack server version)

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
      OPS: "Allexio"
      MEMORY: "5G"
      MODRINTH_PROJECT: allexio-create+
      MODRINTH_VERSION: 0.9.6
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

Please do not forget to do the same in whatever config you use.

# Full modlist / Credits

Modpack curated and managed by Allexio.
Many thanks to [Comp500](https://modrinth.com/user/comp500) for the [Packwiz](https://packwiz.infra.link/) utility !

## Additional Content / Features

### Create & Friends

- [tropheusj](https://modrinth.com/user/tropheusj): [Create](https://modrinth.com/mod/create-fabric)
- [Possible_Triangle](https://modrinth.com/user/possible_triangle): [Create Slice & Dice](https://modrinth.com/mod/slice-and-dice)
- [IThundxr](https://modrinth.com/user/IThundxr):
  - [Create: Steam 'n' Rails](https://modrinth.com/mod/create-steam-n-rails)
- [SOON] -- Not added yet -- [MarbleGateKeeper](https://modrinth.com/user/MarbleGateKeeper): [Create Enchantment Industry Fabric](https://modrinth.com/mod/create-enchantment-industry-fabric)

### Storage

- [Cyberanner](https://modrinth.com/user/cyberanner): [Iron Chest](https://modrinth.com/mod/cyberanner-ironchest)
- [MattiDragon](https://modrinth.com/user/MattiDragon): [Extended Drawers](https://modrinth.com/mod/extended-drawers/)

### New blocks

- [Terrarium](https://modrinth.com/user/Terrarium): [Chipped](https://modrinth.com/mod/chipped)
- [MehVahdJukaar](https://modrinth.com/user/MehVahdJukaar):
  - [Supplementaries](https://modrinth.com/mod/supplementaries)
  - [Randomium Ore](https://modrinth.com/mod/randomium-ore)

### Social

- [kpids](https://modrinth.com/user/kpids):
  - [plasmo-voice](https://modrinth.com/plugin/plasmo-voice)
  - [pv-addon-soundphysics](https://modrinth.com/mod/pv-addon-soundphysics)
- [bl4ckscor3](https://modrinth.com/user/bl4ckscor3): [Sit](https://modrinth.com/mod/bl4cks-sit)

### Sound

- [henkelmax](https://modrinth.com/user/henkelmax): [Sound Physics Remastered](https://modrinth.com/mod/sound-physics-remastered)
- [Sollace](https://modrinth.com/user/Sollace): [Presence Footsteps](https://modrinth.com/mod/presence-footsteps)

### Extra functionality

- [Frozytime](https://modrinth.com/user/Frozytime): [Mine Treasure](https://modrinth.com/datapack/mine-treasure)
- [LordDeatHunter](https://modrinth.com/user/LordDeatHunter): [Fabric Waystones](https://modrinth.com/mod/fwaystones)
- [SAGESSE-CN](https://modrinth.com/user/SAGESSE-CN): [Armourer's Workshop](https://modrinth.com/mod/armourers-workshop)

### New Items

- [Chaosyr](https://modrinth.com/user/Chaosyr): [Nature's Compass](https://modrinth.com/mod/natures-compass)
- [Maxoduke](https://modrinth.com/user/Maxoduke): [Portal Linking Compass](https://modrinth.com/mod/portal-linking-compass)

## World Generation / New Structures

### Biomes

- [Stardust](https://modrinth.com/user/Stardust):
  - [Terralith](https://modrinth.com/mod/terralith)
  - [Incendium](https://modrinth.com/mod/incendium)
  - [Nullscape](https://modrinth.com/mod/nullscape)

### Structures

- [ChoiceTheorem](https://modrinth.com/user/ChoiceTheorem):
  - [ChoiceTheorem's Overhauled Village](https://modrinth.com/mod/ct-overhaul-village)
  - [CTOV - Farmer Delight Compat](https://modrinth.com/datapack/ctov-farmers-delight-compat)
- [TelepathicGrunt](https://modrinth.com/user/TelepathicGrunt): [Repurposed Structures - Fabric](https://modrinth.com/mod/repurposed-structures-fabric)
- [Rebel459](https://modrinth.com/user/Rebel459): [Legacies and Legends](https://modrinth.com/mod/legacies-and-legends)

### Worldgen

- [Apollo](https://modrinth.com/user/Apollo): [Tectonic](https://modrinth.com/datapack/tectonic)

## Quality of Life

- [TheXaero](https://modrinth.com/user/thexaero):
  - [Xaero's World Map](https://modrinth.com/mod/xaeros-world-map)
  - [Xaero's Minimap](https://modrinth.com/mod/xaeros-minimap)
- [kyrptonaught](https://modrinth.com/user/kyrptonaught): [ToolTipFix](https://modrinth.com/mod/tooltipfix)
- [PanSzelescik](https://modrinth.com/user/PanSzelescik): [Colorize](https://modrinth.com/mod/colorize)
- [Shedaniel](https://modrinth.com/user/shedaniel):
  - [Cloth Config API](https://modrinth.com/mod/cloth-config)
  - [Roughly Enough Items (REI)](https://modrinth.com/mod/rei)
- [Treyruffy](https://modrinth.com/user/treyruffy): [BetterF3](https://modrinth.com/mod/betterf3)
- [Rakambda](https://modrinth.com/user/Rakambda): [FallingTree](https://modrinth.com/mod/fallingtree)
- [LaidBackSloth](https://modrinth.com/user/LaidBackSloth): [Why Stacks of 16](https://modrinth.com/mod/why-stacks-of-16)
- [Serilum](https://modrinth.com/user/Serilum):
  - [Double Doors](https://modrinth.com/mod/double-doors)
  - [Weaker Spiderwebs](https://modrinth.com/mod/weaker-spiderwebs)
  - [Starter Kit](https://modrinth.com/mod/starter-kit)
  - [Better Spawner Control](https://modrinth.com/mod/better-spawner-control)
  - [Fish on the Line](https://modrinth.com/mod/fish-on-the-line)
  - [Edibles](https://modrinth.com/mod/edibles)
  - [Softer Hay Bales](https://modrinth.com/mod/softer-hay-bales)
  - [Village Bell Recipe](https://modrinth.com/mod/village-bell-recipe)
  - [Bigger Sponge Absorption Radius](https://modrinth.com/mod/bigger-sponge-absorption-radius)
  - [Fall Through Slime](https://modrinth.com/mod/fall-through-slime)
  - [Scaffolding Drops Nearby](https://modrinth.com/mod/scaffolding-drops-nearby)
- [blackd](https://modrinth.com/user/blackd):
  - [Inventory Profiles Next](https://modrinth.com/mod/inventory-profiles-next)
  - [libIPN](https://modrinth.com/mod/libipn)
  - [isxander](https://modrinth.com/user/isxander): [Zoomify](https://modrinth.com/mod/zoomify)
- [YaLTeR](https://modrinth.com/user/YaLTeR): [Mouse Tweaks](https://modrinth.com/mod/mouse-tweaks)
- [limesplatus](https://modrinth.com/user/limesplatus): [Vanilla Refresh](https://modrinth.com/datapack/vanilla-refresh)
- [Tschipp](https://modrinth.com/user/Tschipp): [Carry On](https://modrinth.com/mod/carry-on)
- [Lortseam](https://modrinth.com/user/Lortseam): [Better Mount HUD](https://modrinth.com/mod/better-mount-hud)
- [schwar](https://modrinth.com/user/schwar): [Accurate Block Placement Reborn](https://modrinth.com/mod/accurate-block-placement-reborn)
- [CloudG360](https://modrinth.com/user/CloudG360): [Bridging Mod](https://modrinth.com/mod/bridging-mod)
- [TheCSDev](https://modrinth.com/user/TheCSDev): [Better Statistics Screen](https://modrinth.com/mod/better-stats)
- [Snownee](https://modrinth.com/user/Snownee): [Jade](https://modrinth.com/mod/jade)

## Performance

- [Jellysquid3](https://modrinth.com/user/jellysquid3):
  - [Sodium](https://modrinth.com/mod/sodium)
  - [Lithium](https://modrinth.com/mod/lithium)
- [spottedleaf](https://modrinth.com/user/spottedleaf): [Starlight](https://modrinth.com/mod/starlight)
- [juliand665](https://modrinth.com/user/juliand665): [Dynamic FPS](https://modrinth.com/mod/dynamic-fps)
- [vladmarica](https://modrinth.com/user/vladmarica): [Better Ping Display [Fabric]](https://modrinth.com/mod/better-ping-display-fabric)
- [tr7zw](https://modrinth.com/user/tr7zw): [Entity Culling](https://modrinth.com/mod/entityculling) - 
- [fxmorin](https://modrinth.com/user/fxmorin): [Memory Leak Fix](https://modrinth.com/mod/memoryleakfix)
- [isxander](https://modrinth.com/user/isxander): [Debugify](https://modrinth.com/mod/debugify)
- [ishland](https://modrinth.com/user/ishland): [Concurrent Chunk Management Engine (Fabric)](https://modrinth.com/mod/c2me-fabric)
- [astei](https://modrinth.com/user/astei): [Krypton](https://modrinth.com/mod/krypton)
- [leon_mout](https://legacy.curseforge.com/members/leon_mout/projects): [Iris & Oculus Flywheel Compat](https://www.curseforge.com/minecraft/mc-mods/iris-flywheel-compat)

## Graphical Additions

- [Tschipcraft](https://modrinth.com/user/Tschipcraft):
  - [More Mobs](https://modrinth.com/datapack/more-mobs)
  - [Spawn Animations](https://modrinth.com/datapack/spawn-animations)
- [NikitaCartes](https://modrinth.com/user/NikitaCartes): [Glowing Torchflower](https://modrinth.com/mod/glowing-torchflower)
- [tr7zw](https://modrinth.com/user/tr7zw):
  - [Not Enough Animations](https://modrinth.com/mod/not-enough-animations)
  - [3D Skin Layers](https://modrinth.com/mod/3dskinlayers)
- [randommcsomethin](https://modrinth.com/user/randommcsomethin): [Falling Leaves](https://modrinth.com/mod/fallingleaves)
- [coderbot](https://modrinth.com/user/coderbot): [Iris Shaders](https://modrinth.com/mod/iris)
- [enjarai](https://modrinth.com/user/enjarai): [Show Me Your Skin](https://modrinth.com/mod/show-me-your-skin)
- [PinkGoosik](https://modrinth.com/user/PinkGoosik): [Visuality](https://modrinth.com/mod/visuality/)
- [theoness1](https://modrinth.com/user/theoness1): [Eating Animation](https://modrinth.com/mod/eating-animation)
- [shmove](https://modrinth.com/user/shmove): [cat_jam](https://modrinth.com/mod/cat_jam)
- [Rivmun](https://modrinth.com/user/Rivmun): [FootprintParticle](https://modrinth.com/mod/footprintparticle)

## Modding Utilities / Libraries

- [Squeek502](https://modrinth.com/user/squeek502): [Appleskin](https://modrinth.com/mod/appleskin)
- [modmuss50](https://modrinth.com/user/modmuss50):
  - [Fabric Language Kotlin](https://modrinth.com/mod/fabric-language-kotlin)
  - [Fabric API](https://modrinth.com/mod/fabric-api)
- [isxander](https://modrinth.com/user/isxander): [YetAnotherConfigLib](https://modrinth.com/mod/yacl)
- [comp500](https://modrinth.com/user/comp500): [Indium](https://modrinth.com/mod/indium)
- [MehVahdJukaar](https://modrinth.com/user/MehVahdJukaar): [Moonlight Lib](https://modrinth.com/mod/moonlight)
- [Serilum](https://modrinth.com/user/Serilum): [Collective](https://modrinth.com/mod/collective)
- [Terrarium](https://modrinth.com/user/Terrarium):
  - [Athena](https://modrinth.com/mod/athena-ctm)
  - [Architectury API](https://modrinth.com/mod/architectury-api)
- [jaredlll08](https://modrinth.com/user/jaredlll08):
  - [Searchables](https://modrinth.com/mod/searchables)
  - [Controlling](https://modrinth.com/mod/controlling)
- [Prospector](https://modrinth.com/user/Prospector): [modmenu](https://modrinth.com/mod/modmenu)
- [Vazkii](https://modrinth.com/user/Vazkii): [Patchouli](https://modrinth.com/mod/patchouli)