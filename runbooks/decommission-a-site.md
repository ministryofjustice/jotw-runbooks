---
category: Runbooks
expires: 2022-01-31
---

# Decommissioning a website

## Required

* WASM
* AWS access
* You'll also need to be connected to the VPN.

## Steps

1. Double-check and confirm site is to be decommissioned.
2. Implement redirects if necessary using team NGINX URL redirect.
3. Archive the GitHub repo. This can be done using the [GitHub archive button](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/archiving-repositories).
4. In AWS, go to s3 bucket `s3://decommissioned-site-archival-store`, and create a new folder (named after the website/app being decommissioned) to put the decommissioned site content in.
5. Create a text file in the new folder with some meta data about the decommissioned site. Here are some example meta fields you might want to include:
```
site url: taxcentreofexcellence.uk
decommission date: 05.05.21
Code repo:  https://github.com/ministryofjustice/wp-taxcentreofexcellence
```
6. Make a copy of the site's database. This can be done using WASM. Run, `wasm db:export <site name>:prod wordpress.sql` and upload to the newly created .sql file to the new s3 folder mentioned above.
7. Next, move site related assets (images,docs,media) into the new s3 folder. You can download the production asset folder from s3 and re-upload it to the new archive folder but it's easier to directly copy from one s3 folder to another. Example, run `aws s3 cp s3://<production site s3 bucket name>/ s3://decommissioned-site-archival-store/<new folder name>/ --recursive`.
8. Delete all s3 bucket environments (dev, staging, prod). If you’re unsure what buckets they are, refer to the CloudFormation template, under `Resources`.
9. Delete the site's CloudFormation template (prod, staging, dev).
10. Delete the site's CodePipline.
11. Check WASM to see site has disappeared, `wasm aws:status`. May take a few mintues.
12. Update team logs so they reflect the site has been removed - [Site checklist (Google Docs)](https://docs.google.com/spreadsheets/d/1-bppj_FYZL4oCcuA8jNuOkW2L8j6V39Hnx_9b1utRbY/edit?usp=sharing)

Update the DM or PM and/or ticket to confirm decommission has been completed. Additional information also available at
[Decommission a website (Confluence)](https://dsdmoj.atlassian.net/wiki/spaces/JOWJ/pages/1562706189/Decommission+a+WP+website)