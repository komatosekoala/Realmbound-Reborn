# Realmbound: Ascendance

Game overview and implemented features  
Release summary | 16 October 2026

## The game

Realmbound: Ascendance is a third-person celestial dark-fantasy action RPG for Windows, playable alone or in cooperative parties of up to four players. Its current playable structure is a six-wave expedition through three connected regions. The focus is deliberate combat, evolving equipment combinations, preparation between encounters, and a boss battle at the end of every wave.

The setting combines weathered fantasy ruins, monumental stone architecture, celestial energy, and mysterious magical machinery. The three regions are the Verdant Reliquary, the Astral Crossing, and the Cathedral of the Last Sun. Two waves belong to each region. The established map layout and dimensions are preserved in this release.

This summary describes the implemented game. It does not present planned features as completed systems. The release is a bounded cooperative expedition, rather than a large open-world campaign, MMO, or branching narrative RPG.

## The expedition loop

The central sequence is:

> Combat wave → reward pedestal and preparation → boss encounter → victory → next wave or movement into the next region.

Ordinary encounters mix melee pursuers, ranged attackers, agile swarmers, and tougher elites. Enemy health, density, and pressure respond to the wave, party size, difficulty, and elapsed expedition time. Spawn warnings provide notice before incoming enemies enter the fight. Archetypes have different movement and attack behavior rather than sharing one uniform stat profile.

Normal, Hard, and Brutal difficulty options are available. Normal is the intended starting difficulty. The host controls room difficulty and starts or restarts the expedition. Encounter progression and victory state are authoritative, with safeguards against duplicate boss activation and repeated reward claims.

Intermissions are active preparation periods. Players can inspect and equip gear, select pedestal rewards, move, and use permitted abilities, including healing. Healing still consumes its normal resource and respects its cooldown; the pause between encounters is not an unlimited free-healing mode. Warrior preparation includes a limited resource provision for healing when necessary.

## Three playable classes

Each class has a primary attack, secondary area ability, self-heal, mobility action, and ultimate. Combat inputs are left mouse for primary, right mouse for secondary, Shift for mobility, 1 for healing, and R for the ultimate. Abilities use class resources and cooldowns. Equipment can modify performance within bounded calculations.

### Warrior

A close-range fighter using rage, sweeping melee contacts, impact effects, and a forward charge. Its kit is Sword cut, Faultline, Second wind, Charge, and Worldbreaker. Legendary mechanics include Bloodbound lifesteal, Seismic third-hit area damage, and Reprisal charge/parry interactions.

Base primary damage: 12.3. Base primary cooldown: 0.452 seconds, before equipment and other modifiers.

### Mage

A ranged spellcaster using mana, visible magical projectiles, a ground-targeted area attack, self-restoration, mobility, and a powerful magical ultimate. Its kit is Spark bolt, Astral Frost, Restore, Blink dash, and Starfall Lance. Legendary mechanics include Overflow power at high mana, Echo follow-up bursts, and Afterimage attacks associated with mobility.

Base primary damage: 10.6. Base primary cooldown: 0.429 seconds, before equipment and other modifiers.

### Hunter

A ranged fighter using energy, narrow arrow projectiles, an area volley, field healing, evasive movement, and a piercing ultimate. Its kit is Quick arrow, Sunburst Volley, Field mend, Evasive leap, and Heavenspear. Legendary mechanics include Quickdraw primary-attack benefits, Ricochet follow-up damage, and Threadneedle piercing.

Base primary damage: 9.4. Base primary cooldown: 0.381 seconds, before equipment and other modifiers.

## Combat feel and mechanical rules

The recent balance direction is retained: baseline primary attack frequency is approximately 58% lower than the earlier rapid-fire version, while approved primary damage per hit remains unchanged. Primary animation timing, admission cooldowns, release timing, and collision handling are coordinated. Practical firing frequency also depends on resources, input, movement, and item bonuses.

Warrior attacks use melee contact checks. Mage and Hunter ranged attacks create visible gameplay projectiles that travel and collide. One cast tracks its resolved contacts so overlapping split projectiles cannot multiply damage against the same target unintentionally. Item-driven piercing, ricochets, and secondary effects follow their own limits.

The server validates damage and ability activation. Health, armor, haste, critical effects, healing, and item bonuses use bounded calculations intended to prevent runaway stacking. Enemy threats depend on positioning, attack commitments, and readable windups as well as damage. Mobility, cover, and moving out of marked attack shapes remain central defensive tools.

## Six boss encounters

Every wave culminates in a named encounter:

