
### Language resource classification by Joshi et al.
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

#### Limitations
- Based on publications in CL/NLP venues
- The original classification is provided by language name, lacking standardized language code for unification. Automatic mapping from language name to ISO codes might have some errors. 