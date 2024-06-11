# ghcr.io pulls

## JSON Endpoint for GHCR Badges

Makes the pull count badge possible for these ghcr.io packages:

[![timeplus-io/proton/proton](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fipitio%2Fghcr-pulls%2Fmaster%2Findex.json&query=%24%5B%3F(%40.owner%3D%3D%22timeplus-io%22%20%26%26%20%40.repo%3D%3D%22proton%22%20%26%26%20%40.image%3D%3D%22proton%22)%5D.pulls&label=Docker%20Pull)](https://github.com/timeplus-io/proton/pkgs/container/proton)

If we don't yet follow an image, you can either:

* open an issue or
* add it on a new line in `pkg.txt` on your own fork [here](https://github.com/ipitio/ghcr-pulls/edit/master/pkg.txt) and make a pull request.

### Custom Badges

To make a badge, you can modify one of the badges above or generate one with something like [shields.io](https://shields.io/badges/dynamic-json-badge) and these parameters:

#### URL

```markdown
https://raw.githubusercontent.com/ipitio/ghcr-pulls/master/index.json
```

#### JSONPath

You can show either a pretty value like 12K or the raw number like 12345.

##### Pretty Count

```markdown
$[?(@.owner=="<USER>" && @.repo=="<REPO>" && @.image=="<IMAGE>")].pulls
```

##### Raw Count

```markdown
$[?(@.owner=="<USER>" && @.repo=="<REPO>" && @.image=="<IMAGE>")].raw_pulls
```

### Further Study

GHCR itself doesn't provide an API endpoint for the pull count, so Github Packages is scraped twice daily for every image in `pkg.txt`. In addition to the latest stats, the index also contains a history of the raw pull counts for each image, starting on 2024-06-10, should you find that useful or interesting. Should the pulls for each tag be kept individually as well?

### TODO

Feel free to help with any of these:

* [ ] Make a GitHub Pages site that integrates ghcr-pulls with [eggplants/ghcr-badge](https://github.com/eggplants/ghcr-badge) (or provides an alternative)
* [ ] Show each version:

```json
{
    ...,
    "version": {
        "<version>": {
            "raw_pulls": "365",
            "raw_pulls_day": "1",
            "raw_pulls_week": "7",
            "raw_pulls_month": "30",
            "raw_pulls_all": {
                "<date>": "365"
            }
        }
    }
}
```

* [ ] Any other improvements or ideas you have
