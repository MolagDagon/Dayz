PATROL_PARAMETERS_INFORMATION


# 1 Persist

    If Name is given and unique, alive patrol members will be saved when despawning (also at server restarts) and restored with all their gear at the last position when respawning. Note this is only supported if ObjectClassName is not set.

# 2 Faction

    This setting allows you to specify what faction this patrol will be in. You can currently choose between these factions:

    West -> Friendly toward Civilian and West

    East -> Friendly toward Civilian and East

    Raiders -> Hostile toward everyone, including other Raiders (unless they are part of the same group)

    Mercenaries -> Hostile toward everyone except other Mercenaries

    Civilian -> Friendly toward any faction that is not hostile to them (so by default, West, East, Civilian, Passive and Guards)

    Passive -> Completely passive, will not even look at other entities.

    Guards -> Always friendly toward other guards, friendly toward other AI and players as long as they don't raise their weapon

    InvincibleGuards -> Like guards, but can't be killed.

    Shamans -> Friendly towards other shamans, won't attack or be attacked by Zs and animals

    Observers -> Will only look at other entities, but not engage in combat.

    InvincibleObservers -> Like observers, but can't be killed.

    YeetBrigade -> Same as guard faction but won't pick up weapons and has insanely strong melee (one-shots bears with their fists) that send their victim flying. More of a showcase for faction abilities than something you should actually use.

    InvincibleYeetBrigade -> Like YeetBrigade, but can't be killed.

    Brawlers -> Friendly toward Civilian and Brawlers. Very strong melee (not as strong as YeetBrigade) that can one-shot Infected with fists.

    RANDOM -> Chooses one of the above factions that are not invincible, observer or passive and don't have special melee abilities.

# 4 Formation
    Formation of the group. Valid values Column, File, Vee, Wall or RANDOM.

# 5 FormationScale
    How far apart the individual formation positions are.

    For formations that are on a grid (like Vee, InvVee, Wall, Column and InvColumn), the value determines the side length of the grid in meters.

    For formations that are not on a grid (like Star, StarDot, Circle and CircleDot), the value roughly determines the distance between the positions (in case of star-based formations, the inner positions, with distances between outer positions scaled accordingly).

    Default: -1.0 (uses AISettings.json value, which defaults to 1.0)

# 6 FormationLooseness
    How loose the formation is, i.e. how close each AI tries to stay to their respective position in the formation. In meters.

    Examples:

    0 = will try to follow formation exactly
    0.5 = loose formation
    1.0 = very loose formation

# 7 Loadout
    The name of your loadout.json containing the weapons, outfit and gear they will carry with them. For example "HumanLoadout"

# 8 Units
    If you want specific AI to spawn, enter the eAI classnames here, else leave empty. Note that it will pick classnames randomly from the list UNLESS you set NumberOfAI (see below) to EXACTLY the number of classnames you enter here (in which case it will spawn the exact set you entered).

    Example:

        "Units": [
            "eAI_SurvivorF_Eva",
            "eAI_SurvivorM_Mirek",
            "eAI_SurvivorF_Judy",
            "eAI_SurvivorM_Guo"
        ],

# 9 NumberOfAI
    How many AI will be in this patrol.

    If you set this setting to a negative number, the system will spawn a random amount of AI between 1 and the specified number with the sign removed.

    For example -6 will tell the game to spawn between 1 and 6 AI.

# 10 Behaviour
    Desired behaviour of your patrol.

    HALT -> The patrol won't move
    ONCE -> The patrol will follow the waypoints from start to finish, then stop.
    LOOP -> The patrol will follow the waypoints from start to finish, then return to start and repeat. Should only be used if the last waypoint is close to the first waypoint, as the AI will just go in a more or less straight line from finish back to start.
    ALTERNATE -> The patrol will follow the waypoints from start to finish, then from finish to start and repeat
    HALT_OR_ALTERNATE -> The patrol will spawn with a random behaviour of either HALT or ALTERNATE
    HALT_OR_LOOP -> The patrol will spawn with a random behaviour of either HALT or LOOP
    ROAMING -> Only the starting waypoint will be used, then the AI will go off and pick destination locations on its own.

# 11 LootingBehaviour
    Desired AI looting behavior.

    Options can be combined like so:

    "LootingBehaviour": "WEAPONS | BANDAGES | CLOTHING_HIPS | CLOTHING_BACK_SMALL | UPGRADE",
    Available options:

    WEAPONS_FIREARMS
    WEAPONS_LAUNCHERS
    WEAPONS_MELEE
    WEAPONS               //! Same as WEAPONS_FIREARMS | WEAPONS_LAUNCHERS | WEAPONS_MELEE
    BANDAGES
    CLOTHING_ARMBAND
    CLOTHING_BACK_LARGE
    CLOTHING_BACK_MEDIUM
    CLOTHING_BACK_SMALL
    CLOTHING_BACK         //! Same as all CLOTHING_BACK_* options combined
    CLOTHING_BODY
    CLOTHING_EYEWEAR
    CLOTHING_FEET
    CLOTHING_GLOVES
    CLOTHING_HEADGEAR
    CLOTHING_HIPS
    CLOTHING_LEGS
    CLOTHING_MASK
    CLOTHING_MELEE
    CLOTHING_SHOULDER
    CLOTHING_VEST
    CLOTHING              //! Same as all the other CLOTHING_* options combined
                            //! (except CLOTHING_SIMILAR and CLOTHING_IDENTICAL)
    CLOTHING_IDENTICAL    //! Will only loot identical clothing to the one the AI is currently wearing
    CLOTHING_SIMILAR      //! Will only loot similar clothing to the one the AI is currently wearing
                            //! (i.e. same type, different color)
    FOOD                  //! Food procurement including hunting and animal skinning
    UPGRADE               //! If the AI already has a weapon or clothing in slot, 
                        //! should it be allowed to upgrade?
    DEFAULT               //! Same as WEAPONS_FIREARMS | WEAPONS_LAUNCHERS | WEAPONS_MELEE
    ALL                   //! Same as WEAPONS | BANDAGES | CLOTHING | UPGRADE

