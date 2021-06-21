# cse-latex-202104

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/lukeolson/cse-latex-202104/HEAD?urlpath=lab)

To build the html file for the EGAP Guide

```
pandoc --css latex-guide.css --standalone -N  --from=markdown+yaml_metadata_block -V date="Version of $(date +%Y-%b-%d%n)" latex-guide.md -o latex-guide.html
```
