# figuresforcongress-apex-redirect

Serves the bare domain `figuresforcongress.com` and redirects it to
`https://www.figuresforcongress.com`, which is the Cloudflare Pages site.

This repo exists because the campaign's DNS is hosted at Wix, and a bare domain
cannot be a CNAME. So the apex points at GitHub Pages by A record and GitHub
does the redirect, while `www` CNAMEs straight to Cloudflare Pages.

`404.html` is a copy of `index.html` on purpose: GitHub Pages serves it for any
unknown path, so `figuresforcongress.com/issues` redirects to
`www.figuresforcongress.com/issues` rather than showing a 404.

DNS at Wix:

    CNAME  www  figuresforcongress.pages.dev
    A      @    185.199.108.153
    A      @    185.199.109.153
    A      @    185.199.110.153
    A      @    185.199.111.153

Do not touch the MX, SPF, DKIM or DMARC records on that domain. The campaign's
mail runs through Google and NGP VAN.