# 12 Speed
    Maximum speed allowed for the AI when not in combat.

    STATIC
    WALK
    JOG
    SPRINT
    RANDOM -> will give a result between STATIC and SPRINT
    RANDOM_NONSTATIC -> will give a result between WALK and SPRINT

# 13 UnderThreatSpeed
    Maximum speed allowed for the AI when in combat.

    STATIC
    WALK
    JOG
    SPRINT
    RANDOM -> will give a result between STATIC and SPRINT
    RANDOM_NONSTATIC -> will give a result between WALK and SPRINT

# 14 CanBeLooted
    If set to 1, AI can be looted once dead. If set to 0, they cannot be looted.

# 15 LootDropOnDeath
    If set to a JSON filename in <serverprofile>\ExapnsionMod\AI\LootDrops, will spawn this loot when AI dies. You can look at the Example.json that is automatically generated to see how the file contents need to be laid out (format is similar to loadouts).

# 16 UnlimitedReload
    Bitmask. If set to any non-zero value (see below), AI will be able to reload infinitely if they have a spare mag or ammo in their inventory (mags will refill automagically).

    0 -> Off
    1 -> All targets
    2 -> Animals
    4 -> Infected
    8 -> Players
    16 -> Vehicles
    Values other than 1 can be added together to combine them. E.g. a value of 6 means only allow unlimited reload if current AI target is an animal or Infected.

# 17 SniperProneDistanceThreshold
    Minimum distance in meters before an AI holding a bolt action rifle will go prone to engage a target. If the target is closer, AI won't go prone. Setting to 0 disables prone completely.

# 18 AccuracyMin
    Minimum accuracy of this patrol (0.0-1.0)

    If set to -1 will use the AccuracyMin setting used on the top of the config file.

# 19 AccuracyMax
    Maximum accuracy of this patrol (0.0-1.0)

    If set to -1 will use the AccuracyMax setting used on the top of the config file.

# 20 ThreatDistanceLimit
    Distance in meters when the target will start be considered a potential threat

    If set to -1 will use the setting used on the top of the config file.

# 21DamageMultiplier
    Damage multiplier for damage dealt by the AI. Base damage they deal will be multiplied by this value.

    If set to -1 will use the setting used on the top of the config file.

# 22 DamageReceivedMultiplier
    Damage multiplier for damage the AI receive. Base damage they receive will be multiplied by this value.

    If set to -1 will use the setting used on the top of the config file.

# 23 DespawnRadius
    The required distance from a player to despawn. If a player is closer than DespawnRadius meters, then the patrol won't despawn.

    If set to -1 will use the DespawnRadius setting used on the top of the config file.

# 24 MinDistRadius
    The required minimum distance from a player to spawn. If a player is closer than MinDistRadius meters, then the patrol won't spawn

    If set to -1 will use the MinDistRadius setting used on the top of the config file.

# 25 MaxDistRadius
    The required maxium distance from a player to spawn. If a player is further away than MaxDistRadius meters, then the patrol won't spawn

    If set to -1 will use the MinDistRadius setting used on the top of the config file.
# 26 MinSpreadRadius/MaxSpreadRadius
    This setting allows you to make each of your waypoints randomized in a radius defined by min/max spread. If you want your waypoints to be accurate, keep this setting at 0.

# 27 Chance
    Spawn chance for this patrol as a value between 0.0 (0%) and 1.0 (100%).

# 28 DespawnTime
    How long will it take for the patrol to despawn if no players are in MaxDistRadius.

    If set to -1 will use the DespawnTime setting used on the top of the config file.

# 29 RespawnTime
    How long until this patrol can respawn?

    If set to -1 they won't respawn
    If set to -2 will use the RespawnTime setting used on the top of the config file.

# 30 LoadBalancingCategory
    This allows you to assign a category for load balancing, to determine how many patrols of this type can be active depending on player count, with great amount of customizability. See AI Load Balancing

# 31 ObjectClassName
    (will ignore Waypoints if set)

    A classname of a building you want AI to spawn on (e.g. heli or police wrecks, police stations, etc).

    By default, only objects inheriting from BuildingBase/House are supported, but if you use DayZ-Expansion-Missions, then also the individual airdrop container classnames can be used.

    Other objects can be supported by modding (the object type needs to be registered using eAIRegisterDynamicPatrolSpawner and have a eAIDynamicPatrolSpawner instance assigned. How this needs to be initialized depends on the type of object, see BuildingBase.c in DayZ-Expansion-Scripts and ExpansionAirdropContainerBase.c in DayZ-Expansion-Scripts as examples)