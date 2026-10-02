# The Expected Value for Claude

Look up Daily EV, collectible card and sealed-product prices, observed history,
and Magic sell-through, and manage your own Manafolio with explicit permissions.
Daily EV is free without account linking. Premium pricing and private Manafolio
require an eligible active paid or gifted TEV MCP membership and a linked TEV
account. Coverage depends on the game, printing, product and source.

## Connect Claude: recommended setup

1. Install **The Expected Value** from Claude's plugin directory. For manual
   installation, download the ZIP from this repository's Releases and upload it
   under **Customize → Plugins → Add → Upload plugin**.
2. Open this plugin's **Connectors** tab and choose **Connect**.
3. Use Daily EV without signing in. When you request premium pricing or private
   Manafolio data, follow Claude's sign-in prompt, sign in to TEV and review the
   requested permissions. Changes require separate write consent.

Use automatic OAuth setup. No personal key, request header, client ID or client
secret is needed. Organization accounts may need an owner to add the connector
first. Never paste a key or token into a chat.

You can also add `https://mcp.theexpectedvalue.com/mcp/claude` directly as a
custom connector using OAuth, without the plugin's workflow skills.
If upgrading from 0.1.1, update the plugin and disconnect/reconnect the connector
to approve the added permissions. Existing pricing-only grants do not gain them.

## Personal-key fallback

Use this pricing-only method only when you need a custom connector with
**Request headers**. Add URL `https://mcp.theexpectedvalue.com/mcp` and select
**No sign-in**. Set the header name to `Authorization`. When a new key is shown
on [Manage MCP server access](https://theexpectedvalue.com/sealed-portfolio/public/mcp-access.php),
use **Copy complete Authorization value** and paste it into the value field,
even if masked. For a key you already saved, enter `Bearer YOUR_KEY` with one
space after `Bearer` (no plus sign or quotes).

Save and enable the connector; nine read-only pricing tools should appear.
This fallback does not access private Manafolio. If your existing key connection
works, you can keep it while Claude is busy and switch to OAuth when convenient.
Do not generate a replacement solely to use the copy button: replacement
immediately invalidates your previous key. The key is shown only when issued.
Use header settings, never a chat, to enter it. Request-header availability
varies by Claude account; nonstandard headers require Anthropic approval.
See [setup and troubleshooting](https://theexpectedvalue.com/mcp#claude).

## Use it

Ask for the price of a specific printing or sealed product, its observed price
history, or supported Magic sell-through evidence. Specify the game, set,
finish and marketplace when those matter. Results identify their source,
currency and observation date. Prices are observations, not inventory or a
guarantee of a future sale.

Version 0.4.0 introduced three skills: `daily-ev` for public box/display EV and
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
is separate from manual installation. Version 0.4.0 is published in the directory;
version 0.4.1 simplifies setup instructions and keeps the same skills and tools.
Version 0.4.2 includes the privacy policy URL in the plugin manifest.
Directory updates require their own publication review.
