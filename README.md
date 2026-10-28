# [L4D2] Survivor Bot AI Improver - SI-Only Primary Edition

A feature-packed fork of [Emana202's Survivor Bot AI Improver](https://github.com/Emana202/L4D2-Survivor-Bot-AI-Improver) for *Left 4 Dead 2*. 

This fork introduces smart ammo conservation by restricting primary weapons to Special Infected encounters, survivor-specific melee preferences, intelligent shotgun tank-kiting routines, and automated anti-stuck failsafes.

---

## 🌟 What's New in This Fork?

### 1. 🎯 SI-Only Primary Logic (Ammo Conservation)
Survivor bots in L4D2 notoriously burn through primary rifle and shotgun ammo on stray common infected. This fork gives bots strict combat discipline:
* **Sidearms for Commons, Primaries for SI:** Bots draw their secondary weapons (Pistols, Magnums, or Melee) against normal common infected and only draw their primary weapons when Special Infected (SI), Witches, or pinned teammates are detected.
* **Granular Distance Ranges:** Distinct detection radiuses for **Visible** and **Non-Visible** SI, categorized by weapon types (Snipers, Shotguns, Rifles/SMGs).
* **Swarm Overrides:** When surrounded by a horde, bots can dynamically switch back to Melee or Sidearms depending on per-weapon class permissions.
* **Tactical Reload Before Stow:** Once all SI are dead or lost from sight, bots will hold their primary, reload it (if below a customizable capacity threshold), and wait out a cooldown timer before stowing it away.

### 2. 🗡️ Survivor-Specific Melee Allow/Disallow
Assign melee weapons character-by-character. 
* Want Coach and Rochelle to wield katanas/axes while Nick and Bill strictly stick to Pistols and Deagles? Easily toggle who can and cannot pick up melee weapons.
* Bots barred from melee will ignore melee drops and actively seek out pistols or magnums to replace unwanted melee weapons.

### 3. 🏃 Intelligent Shotgun Tank Kiting
Stock bots with shotguns either retreat into corners or push into Tank punches.
* Shotgun-wielding bots will maintain an optimal combat loop against Tanks: actively pursuing within optimal pellet spread range, and retreating if the Tank gets too close.
* Bots also perform tactical retreats when reloading shotgun shells instead of standing in harm's way.

### 4. 🧙 Startled Witch Chase Compatibility
* Optional CVar (`ib_witchbehavior_chase`) to disable or enable custom bot pursuit toward startled Witches—ideal for avoiding conflicts with standalone Witch behavior plugins.

### 5. 🛠️ Anti-Stuck Failsafe
* Built-in position monitor: if a bot gets stuck standing still while firing (without being pinned, incapped, climbing, or healing), the system resets their movement path after a 4-second delay to snap them out of the freeze.

---

## 📦 Requirements & Installation

### Requirements
* [SourceMod](https://www.sourcemod.net/) 1.11+
* [Left 4 DHooks Direct](https://forums.alliedmods.net/showthread.php?t=321696)
* [VScript Plugin](https://github.com/FortyTwoFortyTwo/VScript) *(Optional, for optimized location pathing)*
* [Actions Extension](https://forums.alliedmods.net/showthread.php?t=336374) *(Optional)*

### Installation
1. Follow the base setup outlined in the [original plugin repository](https://github.com/Emana202/L4D2-Survivor-Bot-AI-Improver).
2. Place the compiled `.smx` file into your `left4dead2/addons/sourcemod/plugins/` directory.
3. Configure the CVars below in `left4dead2/cfg/sourcemod/l4d2_improved_bots.cfg` (generated automatically after first launch).

---

## ⚙️ New CVars & Configuration

### 🗡️ Survivor-Specific Melee Permissions
Controls which survivor bots are allowed to pick up and use melee weapons `(0 = Disabled / Pistols & Magnums Only, 1 = Enabled)`.

| CVar | Default | Description |
| :--- | :---: | :--- |
| `ib_melee_nick` | `"0"` | Allow Nick to use melee weapons. |
| `ib_melee_rochelle` | `"1"` | Allow Rochelle to use melee weapons. |
| `ib_melee_coach` | `"1"` | Allow Coach to use melee weapons. |
| `ib_melee_ellis` | `"1"` | Allow Ellis to use melee weapons. |
| `ib_melee_bill` | `"0"` | Allow Bill to use melee weapons. |
| `ib_melee_zoey` | `"1"` | Allow Zoey to use melee weapons. |
| `ib_melee_francis` | `"1"` | Allow Francis to use melee weapons. |
| `ib_melee_louis` | `"1"` | Allow Louis to use melee weapons. |

---

### 🎯 SI-Only Primary Logic
Toggles and tuning parameters for the weapon-switching mechanic.

| CVar | Default | Description |
| :--- | :---: | :--- |
| `ib_primary_only_on_si_enabled` | `"1"` | Master toggle for the SI-only primary logic `(0/1)`. |
| `ib_primary_only_on_si_cooldown` | `"3.0"` | Seconds to keep primary equipped after all threats disappear before stowing. |
| `ib_primary_only_on_si_reload_enabled` | `"1"` | Forces bots to reload their primary before switching back to sidearms `(0/1)`. |
| `ib_primary_only_on_si_reload_threshold`| `"0.7"` | Magazine capacity percentage (0.0 - 1.0) below which a reload is triggered. |

#### Threat Detection Ranges (In Game Units)
Controls how close an SI must be to draw primary weapons.

| Weapon Class | Visible SI Range | Non-Visible / Concealed SI Range |
| :--- | :---: | :---: |
| **Snipers** | `ib_primary_only_on_si_range_vis_sniper "4000"` | `ib_primary_only_on_si_range_novis_sniper "800"` |
| **Shotguns** | `ib_primary_only_on_si_range_vis_shotgun "1200"` | `ib_primary_only_on_si_range_novis_shotgun "400"` |
| **Rifles & SMGs** | `ib_primary_only_on_si_range_vis_rifle "2000"` | `ib_primary_only_on_si_range_novis_rifle "800"` |
| **Fallback / Default** | `ib_primary_only_on_si_range_vis "2000"` | `ib_primary_only_on_si_range_novis "1000"` |

#### Swarm Overrides
Allow bots to switch back to secondary weapons when swarmed by common infected, even during an SI fight `(0 = Keep Primary, 1 = Allow Switch)`.

* **Melee Overrides (When holding Melee):**
  * `ib_primary_only_on_si_melee_override_rifle "1"`
  * `ib_primary_only_on_si_melee_override_shotgun "0"`
  * `ib_primary_only_on_si_melee_override_sniper "0"`
* **Pistol / Magnum Overrides (When holding Sidearms):**
  * `ib_primary_only_on_si_pistol_override_rifle "1"`
  * `ib_primary_only_on_si_pistol_override_shotgun "0"`
  * `ib_primary_only_on_si_pistol_override_sniper "0"`

---

### 🏃 Shotgun Tank Kiting

| CVar | Default | Description |
| :--- | :---: | :--- |
| `ib_tank_kiting_shotgun_enabled` | `"1"` | Enable shotgun-specific kiting behavior around Tanks `(0/1)`. |
| `ib_tank_kiting_shotgun_retreat` | `"200"` | Distance (units) where the bot retreats backwards away from the Tank. |
| `ib_tank_kiting_shotgun_pursue` | `"250"` | Distance (units) beyond which the bot moves closer to stay in lethal spread range. |

---

### 🧙 Witch Compatibility

| CVar | Default | Description |
| :--- | :---: | :--- |
| `ib_witchbehavior_chase` | `"0"` | Custom bot movement when a Witch is startled `(0 = Vanilla/Mod Handling, 1 = Bot Improver Pursuit)`. |

---

## 📜 Credits & Acknowledgments
* **Emana202 & Kerouha** - Creators of the original [Survivor Bot AI Improver](https://forums.alliedmods.net/showthread.php?t=342872).
* **EagleRaviOrange** - Fork author, SI-only primary logic, per-survivor melee settings, tank kiting, and movement fixes.
