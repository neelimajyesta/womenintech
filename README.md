# Women in Tech 2026 — Speaker Guide (Protected)

Private deck for the WIT 2026 session: *The Future of Tech: How Women Product Managers Can Shape Industry Trends.*

Pages are encrypted with [StatiCrypt](https://github.com/robinmoisson/staticrypt) — visitors must enter the password to decrypt and view.

## Re-encrypting after edits

Source HTML lives outside this repo at `../product-manager-agent/assets/`. To rebuild:

```bash
# Stage updated sources
cp ../product-manager-agent/assets/wit-speaker-guide.html _src/index.html
cp ../product-manager-agent/assets/operational-learning.html _src/operational-learning.html

# Re-encrypt (uses the salt in .staticrypt.json so existing sessions keep working)
npx staticrypt _src/index.html -p 'LetsR@ck' --remember 30 --short -d .
npx staticrypt _src/operational-learning.html -p 'LetsR@ck' --remember 30 --short -d .

git add index.html operational-learning.html
git commit -m "Update encrypted deck"
git push
```
