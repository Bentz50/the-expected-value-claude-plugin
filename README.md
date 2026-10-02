# The Expected Value for Claude

Look up Daily EV, collectible card and sealed-product prices, observed history,
and Magic sell-through, and manage your own Manafolio with explicit permissions.
Daily EV is free without account linking. Premium pricing and private Manafolio
require an eligible active paid or gifted TEV MCP membership and a linked TEV
account. Coverage depends on the game, printing, product and source.

## Connect with a personal key

If Claude web/Desktop exposes **Request headers**, add a custom connector with
URL `https://mcp.theexpectedvalue.com/mcp` and **No sign-in**. Set header name
`Authorization` and value `Bearer YOUR_KEY`, replacing `YOUR_KEY` with your
personal TEV key and using one space after `Bearer` (no plus sign or quotes).
Save and enable the connector; nine read-only tools should appear. A member
confirmed this setup and a sealed-price query on September 29, 2026.
Use the header settings, never a chat, to enter your key. Nonstandard headers
require Anthropic approval; use Authorization for Claude. See
[setup and troubleshooting](https://theexpectedvalue.com/mcp#claude).

## Connect the OAuth plugin

Upload the ZIP in Claude's **Customize →
Plugins → Add → Upload plugin**, open this plugin's **Connectors** tab, and
connect The Expected Value. Organization accounts may need an owner to add
the connector first. Use automatic OAuth setup; no client ID or client secret
is required. Public discovery and Daily EV work before sign-in. A protected
pricing or Manafolio call prompts sign-in on TEV to review the needed
permissions. Direct changes require the separate unchecked write-consent box.
Your personal MCP key is not needed. Never paste a key or token into a chat.

You can also add `https://mcp.theexpectedvalue.com/mcp/claude` directly as a
custom connector using OAuth, without the plugin's workflow skills.
If upgrading from 0.1.1, update the plugin and disconnect/reconnect the connector
to approve the added permissions. Existing pricing-only grants do not gain them.

## Use it

Ask for the price of a specific printing or sealed product, its observed price
history, or supported Magic sell-through evidence. Specify the game, set,
finish and marketplace when those matter. Results identify their source,
currency and observation date. Prices are observations, not inventory or a
guarantee of a future sale.

Version 0.4.0 includes three skills: `daily-ev` for public box/display EV and
coverage, `tev-pricing` for prices/history/liquidity, and `manafolio` for private
holdings, changes and undo. Ask for Daily EV without signing in; results preserve
pagination, source dates, missing values and the published model's exclusions.

The connector offers the same 16 tools as ChatGPT: Daily EV, nine pricing
tools and six Manafolio tools. Only protected calls request OAuth: `pricing:read`
for pricing, plus `manafolio:read` for private reads and `manafolio:write` for changes.
Private reads cover your holdings, costs, dated valuations and change history.
With write consent, ask it to add/edit holdings, soft-delete lots, record completed
sales/openings, or undo a specific MCP change. Writes use version checks and
idempotency keys; rollback refuses later conflicts. Review changes at
[MCP change history](https://theexpectedvalue.com/sealed-portfolio/public/mcp-changes.php).
Personal-key connections remain pricing-only. Neither connection executes actual
purchases, sales, payments or messages. Results go to Claude under its privacy
practices. Disconnect the OAuth connector from
[Manage MCP server access](https://theexpectedvalue.com/sealed-portfolio/public/mcp-access.php)
to revoke its access. OAuth connections expire after 30 days and require
reconnecting. For a personal-key connection, revoke or replace your key on that
page instead. Disconnecting or revoking does not remove results already delivered
to Claude.

## Support and terms

[MCP support](https://theexpectedvalue.com/mcp#support) ·
[Privacy](https://theexpectedvalue.com/legal/privacy-policy) ·
[Terms](https://theexpectedvalue.com/legal/terms-of-service).
The package is proprietary. Its included [LICENSE](LICENSE) permits use and
redistribution of this unmodified plugin, including through Anthropic's directory.
It grants no backend, dataset or third-party content rights. Service access remains
subject to TEV's terms and the access requirements above. Directory acceptance
is separate from installing the plugin. Version 0.3.0 was published in the
directory; newer updates require their own review.
