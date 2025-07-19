### Language resource classification by FineWeb2

The classification is based on the [distribution](https://github.com/huggingface/fineweb-2/blob/main/fineweb2-language-distribution.csv) of FineWeb2 Dataset. For each unique language, the `word` counts from all splits (train, test, etc.) are summed to obtain the total number of words for that language variety.

All language varieties are sorted by their total word counts.
- The bottom third are assigned to the low-resource tier
- The middle third to the mid-resource tier
- The top third to the high-resource tier

The final output is a JSON file with three sections:
```json
{
  "low": [ { "lang_code": "...", "lang_name": "...", "words": ... }, ... ],
  "mid": [ { "lang_code": "...", "lang_name": "...", "words": ... }, ... ],
  "high": [ { "lang_code": "...", "lang_name": "...", "words": ... }, ... ]
}

```