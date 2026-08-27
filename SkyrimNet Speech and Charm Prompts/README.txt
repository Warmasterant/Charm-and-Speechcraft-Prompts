SkyrimNet Charm Tiers
=====================

Prompt-only SkyrimNet integration. This mod contains no ESP/ESL, DLL, PEX, or Papyrus script,
so it does not consume a plugin slot and creates no persistent save state.

Install / enable
----------------
Enable this folder in MO2 after SkyrimNet and any SkyrimNet/SeverActions prompt modules.
The file has a unique name, so it does not replace an original prompt file.

How it works
------------
SkyrimNet's has_magic_effect(actorUUID, "EditorID") decorator checks the NPC who is about to
speak or have an action selected. The prompt selects the highest active tier, so stronger active
effects override lower ones. It only changes LLM context and action preference; it never grants
actions that SkyrimNet/SeverActions do not mark eligible.

Tier I - Gentle magical influence
  * Vanilla-style Calm: InfluenceAggDownFFAimed
  * Odin Calm and Calming Rune effects
  * True Thane city Pacify effects

Tier II - Potent charm
  * Reliquary of Myth: Vile's Charm (ROM_DA03_Charm_Effect)
  * Master's Gaze and Master of the Mind single-target Calm
  * Sacrosanct Vampire's Seduction variants
  * Arcanum Enraptured
  * Lost Grimoire Ensnare
  * Odin Calming Rune with Master of the Mind

Tier III - Strong compulsion
  * Vanilla/Odin Pacify
  * Master of the Mind area Charm
  * Arcanum Mesmeric Orb and Mind Twist Calm

Tier IV - Overwhelming compulsion
  * Odin Harmony
  * Master of the Mind Harmony-area effect
  * Lost Grimoire Enthrall

Deliberate exclusions
----------------------
The load order has many other records carrying MagicInfluenceCharm. They are intentionally not
treated as conversational charm: NPC-only quest effects, self/caster effects, creature-only
calming, random Wabbajack outcomes, follower-control utilities, incidental enchantment procs,
and effects whose purpose is harm, sleep, or confusion rather than social influence.

The source records remain untouched. To add another spell later, add its active MGEF EditorID to
the appropriate conditional in 0315_skyrimnet_charm_tiers.prompt.
