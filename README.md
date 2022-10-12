# PSR6 Symfony HTTP Cache Store Analyser

Analyse what URL and Tags are stored in [toflar/psr6-symfony-http-cache-store](github.com/toflar/psr6-symfony-http-cache-store) HTTP Cache store.

## Usage

```bash
git clone git@github.com:alexander-schranz/psr6-symfony-http-cache-store-analyser.git analyser
cd analyser
```

Copy your `http_cache` directory into `var` directory so its available under `var/http_cache/@`.

Run the analyser:

```bash
bin/analyse var/http_cache
```

Output is something like this:

```bash
URL: https://example.org/
CACHE-CONTROL: max-age=240, public, s-maxage=86400
X-REVERSE-PROXY-TTL: 86400
FOS-SMAXAGE-BACKUP: 240
TAGS (2): media-1,page-2
QUERIES (4):
 -
 - ?utm_campaign=some&utm_content=content&utm_medium=newsletter&utm_source=anysource
 - ?page=1
 - ?page=2
 
------------------------------------------------------------------------------------------------

URL: https://example.org/other
CACHE-CONTROL: max-age=240, public, s-maxage=86400
X-REVERSE-PROXY-TTL: 86400
FOS-SMAXAGE-BACKUP: 240
TAGS (1): media-2
QUERIES (1):
 -

```

It is also possible to filter out a specific url only:

```bash
bin/analyse var/http_cache https://example.org/other
```