1. Cairn, the Oathbreaker: sweeping frontal attacks, charges, and halo patterns.
2. Vesper, Keeper of the Hollow Sun: halos, radial volleys, and sanctuary zones.
3. The Glass Choir: projectile fans, targeted starfalls, and crossing attack lanes.
4. Orrery, the Divided Sentinel: celestial crosses, sweeps, and sanctuary pressure.
5. Ashen Pilgrim: charges, starfalls, and close-range attacks, with a later-phase variation.
6. The Astral Warden: a combination of the principal patterns plus two seal objectives.

These are six mechanically differentiated encounters; they should not be interpreted as six wholly unrelated bespoke creature models.

Boss patterns include frontal sweeps, long charge lanes, ring-shaped hazards, full-circle projectile volleys, crossing lanes, targeted ground impacts, and attacks that require entering a sanctuary. Warnings and damage use a shared replicated attack commitment so the displayed geometry corresponds to the server's strike. Individual strikes reject repeated damage from the same commitment.

Boss base health retains the recent 3.5x increase, with additional encounter scaling. Boss attacks retain the recent roughly 4x base-damage multiplier, faster arena-reaching projectiles, increased coverage, and shorter recovery periods. Armor and defensive effects still influence received damage. Boss durability and threat are intentionally separate tuning controls.

The Warden has shielded transitions near two-thirds and one-third health. Players must charge seals while dealing with targeted hazards before normal damage can resume. The encounter culminates in the final expedition result. Boss introductions, warning text, attack effects, and encounter music support the spectacle.

## Loot, equipment, and build variety

Equipment has five slots: chest, gloves, legs, main hand, and off hand. Rarities are Uncommon, Rare, Epic, and Legendary. Gear carries power, stat bonuses, and, where applicable, special modifiers or class-specific legendary mechanics. Damage, health, speed, regeneration, haste, healing, armor, and critical rating are represented in the equipment system.

The seven shared modifier families are:

- **Splinter:** spreads projectile attacks across targets and adds weaker melee shards.
- **Thread:** adds projectile piercing with reduced follow-through damage.
- **Return:** adds ricochet or nearby melee-chain behavior.
- **Ember:** ignites enemies.
- **Rime:** slows enemies and can combine with Ember for a shattering reaction.
- **Tempest:** makes critical hits arc to nearby enemies.
- **Covenant:** grants defensive shielding from critical hits and healing, with offensive interaction.

Run relics provide another layer of temporary build growth. The implemented roster includes Ember tooth, Heartstone, Wind feather, Source bead, Clock shard, Life bloom, Iron charm, Keen lens, Slipstream biscuit, Pocket undertow, Backfire spool, and Mercy bell. They affect statistics or actions. Examples include pulling ordinary enemies toward a secondary attack, leaving a delayed aftershock after mobility, and creating a healing ward for allies.

Gear drops and run-item drops remain separate reward systems. The current configured probabilities are 18.62% for the relevant gear-drop roll and 37.24% for the relevant run-item roll, each about 33% above its earlier setting. These are probabilities, not guaranteed per-wave counts. Pedestal rewards and guaranteed progression grants are distinct from ordinary random drops.

Loot acquisition and reward ownership are server-controlled. Private drop presentation prevents another player's personal loot from appearing as locally claimable equipment. Pedestal selections are checked for eligibility and duplicate redemption. Item inspection and comparison expose the effects needed to make equipment decisions.

## Saves and continue

Character equipment, equipped selections, best-wave accomplishments, and victories persist through normal application restarts. A saved character can be continued from the menu. Progress is saved at meaningful progression events, equipment changes, and normal exit paths.

Continue preserves permanent character development; it is not a snapshot that resumes every enemy, projectile, temporary relic, and position halfway through a battle. Temporary run state resets when a new expedition starts.

Save files are versioned. Writes use a temporary file, verification, and a backup before replacing the active save. Invalid or incompatible data is guarded against overwriting, and a valid backup can be recovered. Profiles distinguish character class and player identity. In cooperative sessions progression follows the host/server authority model; there is no advertised cloud-sync or account-wide cross-host portability system.

## Cooperative play

The menu supports hosting a co-op room and joining a host by IPv4 address with an optional port. The game supports one to four players. The host runs the authoritative simulation for encounters, damage, rewards, equipment ownership, and saved progression. Compatible-build admission helps prevent mismatched gameplay protocols from connecting.

Cooperative mechanics include multiple class roles, shared encounter objectives, party-scaled pressure, and ally healing wards when supported by the acquired relics. Each player's equipment and reward ownership remain distinct.

The release has been exercised with local multi-instance cooperative checks. Those checks establish basic connection, synchronization, ownership, and progression behavior on one computer; they do not certify every separate-computer connection or Internet network configuration. Public matchmaking and dedicated-server hosting are not claimed features of this release.

## Visuals, audio, and interface

