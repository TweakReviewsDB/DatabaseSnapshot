# TweakReviewsDB Database Snapshot

This is a dump of TweakReviewsDB created on July 7, 2021. The database had stopped accepted new reviews on March 10, 2021 so the database hasn't changed since March.

## Usage

**API Base:** https://raw.githubusercontent.com/TweakReviewsDB/DatabaseSnapshot/main

TweakReviewsDB contains two types of reviews called content reviews and compatibility reviews. Content reviews contain text and star ratings and they cannot be filtered while compatibility reviews show whether a package works or not and they can be filtered by iOS version, package version and device model.

### `/packages/:package.json`

Returns content reviews for a given package. Reviews for all versions of the package will be returned.

#### Example Response

```json
{
  "reviews": [
    {
      "stars": 2,
      "username": null,
      "content": "The tweak barely works for me.",
      "version": "1.1",
      "ios": "14.5",
      "date": "2020-01-14T23:31:44.000Z"
    }
  ],
  "stars": {
    "1": 30,
    "2": 21,
    "3": 10,
    "4": 6,
    "5": 11
  },
  "averageStars": 2.32
}
```

### `/packages/:package/:version/:ios/:model.json`

Returns compatibility reviews for a given package. `version`, `ios` and `model` are used as filters. You can specify `any` for these parameters.

#### Example Response

```json
{"status":{"working":196,"partial":4,"broken":13}}
```