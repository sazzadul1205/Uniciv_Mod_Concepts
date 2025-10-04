---

# Colony Mod for Unciv

**Colony Mod** introduces a new way to expand your civilization through **colonies** instead of full cities. Colonies are small, resource-focused outposts with limited growth but strategic value.

---

## 📂 Mod Contents

```
ColonyMod/
├─ jsons/
│  ├─ units.json          # Defines Colony Settler and Colony Builder
│  ├─ buildings.json      # Defines Colony Charter (special colony building)
│  ├─ techs.json          # Adds Colonialism tech for advanced expansion
│  └─ modConfig.json      # Customizable mod settings
├─ Images/
│  ├─ UnitIcons/
│  │   └─ Colony Settler.png
│  ├─ ConstructionIcons/
│  │   └─ Colony Charter.png
│  ├─ ImprovementIcons/
│  │   └─ ColonyExtractor.png
│  └─ preview.png         # Icon preview for the mod selection menu
└─ README.md              # This file
```

---

## 🏗 Features

- **Colony Settler**

  - Appears once you research **Guilds**.
  - Founds a **Colony** instead of a normal city.
  - One colony per city initially.

- **Colony Charter (National Wonder)**

  - Automatically built in colonies.
  - Colonies cannot grow beyond **population 1**.
  - Colonies cannot build most buildings or units (only Colony Builders).
  - Colonies must be connected by **road** to your capital to provide resources.
  - Colonies are **razed if captured**.

- **Colony Builder**

  - Special builder unique to colonies.
  - Can only build **once**, on a **luxury resource** within 1 tile of the colony.
  - Extracts the luxury but does not provide normal food/production yields.

- **Colonialism Tech**

  - Becomes available in the **Industrial Era** (after **Steam Power**).
  - Increases colonies allowed per city from **1 → 3**.

---

## ⚙️ Mod Config (jsons/modConfig.json)

You can tweak these values to change how colonies behave:

```json
{
  "claimRadius": 1, // Max distance from colony a builder can claim
  "requireConnection": true, // Colony must be connected to capital by road
  "harvestResourceOnly": true, // Only get luxury benefit, no food/prod/gold
  "allowStealingOtherCivsTiles": false, // Prevents building on enemy tiles
  "autoBuildRoadIfNeeded": false, // If true, tries to auto-build road
  "consumeBuilderOnBuild": true, // Builder disappears after one use
  "validResourceType": "Luxury" // Only luxuries allowed
}
```

---

## 📥 Installation

1. Download or clone this repository.
2. Place the `ColonyMod` folder into your Unciv **mods** directory:

   - **Windows:** next to your `Unciv.exe`, inside `mods/`.
   - **macOS/Linux:** next to the Unciv `.jar`, inside `mods/`.
   - If `mods/` doesn’t exist, create it.

3. Launch Unciv.
4. Go to **Mods** in the main menu → enable _Colony Mod_.
5. Start a **new game** with the mod enabled.

---

## 🖼 Image Rules

- Image filenames must exactly match the **`name`** field in JSON files.
- Units → `Images/UnitIcons/UnitName.png`
- Buildings → `Images/ConstructionIcons/BuildingName.png`
- Improvements → `Images/ImprovementIcons/ImprovementName.png`

Example:
If `units.json` has `"name": "Colony Settler"`, the file **must** be `Images/UnitIcons/Colony Settler.png`.

---

## ⚠️ Limitations

- JSON-only Unciv mods cannot run custom Kotlin code.
- The advanced logic (e.g., `onColonyBuilderBuild` and `canCityFoundColony`) is included here for reference, but requires modifying the Unciv engine source to fully enable.
- For most players, this mod will still add Colony Settlers, Colony Builders, the Colony Charter, and the Colonialism tech.

---

## 🔧 Optional: Engine Integration

If you want colonies to obey all rules (range checks, tile ownership, special extraction logic), you need to:

1. Clone the Unciv source from [GitHub](https://github.com/yairm210/Unciv).
2. Add the provided Kotlin functions into the builder/tile logic.
3. Build and run Unciv locally with Gradle.

A `ColonyModHandler.kt` patch can be supplied if you plan to go this route.

---

## 📌 Future Ideas

- Diplomatic penalties for stealing luxury tiles from other civs.
- Colony upgrades with later techs.
- Automatic road building option for connected colonies.
- Naval Colony Settler for overseas expansion.

---

## 🧪 Debugging

- Use **Mods → Locate mod errors** in-game to see JSON problems.
- Check the console/logs if icons don’t show (usually a filename mismatch).
- If images don’t load, delete `game.atlas` / `game.png` in your mod folder so Unciv repacks them.

---

## 🙌 Credits

- **Mod Author:** Sazzadul Islam
- **Game:** [Unciv](https://github.com/yairm210/Unciv) by Yair Morgenstern and contributors.
- Inspired by Civilization mechanics, adapted for Unciv.

---
