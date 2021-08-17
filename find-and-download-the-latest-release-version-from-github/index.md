# Find and download the latest release version from GitHub


From this [gist](https://gist.github.com/steinwaywhw/a4cd19cda655b8249d908261a62687f8).

<!--more-->

```bash
curl -s https://api.github.com/repos/jgm/pandoc/releases/latest \
| grep "browser_download_url.*deb" \
| cut -d '"' -f 4 \
| wget -qi -
```

to download the latest release version of [pandoc](https://github.com/jgm/pandoc), for instance.

> - `curl` to get the JSON response for the latest release
> - `grep` to find the line containing file URL
> - `cut`  to extract the URL
> - `wget` to download it