The game uses Unreal Engine 5.8, DirectX 12, Shader Model 6, Nanite-optimized environment assets, Lumen lighting/reflections, virtual shadows, atmospheric fog, and animated character models. Greystone, Gideon, Sparrow, Sevarog, Minion, and Dark Ruins-derived production assets contribute to the current presentation, alongside the project's custom effects and systems. Attribution and notices accompany the distribution.

Projectile trails, area markers, impacts, boss tells, loot acquisition effects, and class-specific sounds help communicate combat events. Music responds to encounter state, including boss fights. World ambience, interface feedback, and combat cues have separate volume controls.

The interface includes health and class resources, ability cooldowns, encounter objectives, boss health and warning text, relic inspection, equipment information, item comparisons, pickup notifications, and expedition results. Equipment and damage-meter display options are available. HUD size can be adjusted.

Settings include windowed/fullscreen/borderless modes, display resolution, graphics presets, resolution scale, frame caps, VSync, audio controls, and configurable supported movement bindings. The combat kit retains fixed primary bindings. F5 replay and menu restart paths have dedicated loading checks.

## Release optimization and distribution

The latest pass targets rendering overhead rather than changing gameplay or reducing the map. The Epic preset retains native main-image rendering, TSR anti-aliasing, Lumen reflections, Nanite geometry, fog, and virtual shadows. Temporal history size, fog sampling density, and soft-shadow sampling are tuned to reduce GPU work. These adjustments can subtly affect temporal stability and shadow/fog detail; they do not remove those systems. Lower presets remain available for users who prefer additional speed.

The package uses stronger lossless compression for cooked assets. The compact ZIP excludes redundant or irrelevant runtime-distribution files, while retaining the required x64 runtime installer and the actual game content. Original source assets, development history, saves, and previous releases remain preserved separately.

Extract the entire archive before launching Realmbound.exe. Sending the executable alone is insufficient because the adjacent engine libraries and cooked content are required. This is a Windows x64 packaged build, not a source-project distribution.

## Verification and limitations

Focused automation covers combat ratings, cast timing and contacts, item interactions, saves, intermission abilities, ordinary enemy threat, and boss damage/coverage. Packaged checks exercise launch, persistence across restart, replay loading, important material initialization, and representative encounter behavior. Earlier same-binary co-op tests cover six-boss progression and duplicate-reward rejection.

Measured performance is reported for the Ryzen 7 9800X3D and RTX 4070 SUPER at native 2560x1440 with VSync off, an uncapped frame rate, no dynamic resolution, and no frame generation. Measurements are short repeatable captures, not guarantees for all scenes. Boss automation screenshots introduce known capture stalls; raw and explicitly filtered measurements must be distinguished.

The ambitious 160-180 native FPS target has not been achieved. Human playtesting remains the deciding evidence for enjoyment, readability in motion, difficulty, and encounter pacing. No automated fixture is presented as proof of human balance acceptance.

## Measured results for this release

Hardware: AMD Ryzen 7 9800X3D and NVIDIA GeForce RTX 4070 SUPER.
Conditions: native 2560x1440, Epic preset, 100% main render scale, uncapped,
VSync off, no dynamic resolution, no frame generation. The game was rendered
offscreen. Analysis uses approximately 20 seconds after startup warm-up.

Previous final package, ordinary combat:
  Average 82.3 FPS; 1% low 64.1 FPS.
New compact package, ordinary combat:
  Average 89.9 FPS; 1% low 71.0 FPS; maximum measured frame 18.28 ms.
  Average improvement: approximately 9.2% over the previous final package.

Matched candidate comparison, local four-player simulation:
  Average 82.5 -> 87.7 FPS; 1% low 63.0 -> 64.4 FPS.
  One rendered host and three headless clients ran on the same computer.

Matched candidate comparison, early boss encounters:
  Raw average 81.7 -> 88.7 FPS; raw 1% low 17.8 -> 18.1 FPS.
  The automated fixture saves screenshots during combat, causing large stalls.
  Excluding those screenshot stalls: average 84.7 -> 92.0 FPS.
  The similarly filtered 1% low changed 71.7 -> 66.8 FPS; not every metric improved.

The packaged ordinary-combat result confirms the settings are applied without
candidate console overrides. Comparison images and fresh region-loading checks
showed no obvious loss of essential scene content or attack markers. These are
short observations; fine temporal detail and subjective motion quality still
benefit from human evaluation. No further attack, boss-health, loot, or map-size
changes were introduced in this optimization pass.

Distribution reduction uses Oodle Kraken level 5 asset compression and stronger
ZIP compression where useful. Removed distribution-only entries are the duplicate
Prerequisites/vc_redist.x64.exe copy, the ARM64 runtime installer, and Vulkan
validation/diagnostic layers. The x64 installer under Engine/Extras/Redist/en-us
remains available. Game assets, audio, animations, all regions, and required DX12
runtime components remain included. The archive is checked for complete readable
entries and CRC integrity before release designation.
