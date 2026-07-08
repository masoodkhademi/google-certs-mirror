# google-certs-mirror

Mirror of [Google's OAuth2 federated-signon certificates](https://www.googleapis.com/oauth2/v1/certs)
(`kid` → PEM), refreshed every 6 hours by GitHub Actions.

**Why:** Google returns `403 Forbidden` to Iranian datacenter IPs, so a server
hosted there cannot fetch the certs it needs to verify Google ID tokens.
GitHub's raw CDN *is* reachable from those servers, so the Loqme API reads
`certs.json` from here instead (`GOOGLE_CERTS_URL`). The certs are public keys —
nothing sensitive is stored or proxied.

Verification (signature, audience, issuer, expiry) still happens on the API
server itself; this repo only substitutes the key-distribution channel.
