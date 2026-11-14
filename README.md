# omk-attestation-mirror

A scheduled copy of `https://android.googleapis.com/attestation/status`, the
list of revoked and suspended Android attestation keys.

The workflow runs every 30 minutes and commits `status.json` only when the
content changed. Consumers that cannot reach `android.googleapis.com` can read
the same bytes from:

    https://raw.githubusercontent.com/qianxiao88/omk-attestation-mirror/main/status.json

The file is unmodified upstream content; its shape is:

    { "entries": { "<decimal serial>": { "status": "REVOKED", "reason": "..." } } }

Keys are decimal serial numbers, matching what `openssl_x509_parse` reports
after converting any `0x`-prefixed hex serial.
