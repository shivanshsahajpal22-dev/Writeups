# DATA FORMATS 
**~ this will teach you how to look at any data stream and know what file or data format it is ~**

## File streams
> look at the start of the data stream to identify file type 
> use hex dump to look at the hex dumps of these files 

1. %PDF → PDF
2. \x89PNG → PNG
3. PK\x03\x04 → ZIP (also .docx, .xlsx, .jar — they're all zips inside)
4. \xFF\xD8\xFF → JPEG
5. GIF87a/GIF89a → GIF
6. \x7fELF → Linux executable
7. MZ → Windows executable

## Data formats
1. 0-9a-f (or A-F), even length → hex
2. A-Z a-z 0-9 + / with = padding at the end -> base64
3. Lots of %XX sequences → URL encoding
4. Three chunks separated by dots, starting with eyJ -> JWT
5. -----BEGIN CERTIFICATE----- / -----BEGIN RSA PRIVATE KEY----- → PEM format
6. -----BEGIN PGP MESSAGE----- → PGP/GPG
7. Starts with Salted__ → output of openssl enc

## Different hashes 
1. 32 hex chars (128 bits) → MD5
2. 40 hex chars → SHA-1
3. 64 hex chars → SHA-256
4. Starts with $2a$, $2b$, or $2y$ → bcrypt
5. Starts with $argon2 → Argon2

## looks like gargabe ??
> is data looks like garabe then do this
> run "binwalk -E somefile" and if entropy is 8+ it conpressed or encrypted
> compressed have following starting bytes -> gzip = 1f 8b, zip = PK, zstd = 28 b5 2f fd
> there is no point if its encryption 
