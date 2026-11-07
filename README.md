# KiteBlocks Custom Enchants v2 (Paper 26.2)

An original Minecraft plugin based on the enchantment names, equipment and maximum levels in the supplied screenshots. **Not an OPBlocks plugin or an exact recreation of its internal behavior.**

## Features
- 60+ enchant names with maximum levels, categories and equipment restrictions listed in `/enchants` (multiple pages).
- `/kbenchant apply <id> <level>` (admin) keeps all existing v1 enchanted item tags/commands compatible.
- `/kbenchant book <id> [level]` (admin) issues an enchantment book; drag book onto the correct item to attempt enchanting.
- `/kbenchant scroll white` or `black` (admin) issues scrolls.
- `/enchanter` or `/enchshop`: purchasable Basic (5,000), Advanced (20,000), Extreme (50,000) random enchant books using **MultiCurrency `xp`**, NOT vanilla XP or Vault money.
- Purchasable White / Black Scrolls (25,000 XP each by default). Drag scroll onto an enchantment book before application. White improves success by randomly 1–10 percentage points; Black reduces break-on-failure chance by randomly 1–10 percentage points. Both percentages are capped to valid 0–100 ranges.
- Separate randomized success (60–100%) and item-break chance (0–20%) on generated books, editable with scrolls.
- A set of implemented enchantment effects, listed below. Other registered enchantments display in menu and can be applied, **but are not yet active in gameplay**: see limitation.
- Shop pricing and proc percentages editable in config.yml.

## Implemented in-game effects
Decapitation, WellFed, Trickster, Summoner, Scorch, Nightblade, Hangry, Experent, Catapult, Venom, Telekinesis, Multikill, Leaden, Illuminating Touch, Freeze, Dragon Slayer, Combo Counter, Blackout, Alacrity, Lightning Rod, Death Wish, Shark Gills, Heat Reflector, Cat Eyes, Blood Rage, Color Spray, Redirect, Guardian Angel, Super Jump, Hermes Wings, Agile, Dasher, Auto Smelt, Gatherer, Multishot (planned), Poison Shot, Fireball, Dragon Hunter, Bait Finder. **Some effects are simplified** compared to the screenshot descriptions.

## Limitations and safety
- Some listed enchants are presently metadata-only (e.g. Armour Saver, Preservation, Railgun, Soul Eater, and others). They **do not yet deliver their described effects**, and no rewards should be sold as fully working without testing them. This v2 is an intermediate expansion.
- Book and scroll GUI actions use Bukkit inventory clicks and should be tested in a staging server. Book application may destroy an item on failure according to its visible chance.
- MultiCurrency payment is asynchronous and the plugin returns to Bukkit main thread for inventory updates.
- Built against Paper API 26.2.build.134-stable and Java 25. GitHub workflow performs the build.
- The project contains the `MultiCurrency-API-1.1.0.jar` library supplied by the user for compilation only. **Only install the generated KiteBlocksCustomEnchants plugin JAR**, not the API jar.
- Back up world/data and test before enabling for players.

## Install
1. Back up your world and current `plugins/KiteBlocksCustomEnchants` folder.
2. Upload all extracted source files to your existing GitHub repo, **overwriting** old `src/.../CustomEnchantsPlugin.java`, `plugin.yml`, `config.yml`, and updating `build.gradle` and workflow; do not upload the ZIP itself.
3. In GitHub → Actions → Build Paper Plugin → Run workflow. Download Artifacts ZIP and **extract** its JAR.
4. Stop Minehut server, remove old KiteBlocksCustomEnchants JAR, upload the new JAR, restart.
5. Ensure MultiCurrency is enabled with currency ID `xp`; run `/enchants`, `/enchanter`, and test a cheap book on a spare item using a test XP balance.

## Level display
Equipment items store levels under the original `kiteblockscustomenchants:enchant_<id>` persistent-data key, so swords enchanted with the original five enchants should retain their enchantments.
