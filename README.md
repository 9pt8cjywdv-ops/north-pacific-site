# North Pacific website

One-page company site: `index.html` and `favicon.svg`. No build step.

Company details are in `index.html` (regulatory section, contact and footer).

## Hosting (free on GitHub Pages)

From this folder on the Mac:

```bash
gh repo create north-pacific-site --public --source . --push
gh api -X POST repos/9pt8cjywdv-ops/north-pacific-site/pages -f "source[branch]=main" -f "source[path]=/"
```

After a minute the site is live at `https://9pt8cjywdv-ops.github.io/north-pacific-site/`.

The repo is public because GitHub Pages is free only for public repos. That is fine for a website: everything in it is public anyway. Never put keys or private files here.

## Own domain (e.g. northpacific.co.za)

1. Buy the domain from a South African registrar.
2. In the registrar's DNS settings add:

   | Type | Name | Value |
   |---|---|---|
   | A | @ | 185.199.108.153 |
   | A | @ | 185.199.109.153 |
   | A | @ | 185.199.110.153 |
   | A | @ | 185.199.111.153 |
   | CNAME | www | 9pt8cjywdv-ops.github.io |

3. Tell GitHub the domain (replace with yours):

   ```bash
   gh api -X PUT repos/9pt8cjywdv-ops/north-pacific-site/pages -f cname=northpacific.co.za
   ```

4. Once DNS has updated (minutes to a few hours), turn on **Enforce HTTPS** under the repo's Settings → Pages.

## Updating the site

Edit `index.html`, then:

```bash
git commit -am "Update site" && git push
```
