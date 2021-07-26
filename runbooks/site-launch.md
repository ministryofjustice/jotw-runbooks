---
category: Runbooks
expires: 2023-01-31
---

# Site launch steps (on multisite)

## Required

* WASM
* AWS access
* You'll also need to be connected to the VPN.

## Phases

This assumes all content is ready on the production environment.

### Phase I - Steps leading up to launch
1. Schedule a time with the domains team to repoint the domain (assuming they control the domain), to go live date of the launch. This involves providing three things to the domains team, 

- date/time, 
- new loadbalancer to point to and 
- the domain name being repointed.

So the information we provided for CCRC was as follows
```
go live date/time: Thursday 15th July at Midday (12)
multisite loadbalancer: jotwp-loadb-1mbwraz503eq6-1769122100.eu-west-2.elb.amazonaws.com
domain:  ccrc.gov.uk
```

2. Add the TLS certificate for the domain to the multisite loadbalancer. To do this, login to AWS and go to the mutlisite loadbalancer (on prod). Click on the `Listeners tab` and then on `View/edit Certificates` link under the HTTPS ID. From there you can add the new TLS cert you created for your domain.


### Phase II - Steps at time of launch
1. Deactivate `Force Login` plugin
2. Login to prod, change WP `Siteurl` and `Home` to the domain (for example add, https://ccrc.gov.uk).
3. Check site links are pointing to domain not jotwpublic.prod. If the links are wrong, you may need to run a wp search and replace command on the database. To do so, login to prod via WASM and run, for example `wp search-replace "jotwpublic.prod.wp.dsd.io/ccrc" "ccrc.gov.uk" --url=ccrc.gov.uk --dry-run` . Make sure to take the `--dry-run` when you want the changes to take effect.
4. Confirm with domains team repoint is done.


## Troubleshooting

After launching the site, some changes may not seem to be taking effect. Domain changes can take some time to propagate so it maybe be that not enough time has passed. Further, there may be caching issues. Try clearing the cache on the problem page first using your browser. You could also try caching the server (NGINX) cache. To do this add `/purge-cache/` to the end of the domain address. For example, `https://ima-citizensrights.org.uk/purge-cache/`. This only has to be run once to take effect across the entire domain. 