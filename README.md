# Personal Automation Assistant — OAuth information website

This repository hosts the public OAuth information website for a private Personal Automation Assistant.

Production domain: https://oauth.fun24storage.com.tw

Deployment target: **Zeabur Static Site**

## Files

- `index.html` — application homepage.
- `privacy.html` — Privacy Policy.

Both pages use plain HTML with inline CSS and system fonts. There are no frameworks, JavaScript, Node.js dependencies, cookies, analytics, third-party tracking, or login requirements. No build step, secrets, environment variables, or backend are required.

## Before publishing

Replace every `CONTACT_EMAIL_HERE` occurrence in `index.html` and `privacy.html` with the application owner's real contact email. The placeholder is plain text, so no broken email link is created. Confirm that the policy matches the actual application's data handling before publishing, including any processors used by automation workflows.

## Deployment

1. Push this repository to GitHub, preferably as `openclaw-oauth-site`. Keep `index.html` and `privacy.html` at the repository root.
2. Create a **new service** in Zeabur dedicated to this website, separate from the existing OpenClaw service.
3. Deploy this GitHub repository as a **Static Site**. Use the repository root as the service root. Zeabur detects this plain HTML repository as static content; no install command or build command is needed.
4. Generate a temporary `zeabur.app` domain and test both `/` and `/privacy.html`. Click Privacy Policy and Back to Home and confirm that the correct page appears without signing in.
5. Add the custom domain: `oauth.fun24storage.com.tw`.
6. Configure **only the DNS record for `oauth.fun24storage.com.tw`** using the type and target Zeabur provides. Do not guess the target or replace other records.
7. Verify both pages over HTTPS:
   - https://oauth.fun24storage.com.tw/
   - https://oauth.fun24storage.com.tw/privacy.html

**DO NOT point this repository or deployment to: `openclaw.fun24storage.com.tw`.**

That hostname is used by the actual OpenClaw application. Do not modify its service, deployment, domain binding, or DNS records. Creating this repository does not deploy anything or change Google Cloud OAuth credentials.

Deployment reference: [Zeabur static website documentation](https://zeabur.com/docs/en-US/guides/static).

## Local preview and checks

Serve this directory with any static HTTP server. For example, if Python is already installed, run the following from this repository (Python is only a local preview option, not a deployment dependency):

```sh
python -m http.server 8080 --bind 127.0.0.1
```

Open http://127.0.0.1:8080/ and http://127.0.0.1:8080/privacy.html. Use HTTP for navigation checks: the required root-relative links `/` and `/privacy.html` expect a website root rather than a `file://` location.

- Confirm both pages load anonymously and each navigation link reaches the correct page.
- Check mobile and desktop widths for readable text and no horizontal overflow.
- Confirm no external CSS, scripts, fonts, tracking requests, or cookies are introduced. The favicon is embedded directly in each page.
- Keep tokens, client secrets, credentials, and personal Google data out of this public repository.

## Suggested Google OAuth Branding configuration

| Setting | Value |
| --- | --- |
| App name | Personal Automation Assistant |
| Application homepage | https://oauth.fun24storage.com.tw/ |
| Privacy Policy | https://oauth.fun24storage.com.tw/privacy.html |
| Authorized domain | fun24storage.com.tw |

`oauth.fun24storage.com.tw` is the public information website.

`openclaw.fun24storage.com.tw` is the actual OpenClaw application.

These hostnames have different purposes and must not be interchanged. The public information website is not an OAuth callback endpoint. These are suggested Branding settings only; this repository does not modify OAuth credentials or redirect URIs.
