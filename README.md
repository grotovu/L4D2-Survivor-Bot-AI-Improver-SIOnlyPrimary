This is a fork. The original plugin has been helpful to me for years back in SourceMod days. I added some features, well, mostly vibe-coded. My brain is rusty.

In summary, the primary features added are:
- Survivor specific cvars for melee use, who can pick up melee and who can't. (Mine has Nick and Bill set to  0, so they'll stick to pistols and magnum)
- Primary weapons use only when SI are present. You can enable or disable the feature. Unit distance can be configured for both visible and non-visible SI for the snipers, shotguns, rifles and the rest. Useful for saving ammo, and doubly effective if your bot uses melee or magnum when dealing with commons. Additionally, when not swarmed and no SI is present after a few seconds, the bots will reload their primary before switching to secondary.
- Shotgun bot kiting the tank at close range, can be configured in the cvars. You can enable or disable the feature, and how close and far the tank is before the bot with a shotgun starts retreating and chasing. (Mine is 200 units retreat, 250 units pursue)

Installation is the same. See the original here for the steps:
https://github.com/Emana202/L4D2-Survivor-Bot-AI-Improver


# New CVars in this fork:
```
// Toggle which specific survivor can pick up melee.
ib_melee_nick "0"
ib_melee_rochelle "1"
ib_melee_coach "1"
ib_melee_ellis "1"
ib_melee_bill "0"
ib_melee_zoey "1"
ib_melee_francis "1"
ib_melee_louis "1"

// Enable shotgun kiting around tanks.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_tank_kiting_shotgun_enabled "1"

// Range to pursue the Tank when holding a shotgun.
// -
// Default: "300"
// Minimum: "0.000000"
ib_tank_kiting_shotgun_pursue "250"

// Range to retreat from Tank when holding a shotgun.
// -
// Default: "200"
// Minimum: "0.000000"
ib_tank_kiting_shotgun_retreat "200"

// Enable SI-only primary logic.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_primary_only_on_si_enabled "1"

// Seconds to wait before stowing primary.
// -
// Default: "3.0"
// Minimum: "0.000000"
ib_primary_only_on_si_cooldown "3.0"

// Allow rifles to switch to melee if swarmed?
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_primary_only_on_si_melee_override_rifle "1"

// Allow shotguns to switch to melee if swarmed?
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_primary_only_on_si_melee_override_shotgun "0"

// Allow snipers to switch to melee if swarmed?
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_primary_only_on_si_melee_override_sniper "0"

// Allow rifles to switch to Pistol/Magnum if swarmed?
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_primary_only_on_si_pistol_override_rifle "1"

// Allow shotguns to switch to Pistol/Magnum if swarmed?
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_primary_only_on_si_pistol_override_shotgun "0"

// Allow snipers to switch to Pistol/Magnum if swarmed?
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_primary_only_on_si_pistol_override_sniper "0"

// Default NoVis Range
// -
// Default: "1000"
// Minimum: "0.000000"
ib_primary_only_on_si_range_novis "1000"

// Non-visible distance for rifles/SMGs.
// -
// Default: "500"
// Minimum: "0.000000"
ib_primary_only_on_si_range_novis_rifle "800"

// Non-visible distance for shotguns.
// -
// Default: "400"
// Minimum: "0.000000"
ib_primary_only_on_si_range_novis_shotgun "400"

// Non-visible distance for snipers.
// -
// Default: "800"
// Minimum: "0.000000"
ib_primary_only_on_si_range_novis_sniper "800"

// Default Vis Range
// -
// Default: "2000"
// Minimum: "0.000000"
ib_primary_only_on_si_range_vis "2000"

// Visible distance for rifles/SMGs.
// -
// Default: "2000"
// Minimum: "0.000000"
ib_primary_only_on_si_range_vis_rifle "2000"

// Visible distance for shotguns.
// -
// Default: "1200"
// Minimum: "0.000000"
ib_primary_only_on_si_range_vis_shotgun "1200"

// Visible distance for snipers.
// -
// Default: "4000"
// Minimum: "0.000000"
ib_primary_only_on_si_range_vis_sniper "4000"

// Enable reload before switch.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_primary_only_on_si_reload_enabled "1"

// Ammo percentage to trigger reload.
// -
// Default: "0.7"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_primary_only_on_si_reload_threshold "0.7"

// Enable custom bot movement when a Witch is startled. 0=Disable, 1=Enable. To accommodate for custom behavior in another mod.
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_witchbehavior_chase "0"

```
