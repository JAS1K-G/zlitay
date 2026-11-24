# zlitay

Static website, deployed to Hostpro.ua hosting automatically.

- `site/` holds the website files. Everything in it is uploaded to the hosting.
- Every push to `main` that changes `site/` runs `.github/workflows/deploy.yml` and uploads the changes over FTP(S).
- A manual run is available in **Actions → Deploy to Hostpro → Run workflow**.

## Secrets (Settings → Secrets and variables → Actions)

| Secret | Required | Value |
|---|---|---|
| `FTP_SERVER` | yes | FTP host from the Hostpro panel |
| `FTP_USERNAME` | yes | login of a separate FTP account limited to the site folder |
| `FTP_PASSWORD` | yes | that account's password |
| `FTP_DIR` | no | folder on the server, with a trailing slash, e.g. `public_html/`. Default `./` (the FTP account's own root) |
| `FTP_PROTOCOL` | no | `ftps` (default) or `ftp` if FTPS is not available |

Until the required secrets are set, the workflow finishes without uploading anything.
