# Women in Tech 2026 — Speaker Deck (Protected)

Private deck for the WIT 2026 session: *The Future of Tech: How Women Product Managers Can Shape Industry Trends.*

Pages are encrypted with [StatiCrypt](https://github.com/robinmoisson/staticrypt) — visitors must enter the shared password to decrypt and view. The password is **not** stored in this repo; ask the speaker directly.

## Layout

| File | Purpose |
| --- | --- |
| `index.html` | Current deck (encrypted) |
| `index-v1.html` | Previous deck snapshot kept for rollback |
| `operational-learning.html` | Live POC walkthrough (encrypted) |
| `src/` | Plaintext sources — untracked, kept local |

## Re-encrypting after edits

Sources live under `src/`. After editing, re-encrypt and replace the root file. Pass the password via the `WIT_PW` environment variable so it never lands in shell history or this README:

```bash
# Encrypt the deck source → root index.html
WIT_PW='<shared-password>' npx staticrypt src/index2.html -p "$WIT_PW" --remember 30 --short -d .
mv index2.html index.html

# Encrypt the POC the same way
WIT_PW='<shared-password>' npx staticrypt src/operational-learning.html -p "$WIT_PW" --remember 30 --short -d .

git add index.html operational-learning.html
git commit -m "Update encrypted deck"
git push
```

`.staticrypt.json` holds the salt — existing browser sessions keep working across re-encryptions.

## Rollback

```bash
cp index-v1.html index.html
git add index.html && git commit -m "Rollback deck" && git push
```
