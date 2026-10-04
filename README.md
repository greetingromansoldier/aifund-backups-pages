# AIFund Backups information pages

Static source for the AIFund Backups information website. Deployment status
is tracked in the separate repository's GitHub Pages deployment history.

Two small public pages for the AIFund Backups Google OAuth configuration.
They describe the utility and its intended data handling. They are not a
backup implementation or evidence that backups are running.

## Files

- `index.html`: application homepage and link to the privacy policy.
- `privacy.html`: Google Drive permissions, data handling, and access removal.
- `styles.css`: local shared stylesheet; no remote fonts or scripts.
- `.nojekyll`: serve the static files directly on GitHub Pages.
- `.gitignore`: guard against common credentials and backup artifacts.
- `README.md`: these publication instructions.

No build, framework, package installation, database, JavaScript, or backend
is required. Public content is written in simple English. The contact email
matches the support email shown in the operator's Google OAuth screenshots.

## Local preview on the Mac

Run from this directory:

```sh
python3 -B -m http.server 8765 --bind 127.0.0.1 --directory .
```

Open `http://127.0.0.1:8765/` and
`http://127.0.0.1:8765/privacy.html` in the browser. Stop the preview with
Ctrl+C. Do not serve the parent workspace or bind this preview to all network
interfaces.

## Publish only after operator approval

Use a separate repository named `aifund-backups-pages`. A new repository is
not technically required by Pages, but it isolates the public website from
trading code and private operational data. GitHub Pages may be public even
when the source repository is private. GitHub Free supports Pages in public
repositories.

1. Confirm the GitHub account or organization that should own the site.
2. On GitHub: **+ → New repository**. Select that owner and enter
   `aifund-backups-pages`. Use **Public** for the free Pages option. Review the
   visibility before creating the repository.
3. Upload or commit only the six files listed above. Do not import the trading
   repository or upload the parent workspace. Do not copy OAuth JSON, rclone
   configuration, environment files, backup archives, or database exports.
4. In this repository: **Settings → Pages → Build and deployment**.
   Select **Source: Deploy from a branch**, **Branch: main**, **Folder: /(root)**,
   then **Save**.
5. Wait for deployment and open the actual URL shown in **Settings → Pages**.
   Verify that both pages and the stylesheet are accessible without login,
   including the link from the homepage to the privacy policy.

`.gitignore` does not protect files already tracked, files force-added to Git,
or files uploaded through the GitHub website. Review the exact publication
allowlist before every upload or commit. No production server or firewall
change is needed for this website.

## Set the Google OAuth links

After the actual deployment has been checked, select `aifund-backups` in
Google Cloud Console and open **Google Auth Platform → Branding → App domain**.

Set **Application home page** to the real published homepage URL. Set
**Application privacy policy link** to the same site's `privacy.html` URL.
Add the site's hostname under **Authorized domains**, without a scheme or
path, as accepted by Google. Click **Save**.

Then open **Audience → Publish app** and check the resulting publishing
status. If Google requests domain ownership verification or another review,
follow the actual prompt; preparing these pages does not guarantee acceptance.
Use URLs that you control, not unrelated websites or a private platform URL.

The target site will normally be a project site with the repository name in
its path. All local links are relative, so the pages work in that subdirectory
as well as in the local preview. No URL is presented here as already deployed.

## Keep the policy consistent

Review the text before publication. The encryption and credential restrictions
are requirements of the intended backup procedure, not a claim that the
server job has been installed. If the actual scopes, data handling, hosting,
or retention practices change, update the policy and effective date.

## References

- [rclone: creating a Google OAuth client, including the Pages suggestion](https://rclone.org/drive/#making-your-own-client-id).
- [Google: homepage and privacy policy requirements](https://developers.google.com/identity/protocols/oauth2/production-readiness/brand-verification).
- [Google: Drive permission scopes](https://developers.google.com/workspace/drive/api/guides/api-specific-auth).
- [GitHub: creating a Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site).
