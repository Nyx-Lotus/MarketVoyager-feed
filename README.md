# MarketVoyager downloads

Distribution feed and compiled builds for the personal MarketVoyager Dalamud plugin. Source code is maintained separately.

## Install

Add this URL under Dalamud Settings → Experimental → Custom Plugin Repositories:

```text
https://raw.githubusercontent.com/Nyx-Lotus/MarketVoyager-feed/main/pluginmaster.json
```

Save, then search for **MarketVoyager** in `/xlplugins`. Open it with `/marketvoyager`.

## Prototype status

Version 0.7.2 targets Dalamud API 15. Install Lifestream and vnavmesh separately for travel and approaches.

The character's current region is detected automatically from game data. **Allow travel to other worlds** is on by default and searches that region. Turn it off to keep lookup and purchases on your current world. There is no region, data-center, or world dropdown. The run captures the choice when started.

The redesigned UI uses hot-pink accents on plum-charcoal surfaces with rounded controls. Shop, World quotes, and Live market tabs separate order settings, price comparisons, and manual controls. Run progress and Stop remain visible above the scrolling content. **Preview world prices** is the renamed Find prices action. Purchase and navigation behavior remain the same.

### New price and quantity limits

- Extra items default to zero. Enabling extras also requires setting **Maximum extra items per request**. Needing 6 with a limit of 2 can buy at most 8, never 99.
- Default unit-price ceiling is **150% of the median recent completed sale price**, separately for NQ/HQ. Requires at least 5 sales within 7 days for that quality. References expire after 10 minutes. Missing, sparse, or stale data blocks automation.
- The planner minimizes the total whole-stack cost among eligible combinations, including live tax, while respecting your unit cap and request budget. A lower unit price does not justify an oversized stack.
- Full automatic runs fetch the reference themselves. For standalone/manual shopping, click **Find prices** first. These controls need in-game retesting; they reduce outlier exposure and do not guarantee market prices are fair.

Choose your item, quantity, scope, and purchase limits, then click **Find cheapest, travel and buy (spends gil)**. The plugin finds a fitting reachable world quote, travels there, approaches a board, searches, selects the cheapest fitting live stacks, confirms matching purchase dialogs, and verifies inventory/gil before completing. If no board is loaded, it uses Limsa Lominsa Lower Decks as a fallback market area. This requires attunement and teleport gil. Teleport costs are additional to the purchase budget.

Use **Stop entire run** to cancel further steps. Already sent purchases remain under verification. Runs handle one item on one chosen world; they stop if live stock/prices no longer fit instead of exceeding limits or automatically trying another world. The new complete sequence requires in-game testing.

After travel finishes, click **Approach nearest marketboard**. The plugin walks toward the nearest loaded board and stops within interaction range. Use **Stop marketboard approach** to cancel. If no board is loaded, enter a market area and try again; this action stays in the current territory.

After approaching, click **Open board and search selected item**, select a live stack, then **Confirm and buy this stack**. The final button spends gil immediately. Live totals include listing tax. Price, quantity, HQ, remaining budget, inventory space, and gil are checked before sending. Use **Refresh live listings** for subsequent stacks.

The plugin waits for inventory/gil verification. Unresolved outcomes block more purchases until manually checked and acknowledged. Spending reservations persist only for the current plugin session. Clearing a purchase lock retains the reserved spending and conservatively counts the stack as acquired.

For automatic current-world purchasing, click **Search and buy cheapest fitting stacks (spends gil)**. It selects the exact item, plans the lowest tax-inclusive whole-stack total within your limits, selects each listing, confirms only its matching game dialog, and verifies inventory/gil before continuing. **Stop automatic purchasing** prevents further actions; handle any open confirmation manually. Full automatic travel between shopping stops is not implemented. The updated item selection and automatic purchase sequence require in-game testing.

Quotes may be stale or incomplete and exclude buyer tax and travel costs. Confirm live prices before purchasing.



Use **Reset / cancel current operation** to stop and recover immediately. It cancels a matching unsent confirmation and releases the reservation after checking that gil/inventory are unchanged and no purchase request was observed. If a request was already sent, it remains under verification to prevent duplicate buying. Confirmation checks use the selected live item and the displayed quantity/final total, with a budget recheck for displayed tax.


Budgets apply to each new shopping request. Prior session spending is displayed separately and does not reduce a new request's budget. A refresh or automatic continuation retains the same request budget and prior spending. Rejected plans now display the effective limits and available exact-quantity stack price.


