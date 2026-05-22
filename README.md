# TSM v2.8.3
Backport of [TradeSkillMaster](https://www.tradeskillmaster.com/) for 3.3.5a

Most porting done by [Various Authors](https://github.com/andrew6180/TradeSkillMaster/network/members)

Large amount of fixes done by [BlueAo - Warmane](https://forum.warmane.com/showthread.php?t=412904) and [Gnomezilla](https://github.com/Bananaman)

Cross-faction edits by [BigTerrick](https://github.com/BigTerrick)

## 🛠 Cross-Faction Support (i.e. ChromieCraft Patch)

This fork includes a specialized patch designed for cross-faction environments (such as ChromieCraft). Standard TSM isolates data by faction and realm, which limits cross-faction functionality.

### Key Enhancements
- **Memory-Level Syncing:** Hard-links Horde and Alliance data at the `OnInitialize` stage, creating a single data repository for your TSM data.
- **Unified Inventory:** ItemTracker now recognizes characters across factions in your tooltips.
- **Shared Financials:** Accounting, Auctioning, and Crafting modules now share gold data, purchase/sale history, and crafting material costs between all your alts, regardless of faction.

### Implementation Details
- This patch works by intercepting the AceDB-3.0 initialization and forcing Horde and Alliance keys in the raw database to point to the same memory address.
- **Note on SavedVariables:** You will see duplicate entries in your LUA files for both factions. This is expected. The game engine writes the shared memory out twice upon saving, but the data is unified instantly upon the next login.

### Updated TSM Modules
- TradeSkillMaster
- TradeSkillMaster_Accounting
- TradeSkillMaster_AuctionDB
- TradeSkillMaster_Auctioning
- TradeSkillMaster_Crafting
- TradeSkillMaster_ItemTracker

# If you are expericing lua errors and you were previously using another TSM port
Other popular ports use different versions of TSM completely incompatible with this one.

If you are experiecing lua errors **and** you were previously using another version:

Navigate to `<WoW Folder>\WTF\Account\<Account Name>\SavedVariables` and delete any file relating to TSM.

Example:

![https://i.imgur.com/bEpccPg.png](https://i.imgur.com/bEpccPg.png)
