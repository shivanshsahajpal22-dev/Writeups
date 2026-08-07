# DATA FORMATS 
**This will teach you how to look at any data stream and know what file or data format it is**

## File streams
> look at the start of the data stream to identify file type

> use hex dump to look at the hex dumps of these files 

```
1. %PDF → PDF
2. \x89PNG → PNG
3. PK\x03\x04 → ZIP (also .docx, .xlsx, .jar — they're all zips inside)
4. \xFF\xD8\xFF → JPEG
5. GIF87a/GIF89a → GIF
6. \x7fELF → Linux executable
7. MZ → Windows executable
```

## Data formats
```
1. 0-9a-f (or A-F), even length → hex / base16 
2. A-Z a-z 0-9 + / with = padding at the end -> base64
3. Lots of %XX sequences → URL encoding
4. Three chunks separated by dots, starting with eyJ -> JWT
5. -----BEGIN CERTIFICATE----- / -----BEGIN RSA PRIVATE KEY----- → PEM format
6. -----BEGIN PGP MESSAGE----- → PGP/GPG
7. Starts with Salted__ → output of openssl enc
```
## OTHER BASE ENCODING
```

```
## Different hashes 
```
1. 32 hex chars (128 bits) → MD5
2. 40 hex chars → SHA-1
3. 64 hex chars → SHA-256
4. Starts with $2a$, $2b$, or $2y$ → bcrypt
5. Starts with $argon2 → Argon2
```
## Different Access keys
1. Amazon Web Services (AWS)
```
- **`AKIA...`** — IAM User Access Key ID (Permanent long-term credentials)
- **`ASIA...`** — IAM Temporary Access Key ID (AWS STS session / assumed role)
- **`AROA...`** — IAM Role Unique Identifier
- **`AIDA...`** — IAM User Unique Identifier
- **`AGPA...`** — IAM Group Unique Identifier
- **`ANPA...`** — AWS Managed Policy Unique Identifier
- **`ANVA...`** — AWS Policy Version Identifier
- **`ABIA...`** — AWS Service Bearer Access Key ID
- **`ACCA...`** — AWS Context-Specific Credentials
```
2. Google Cloud Platform (GCP) & Firebase
```
- **`AIzaSy...`** — GCP / Firebase API Key (39 characters starting with `AIza`)
- **`ya29....`** — Google OAuth 2.0 Access Token
- **`"type": "service_account"`** — GCP Service Account Key File (JSON structure)
```

3. Microsoft Azure
```
- **`~` prefix + 34–40 chars** — Azure AD Client Secret
- **`eyJ...`** — Azure Bearer Access Token (Base64 JWT header format)
- **`8-4-4-4-12 UUID format`** — Azure Tenant ID / Subscription ID / Client Application ID
```

4. Developer Platforms & Package Managers
```
GitHub
- **`ghp_...`** — Personal Access Token (Classic)
- **`github_pat_...`** — Fine-Grained Personal Access Token
- **`gho_...`** — OAuth Access Token
- **`ghu_...`** — User-to-Server Token
- **`ghs_...`** — Server-to-Server Token
- **`ghr_...`** — Refresh Token

GitLab & Other DevOps
- **`glpat-...`** — GitLab Personal Access Token
- **`glrt-...`** — GitLab Runner Registration / Job Token
- **`glagent-...`** — GitLab Agent Token
- **`pypi-...`** — PyPI API Token
- **`npm_...`** — npm Access Token
```
AI & Machine Learning Platforms
```
- **`sk-proj-...`** — OpenAI Project API Key
- **`sk-admin-...`** — OpenAI Admin API Key
- **`sk-ant-api...`** — Anthropic Claude API Key
- **`hf_...`** — Hugging Face User Access Token
- **`pplx-...`** — Perplexity API Key
```
Payments & Financial Infrastructure (Stripe)
```
- **`sk_live_...`** — Stripe Live Secret Key
- **`sk_test_...`** — Stripe Test Secret Key
- **`pk_live_...`** — Stripe Live Publishable Key
- **`pk_test_...`** — Stripe Test Publishable Key
- **`rk_live_...`** — Stripe Live Restricted Key
- **`whsec_...`** — Stripe Webhook Signing Secret
```
Communications & Cloud Services
```
- **`xoxb-...`** — Slack Bot User Token
- **`xoxp-...`** — Slack User Access Token
- **`xapp-...`** — Slack App-Level Token
- **`AC...` (32 hex characters)** — Twilio Account SID
- **`SK...` (32 hex characters)** — Twilio API Key SID
- **`SG....`** — SendGrid API Key
- **`hvs....`** — HashiCorp Vault Service Token
- **`hvb....`** — HashiCorp Vault Batch Token
```

## looks like garbage??
```
> is data looks like garbage, then do this
> run "binwalk -E somefile" and if entropy is 8+ it is compressed or encrypted
> compressed have following starting bytes -> gzip = 1f 8b, zip = PK, zstd = 28 b5 2f fd
> there is no point if its encryption
```
