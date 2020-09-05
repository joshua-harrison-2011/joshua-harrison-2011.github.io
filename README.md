This repository exists to host https://southlandpto.com and redirect it to https://southlandpto.weebly.com.

`southlandpto.weebly.com` is a blog managed by the Soutland Elementary PTO.  The PTO did not want "weebly" included in the url.  While Weebly allows for this, it costs at least $72/year and the PTO is especially budget conscious this year, given Covid-19.

To make this happen, we did the following:

1. Registered `southlandpto.com` with GoDaddy.  The account is currently tied to the secretary, but could easily be moved to a shared Southland PTO GoDaddy account, if desired.

2. Inside GoDaddy, configured `southlandpto.com` to point to IP Addresses owned by GitHub.  I followed instructions [here](https://medium.com/@JinnaBalu/godaddy-domain-with-github-pages-62aed906d4ef), but more generic instructions are [here](https://docs.github.com/en/github/working-with-github-pages/configuring-a-custom-domain-for-your-github-pages-site).

3. Created this repository to be hosted in Github Pages.  It contains an `index.html` page that simply redirects to https://southlandpto.weebly.com.
It also contains a file called `CNAME` that contains "southlandpto.com" and in the GitHub page configuration, `Enforce SSL` is enabled.  I believe
this triggers Github to create an SSL certificate on my behalf using Let's Encrypt, but I'm not positive.

When you type `southlandpto.com` into your browser, it returns a page over SSL from GitHub that issues a client side redirect to `southlandpto.weebly.com`.

This approach has three downsides:

1. Once you land on `southlandpto.weebly.com`, you continue to see `weebly` in the URL.  This is not ideal, but the costs to address it are not currently acceptable.
2. There needs to be a GitHub account that hosts this content.  This isn't overly complicated, but it's also not the kind of thing that most people know how to do.
3. Because this is a client side redirect, you see `southlandpto.com` quickly and then it goes away.  This is acceptable, but not ideal.

Should we choose to invest the money in making this process more streamlined, we'd pay weebly $72 per year for their lowest tier paid plan, which would let us use our own custom domain.  We would then register our domain with them and they would create an SSL certificate on our behalf (using Let's Encrypt).  In addition, we'd need to point our domain at the weebly IP addresses in GoDaddy or transfer our domain from GoDaddy to weebly to handle that for us.

GoDaddy has a "forwarding" feature we tried to use first, where they point `southlandpto.com` at their servers and there is some lightweight server
config that redirects to `southlandpto.weebly.com`.  However, this doesn't support SSL and we were concerned that users might type `southlandpto.com
` into their broswers, see "Insecure" warnings, and not continue.
