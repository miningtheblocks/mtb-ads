# mtb-ads

Subdomain isolation for the Mining The Blocks ad network.

This repo serves `ads.miningtheblocks.com` via GitHub Pages. The only content
is `ad-frame.html`, which loads the ad-network script and is embedded by the
main site at `miningtheblocks.com/adpick.html` via `<iframe sandbox>`.

By living on a separate origin (`ads.miningtheblocks.com` vs the parent
`miningtheblocks.com`), the iframe can use `sandbox="... allow-same-origin"`
to get cookies/storage on its own origin (which the ad-network needs to
initialize) WITHOUT being able to read the parent's DOM, cookies, or
sessionStorage (where the ad-claim sid+token are stored). The
Same-Origin Policy of the browser enforces this isolation.

See the parent repo `Mining-The-Blocks` for the full context (`docs/adpick.html`
and `docs/adpick.js`).
