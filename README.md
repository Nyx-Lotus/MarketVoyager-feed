# MarketVoyager downloads

Distribution feed and compiled builds for the personal MarketVoyager Dalamud plugin. Source code is maintained separately.

## Install

Add this URL under Dalamud Settings → Experimental → Custom Plugin Repositories:

```text
https://raw.githubusercontent.com/Nyx-Lotus/MarketVoyager-feed/main/pluginmaster.json
```

Save, then search for **MarketVoyager** in `/xlplugins`. Open it with `/mv` or `/marketvoyager`.

## Return to outdoor housing wards (0.17.0)

Starting location now captures world, district, **ward and subdivision**, plus coordinates when buying starts. Outdoor Mist and the other four housing districts no longer fail for lacking an in-zone main aetheryte. Requires the district gateway city attuned. After shopping, Lifestream returns to an outdoor address anchor in the saved ward/division, then vnavmesh walks to the saved coordinates. World, district, ward and division are checked before and throughout the final walk. The saved return point appears in status.

No shared-house shortcut configuration or ownership is required for this outdoor coordinate return. House/apartment interiors remain unsupported; ward access and a valid walking route are required, and travel fees are additional. Build and 119 checks pass; the residential round trip needs in-game testing.

## Retainer credit compatibility (0.16.2)

The retainer reader now ignores empty/unrelated cached entries before validating owners and supports the installed library's legacy 32-bit owner metadata only when it matches the IPC-scoped full retainer ID. Other owners and malformed populated entries still fail. Inventory errors appear once with more specific diagnostics; successful refresh clears old errors. Build and 108 checks pass; please refresh inventory and retry the quote in-game.

## Quote action handling (0.16.1)

Quote/buy controls now use a dedicated action bar and dispatch on the game update thread, with immediate queued feedback, explicit blockers/errors and click logging. Inventory-refresh failures no longer leave a silent return. `/mv quote` is an alternate command to request the same quote. Purchases still require a current matching quote and a separate Start buying action. Build and 103 existing checks pass; the reported click regression needs in-game validation.

## Compact wider layout (0.16.0)

Wider, shorter default window (1180x740, scaled and capped to the display), side-by-side quote/buy actions, tighter spacing, and batch setup in a separate left pane. Drag the divider to change pane widths. The item table has independent scrolling, fixed headers, resizable columns, wrapped item/status text and properly sized Remove controls. Small windows can scroll horizontally. The layout resets once when the plugin loads, then remains resizable. Release build passes; in-game visual validation remains.

## Exclude pre-crafts by default (0.15.1)

Teamcraft imports skip **Pre crafts** sections by default and keep raw materials/crystals, avoiding purchases of both intermediates and their ingredients. Import feedback reports skipped rows. The optional **Include pre-crafts in Teamcraft import** checkbox restores them on the next import. **Reimport existing lists** to apply the filter. Manual additions and headerless text are unchanged. Recognizes the standard English heading and common spelling/tier variants; custom/non-English headings are not currently detected. Build and 103 checks pass; UI validation remains in-game.

## Manual batches and average prices (0.15.0)

The **Batch** tab now supports searching/adding items without Teamcraft, editing each row's Needed quantity, Remove, and Clear batch. Adding a duplicate increases its quantity. Teamcraft import is optional and collapsed; imported lists can also be edited. Any change requires a fresh quote before buying. All existing quantity/budget and inventory-credit safeguards apply.

Each quoted total now includes a weighted **average gil per item** underneath, including tax. The denominator is the actual planned/purchased quantity including allowed extras, excluding units already owned. Hover for details. Completed purchases are included when an item replans. Build and 94 checks pass; editor layout and in-game flow still need testing.

## Bulk import fix (0.14.1)

Fixes the `1193x Fire Crystal` import failure by raising the supported quantity to **9,999 per material** throughout importing, queue validation, price planning and purchase setup. Keeps whole-stack, budget and extra-quantity safeguards. Import errors now show their specific reason in the top status panel and are recorded in the plugin log. Build and 84 checks pass, including the reported input; live bulk purchasing needs in-game testing.

## Count owned items (0.14.0)

Materials now offers **Count carried inventory toward imported quantities** and **Count retainer stock (Allagan Tools)**. Both default off to avoid subtracting twice from Teamcraft exports that already exclude owned items. Enable them for total requirements. The table shows Imported, Carried, Retainer and To buy quantities; quotes and purchases cover only the remainder. Refresh is automatic before quoting and buying, with a new quote required if the remaining quantities changed. Fully covered imports cost zero and trigger no travel/purchases.

