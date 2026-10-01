![AstralOS Logo](logo-small.png)
# AstralOS OTA

Static OTA index for the AstralOS Updater. Device JSON files are served via GitHub Pages:

- `https://astralosproject.github.io/ota/<device>.json`

Build zips are attached to [GitHub Releases](https://github.com/AstralOSProject/ota/releases).

## Updating the index

For each new release:

1. Create a release and upload the zip.
2. Update `<device>.json` with a new entry:

```json
{
  "response": [
    {
      "datetime": <ro.build.date.utc of the build>,
      "filename": "<zip name>",
      "id": "<echo filename | sha1sum>",
      "romtype": "OFFICIAL",
      "size": <bytes>,
      "url": "<release asset URL>",
      "version": "<major.minor>"
    }
  ]
}
```

`datetime` must be greater than the installed build's `ro.build.date.utc`, and `version` must be `>= ro.lineage.build.version`.
