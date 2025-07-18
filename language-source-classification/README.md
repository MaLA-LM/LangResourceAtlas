### Language Source Classification
#### language-source-classification-by-fineweb2
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

#### language-source-classification-by-Joshi
The classification is based on [Joshi et al.'s work](https://microsoft.github.io/linguisticdiversity/assets/lang2tax.txt). 
Resource levels are divided into six categories, from 0 (lowest) to 5 (highest). Since the original classification only included language names without the corresponding ISO 639-3 codes and scripts, we used `Gemini-2.5-Pro` and `Grok-3` to annotate them. If the annotations from the two models were inconsistent, we conducted a secondary annotation using `DeepSeek-V3`.

The prompt we used is as follows:
```
<original classification>
Convert all of the above languages to ISO 639-3 codes plus script, e.g., English is eng_Latn.
If a language does not have an ISO 639-3 code, skip it.
The number 0–5 after each language indicates its resource level, with 0 being the lowest. Please group the results by resource level.
```
The final output is a JSON file with three sections:
```json
{
  "0": [ { "lang_code": "...", "lang_name": "..."}, ... ],
  "1": [ { "lang_code": "...", "lang_name": "..."}, ... ],
  "2": [ { "lang_code": "...", "lang_name": "..."}, ... ],
  "3": [ { "lang_code": "...", "lang_name": "..."}, ... ],
  "4": [ { "lang_code": "...", "lang_name": "..."}, ... ],
  "5": [ { "lang_code": "...", "lang_name": "..."}, ... ]
}

```