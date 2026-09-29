# bayoulanding-site

Resident info site for the Bayou Landing HOA, live at https://bayoulandinghoa.com.

Static HTML/CSS/JS, no build step. Files in `site/` are served as-is by nginx.

## Authoring source

The authoring source is `hoaAssistant/site` on Omar's Mac, not this repo. This repo is a published copy. The parent `hoaAssistant/` folder holds private resident data and must never be committed, which is why this is a separate folder.

To update the repo, re-rsync `site/` into this folder and commit:

```sh
rsync -a --delete --exclude .DS_Store /Users/omar/Downloads/hoaAssistant/site/ site/
git add -A && git commit -m "Update site" && git push
```

Review `git diff --stat` and scan for personal data before committing.

## Deploying

```sh
rsync -av --delete --exclude '.DS_Store' site/ homelab:/home/omar/bayoulanding-site/site/
```

## deploy/

`deploy/` holds the nginx container config (`docker-compose.yml`, `nginx.conf`) as it runs on the server. Reference copy only.
