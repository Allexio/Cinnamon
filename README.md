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

Notice how I am forwarding port 24454 for the UDP protocol.

This is for the voice chat mod.

Please do not forget to do the same in whatever config you use.