Carried counts use bags/crystals directly. Retainer counts use [Allagan Tools IPC](https://github.com/Critical-Impact/InventoryTools/blob/main/InventoryTools/IPC/IPCService.cs) for this character's cached retainer bags/crystals; enable Allagan Tools and visit each retainer to update its record. Sale listings, equipped gear, collectibles, other characters, shared storage and saddlebag contents do not count. HQ contributes only when Include HQ is on. **Retainer items are counted but must still be withdrawn manually**; the UI shows the outstanding collection quantity. Cached counts may be stale. Build and 73 checks pass; the new native inventory reader and IPC require in-game validation.

## Quote before buying (0.13.0)

Use **Get quote / Get queue quote**, review the prominent total and Materials row costs, then separately press **Start buying**. Quoting does not travel or spend gil. Changing inputs/settings or waiting ten minutes requires a new quote. Buying captures the starting return location then and refreshes current prices; the quote is an estimate, and the shared budget is the hard purchase limit. Travel fees are additional.

Status now explicitly distinguishes not started, working, quote ready, stopped and needs attention. It shows an animated activity indicator, elapsed time, current item/server wait, queue prices/plans progress, a warning after 15 seconds waiting for a server response, and named-item timeout errors after the 30-second request limit. Errors remain visible rather than reverting to Ready. Build and 61 existing checks pass; in-game UI and workflow testing remain.

## Teamcraft materials (0.12.0)

Copy the **materials panel as text** in Teamcraft, paste it into MarketVoyager's **Materials** tab, click **Import / replace queue**, review the rows, then **Start imported queue**. Uses Teamcraft's text format (`6x Zinc Ore` with optional section headings), verified against [the official panel exporter](https://github.com/ffxiv-teamcraft/ffxiv-teamcraft/blob/staging/apps/client/src/app/modules/list/list-details-panel/list-details-panel.component.ts). Export just the materials you intend to purchase: whole-list exports may contain both intermediates and ingredients. Names must match your game language. URLs/JSON/encoded strings are not supported.

The queue estimates all materials before spending, uses one shared budget set in Shop, finishes and verifies each material before the next, and returns to the original saved destination after the final item. Live fallback and price/quantity safeguards apply to each material. Invalid imports show errors and preserve the prior queue; duplicates merge in first-seen order. Supports 100 distinct materials with 1-999 each. Imported remaining amounts are not reduced by inventory again.

Stop/failure halts the queue; no skipping or blind retry. Progress is session-only. Starting again starts a new queue and can repurchase completed materials, so reimport only remaining quantities after interruption. Build and 61 automated checks pass; the multi-material in-game sequence needs testing.

## Cost and status dashboard

Version 0.11.0 adds a prominent estimated basket total, verified item/spending progress, current activity, and next purchase quantity, item, world and expected cost. Preview prices includes a combined multi-world basket with estimated market tax; travel fees are additional. Manual controls and diagnostics are collapsed by default. Build and 42 checks pass; in-game visual testing remains.

## Prototype status

Version 0.17.0 targets Dalamud API 15. Install Lifestream and vnavmesh separately for travel and approaches.

Orders can now split purchases across worlds to minimize the combined eligible stack cost. Verified quantity and spending carry across stops. **Replacement price increase (%)** under Purchase safeguards defaults to 10%; live replacements must fit this increase over the stop's quoted unit/subtotal prices, plus all existing safety limits. If none fit, the remaining quantity is replanned against fresh region quotes, excluding visited worlds. Return travel starts only after the entire order is verified. Ambiguous purchase outcomes stop instead of hopping/retrying. World plans estimate buyer tax; final live tax and the order budget are checked before confirming. Teleport fees remain additional. The new multi-world/fallback sequence needs in-game testing.

**Starting location (world, zone, coordinates)** is now the default return option. It saves your position when Find cheapest is pressed, returns to that world/zone through Lifestream, then walks to within 1.5 yalms using vnavmesh. Requires an attuned main aetheryte in the starting zone and an available walking route. Numbered instances and arbitrary housing/interior routes are not supported by coordinate return; unsupported starts stop before shopping. Housing shortcut options remain available. The new route needs in-game testing.

**After shopping** offers Stay at marketboard, Starting world (world only), Private house, Free company estate, Shared estate, and Apartment. Returns run only after purchases are verified. Starting world does not restore your exact starting position. Housing options use your home-world Lifestream shortcuts; configure those destinations in Lifestream. Return fees are additional. A return failure reports that purchases already succeeded. Return routes need an in-game retest.

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



