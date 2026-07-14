# Hash Identifier

Paste a hash string and get a ranked list of the algorithms that could have produced it, based on length and format. It recognizes MD5, SHA-1, SHA-256, SHA-512, CRC32, bcrypt, argon2, NTLM, MySQL, base64-looking values, and several Unix crypt formats, and it is honest when the answer is ambiguous. Single self-contained file, no external dependencies, works offline.

## Live demo

https://0xelitesystem.github.io/hash-identifier/

## Features

- Ranked candidate list with a confidence label (high, medium, low) and a one-line note per match
- Length and character-set detection (hex, base64-like, or mixed)
- Prefixed schemes detected first: bcrypt (`$2a$`, `$2b$`, `$2y$`), argon2 (`$argon2i$`, `$argon2d$`, `$argon2id$`), md5crypt (`$1$`), sha256crypt (`$5$`), sha512crypt (`$6$`), LDAP SSHA
- MySQL 4.1+ (`*` then 40 hex) and old MySQL (16 hex) recognition
- Honest about ambiguity: when a length matches several algorithms (for example 32 hex for MD5, NTLM, and MD4) all are listed
- Base64-length hints (28, 44, 88 characters) that map to SHA-1, SHA-256, and SHA-512 byte sizes
- Quick reference table of common lengths and formats
- Dark-mode toggle, keyboard usable

## How it works

The tool inspects the shape of the string, not its meaning. It first checks for strong prefix signatures (bcrypt, argon2, Unix crypt, MySQL), then falls back to length plus character-set matching for bare hex and base64 strings. Confidence reflects how uniquely a shape maps to one algorithm: a bcrypt prefix is high confidence, while 32 hex characters is genuinely ambiguous.

This is format-based heuristic identification, not verification. It cannot confirm which algorithm actually produced a given hash, because many algorithms share the same length and alphabet. The interface states this plainly.

## Privacy

Everything runs in your browser. The hash you paste is never sent anywhere. There are no external scripts, fonts, stylesheets, or analytics. Open the page source to confirm. It works fully offline.

## License

MIT. Copyright 0xelitesystem 2026.
