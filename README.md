# Redirect

A lightweight redirect page. Shows the user where they're being sent, then redirects after a short countdown.

## Usage

Deploy to Cloudflare Pages (or any static host). Then link to it with a query parameter:

```
https://your-domain.com/?to=https://example.com
https://your-domain.com/?url=https://example.com
https://your-domain.com/?redirect=https://example.com
```

### Optional parameters

- `delay` or `d` — countdown seconds before redirect (default: 3, max: 30)

Example: `https://your-domain.com/?to=https://example.com&delay=5`

## Deploy to Cloudflare Pages

1. Push this repo to GitHub
2. Go to Cloudflare Dashboard → Pages → Create a project
3. Connect the `lversky/redirect` repo
4. Build settings: none needed (static site, no build step)
5. Deploy

## CNAME

Set your CNAME to point to the Cloudflare Pages URL, or use the `*.pages.dev` subdomain directly.