# ScullyXlife Links

GitHub Pages profile landing page for:

- My Tool
- Stella DayZ Tools
- FREE Trusted Killfeed Bot
- IC Moderation
- Iron Translator
- Coffee?

Live site: <https://scullyxlife.github.io/>

## IC Moderation

Public overview: <https://scullyxlife.github.io/ic-moderation/>

The overview covers shipped features, the current administration and recovery development focus, and planned work. Keep roadmap labels and the reviewed date aligned with bot releases; a planned item must not be presented as available until it ships.

The public install entry point is <https://ironchronicle.studio/login>. Visitors sign in with Discord, then choose **Add bot to a server** in the dashboard. The authenticated `/install` route must not be used as the public CTA because signed-out visitors receive an authorization error. The dashboard link is <https://ironchronicle.studio/>.

Paid checkout remains disabled and is not advertised on this page. The existing bot emblem is copied from the IC Moderation dashboard branding assets.

This is a static site with no build step. GitHub Pages publishes the repository root from `main`. To preview locally, run `python -m http.server 4178 --bind 127.0.0.1` and open <http://127.0.0.1:4178/>. Before publishing, check the home-to-overview link, section anchors, install and dashboard destinations, keyboard navigation, and narrow/mobile layouts.

## Publishing updates

Use Git, GitHub CLI, and Python from the website checkout:

```powershell
python -m http.server 4178 --bind 127.0.0.1
```

After checking the preview, run these in another terminal:

```powershell
git diff --check
git diff
git status --short
git add README.md index.html ic-moderation/
git commit -m "Update IC Moderation overview"
git push origin main
gh api repos/ScullyXlife/scullyxlife.github.io/pages/builds/latest --jq '{status: .status, commit: .commit, error: .error.message}'
```

Wait until the Pages build reports `built` for the pushed commit, then check both the public homepage and overview. A successful Git push alone does not confirm that the website has deployed. Stop the local preview server with Ctrl+C when finished.
