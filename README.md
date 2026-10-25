# MarketVoyager downloads

Distribution feed and compiled builds for the personal MarketVoyager Dalamud plugin. Source code is maintained separately.

## Install

Add this URL under Dalamud Settings → Experimental → Custom Plugin Repositories:

```text
https://raw.githubusercontent.com/Nyx-Lotus/MarketVoyager-feed/main/pluginmaster.json
```

Save, then search for **MarketVoyager** in `/xlplugins`. Open it with `/marketvoyager`.

## Prototype status

Version 0.4.1 targets Dalamud API 15. It provides Universalis whole-stack price comparisons, guided Lifestream world travel, nearby marketboard approaches, and live stack purchases. Install Lifestream and vnavmesh separately for travel and approaches.

After travel finishes, click **Approach nearest marketboard**. The plugin walks toward the nearest loaded board and stops within interaction range. Use **Stop marketboard approach** to cancel. If no board is loaded, enter a market area and try again; this action stays in the current territory.

After approaching, click **Open board and search selected item**, select a live stack, then **Confirm and buy this stack**. The final button spends gil immediately. Live totals include listing tax. Price, quantity, HQ, remaining budget, inventory space, and gil are checked before sending. Use **Refresh live listings** for subsequent stacks.

The plugin waits for inventory/gil verification. Unresolved outcomes block more purchases until manually checked and acknowledged. Spending reservations persist only for the current plugin session. Clearing a purchase lock retains the reserved spending and conservatively counts the stack as acquired.

For automatic current-world purchasing, click **Search and buy cheapest fitting stacks (spends gil)**. It selects the exact item, plans the lowest tax-inclusive whole-stack total within your limits, selects each listing, confirms only its matching game dialog, and verifies inventory/gil before continuing. **Stop automatic purchasing** prevents further actions; handle any open confirmation manually. Full automatic travel between shopping stops is not implemented. The updated item selection and automatic purchase sequence require in-game testing.

Quotes may be stale or incomplete and exclude buyer tax and travel costs. Confirm live prices before purchasing.



Use **Reset / cancel current operation** to stop and recover immediately. It cancels a matching unsent confirmation and releases the reservation after checking that gil/inventory are unchanged and no purchase request was observed. If a request was already sent, it remains under verification to prevent duplicate buying. Confirmation checks use the selected live item and the displayed quantity/final total, with a budget recheck for displayed tax.

