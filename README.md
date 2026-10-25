# MarketVoyager downloads

Distribution feed and compiled builds for the personal MarketVoyager Dalamud plugin. Source code is maintained separately.

## Install

Add this URL under Dalamud Settings → Experimental → Custom Plugin Repositories:

```text
https://raw.githubusercontent.com/Nyx-Lotus/MarketVoyager-feed/main/pluginmaster.json
```

Save, then search for **MarketVoyager** in `/xlplugins`. Open it with `/marketvoyager`.

## Prototype status

Version 0.2.0 targets Dalamud API 15. It provides Universalis whole-stack price comparisons, guided Lifestream world travel, and nearby marketboard approaches through vnavmesh. Install Lifestream and vnavmesh separately to use those features.

After travel finishes, click **Approach nearest marketboard**. The plugin walks toward the nearest loaded board and stops within interaction range. Use **Stop marketboard approach** to cancel. If no board is loaded, enter a market area and try again; this action stays in the current territory.

Purchases are manual. Automatic marketboard interactions and unattended buying are not implemented. Build and planner checks pass; in-game testing of approaches is still required.

Quotes may be stale or incomplete and exclude buyer tax and travel costs. Confirm live prices before purchasing.
