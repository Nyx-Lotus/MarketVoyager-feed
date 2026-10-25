# MarketVoyager downloads

Distribution feed and compiled builds for the personal MarketVoyager Dalamud plugin. Source code is maintained separately.

## Install

Add this URL under Dalamud Settings → Experimental → Custom Plugin Repositories:

```text
https://raw.githubusercontent.com/Nyx-Lotus/MarketVoyager-feed/main/pluginmaster.json
```

Save, then search for **MarketVoyager** in `/xlplugins`. Open it with `/marketvoyager`.

## Prototype status

Version 0.3.0 targets Dalamud API 15. It provides Universalis whole-stack price comparisons, guided Lifestream world travel, nearby marketboard approaches, and confirmed live stack purchases. Install Lifestream and vnavmesh separately for travel and approaches.

After travel finishes, click **Approach nearest marketboard**. The plugin walks toward the nearest loaded board and stops within interaction range. Use **Stop marketboard approach** to cancel. If no board is loaded, enter a market area and try again; this action stays in the current territory.

After approaching, click **Open board and search selected item**, select a live stack, then **Confirm and buy this stack**. The final button spends gil immediately. Live totals include listing tax. Price, quantity, HQ, remaining budget, inventory space, and gil are checked before sending. Use **Refresh live listings** for subsequent stacks.

The plugin waits for inventory/gil verification. Unresolved outcomes block more purchases until manually checked and acknowledged. Spending reservations persist only for the current plugin session. Clearing a purchase lock retains the reserved spending and conservatively counts the stack as acquired.

Unattended buying is not implemented. New board opening, live search, and purchase behavior require in-game testing.

Quotes may be stale or incomplete and exclude buyer tax and travel costs. Confirm live prices before purchasing.

