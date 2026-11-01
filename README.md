# Redirect

A small static handoff page for links already used by LZVE.ly. It shows the destination before opening it, supports a short countdown, and keeps the user in control with an immediate-open link and a pause/resume button.

## Usage

Deploy to Cloudflare Pages (or another static host), then pass an HTTP or HTTPS destination through one of the supported query parameters:

```text
https://your-domain.com/?to=https://example.com
https://your-domain.com/?url=https://example.com
https://your-domain.com/?redirect=https://example.com
https://your-domain.com/?target=https://example.com
https://your-domain.com/?link=https://example.com
```

The parameters are checked in this order: `to`, `url`, `redirect`, `target`, then `link`.

### Delay

Use `delay` or its short form `d` to set the countdown. The default is 7 seconds and the maximum is 30 seconds. An invalid or negative value falls back to 3 seconds.

```text
https://your-domain.com/?to=https://github.com/lversky&delay=5
```

## Allowed destinations

The page accepts only `http:` and `https:` URLs whose hostname exactly matches a host linked through the redirect from the LZVE site. The current allowlist is:

- `beta.music.apple.com`
- `discord.com`
- `github.com`
- `lzvesky.yrs.wtf`
- `orcid.org`
- `sky-link-in-bio.pages.dev`
- `snapchat.com`
- `www.tiktok.com`
- `x.com`

Host matching is exact; a new hostname is rejected until it is linked from LZVE and added to `allowedHosts` in `index.html`. Keep this list and the LZVE site's outbound links in sync.

## Deploy to Cloudflare Pages

1. Push this repo to GitHub.
2. Connect `lversky/redirect` to a Cloudflare Pages project.
3. Use no build command and serve the repository root.
4. Configure Cloudflare Access separately from this repository. The public redirect page should be protected by the destination allowlist in `index.html`, not by a Zero Trust login gate.
