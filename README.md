# House of Iliaster — Quest Board

A static GitHub Pages site for the House of Iliaster quest board.

## Files

| File | Purpose |
|---|---|
| `index.html` | Player-facing board — shows available, visible contracts only |
| `dm.html` | Aurelian view — password protected, full controls |
| `quests.json` | The data file — edit this to add or update contracts |

## Deployment

1. Create a new GitHub repository (e.g. `iliaster-board`)
2. Upload `index.html`, `dm.html`, and `quests.json` to the root
3. Go to **Settings → Pages → Source** and set to **Deploy from a branch → main → / (root)**
4. Your board will be live at `https://[your-username].github.io/[repo-name]/`
5. Share `index.html` URL with players; keep `dm.html` URL to yourself

## Updating the board

**To change what's visible to players:** Open `dm.html` in your browser, enter the passphrase, and use the status/hide controls on each card. Changes save to your browser's localStorage immediately. They do not automatically update the live site for other users.

**To make changes permanent and visible to all players:** Edit `quests.json` directly and push to GitHub. The live site updates within a minute.

**To add a new contract:** Add a new object to `quests.json` following the existing structure, push to GitHub.

## DM passphrase

Default: `iliaster`

To change it: open `dm.html` in a text editor and find the line:
```js
const PASSPHRASE = 'iliaster';
```
Replace `iliaster` with your chosen passphrase.

## Quest status values

| Status | Player sees it? |
|---|---|
| `available` | Yes (unless also hidden) |
| `taken` | No |
| `expired` | No |
| `completed` | No |

Setting a quest to `hidden: true` additionally removes it from the player board regardless of status — useful for contracts you want to suppress temporarily without changing their status.

## LegendKeeper links

In DM mode, each card has a URL field for the corresponding LegendKeeper page. Once set, a "View in Guild Records" link appears on the player-facing card. Paste the full LegendKeeper page URL and save.

## quests.json field reference

```json
{
  "id": "C1-001",
  "tier": "rat",
  "title": "In Aid of ...",
  "summary": "Player-facing description.",
  "completion": "What completing looks like.",
  "reward": "What the party earns.",
  "contact": "Name, role",
  "length": "Duration estimate",
  "timeSensitive": true,
  "expires": "What causes the contract to lapse",
  "lkUrl": "https://app.legendkeeper.com/...",
  "status": "available",
  "hidden": false
}
```

Valid tiers: `rat`, `ram`, `lion`, `dragon`, `chimera`
Valid statuses: `available`, `taken`, `expired`, `completed`
