# nepali-canonical

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

Standardized Nepali and English names for Nepal's provinces, districts, and local levels, as ready-to-use JSON for developers, data scientists, and content creators.

---

## 🤔 Why Does This Repository Exist?

The Nepali language has many words that can be transliterated into English in multiple ways. This creates inconsistency in digital products, databases, and user interfaces. Furthermore, even within the Nepali script, there can be ambiguity about the official or most common spelling.

A classic example is the name of a province, **Koshi**. Which is the correct Nepali spelling?

- `कोशि`
- `कोशी`
- `कोसी`

Without a standard, different applications will store and display this data differently, leading to confusion and data integrity issues. This repository aims to be a **single source of truth** to solve that problem.

## 🗂️ What's Included?

| File | Contents |
| --- | --- |
| [`name-of-places/provinces.json`](name-of-places/provinces.json) | All 7 provinces in Nepali and English, with the number of districts in each. |
| [`name-of-places/municipalities.json`](name-of-places/municipalities.json) | All 77 districts and 753 local levels, nested by province → district → local level. |

Each local level has its name in Nepali and English, its type, and its number of wards (in both Arabic and Nepali digits). Types are:

- Metropolitan City (`महानगरपालिका`)
- Sub-Metropolitan City (`उपमहानगरपालिका`)
- Municipality (`नगरपालिका`)
- Rural Municipality (`गाउँपालिका`)

## 🚀 Quick Start

No install needed. Load the JSON straight from the jsDelivr CDN:

```
https://cdn.jsdelivr.net/gh/ritushishir/nepali-canonical@main/name-of-places/provinces.json
https://cdn.jsdelivr.net/gh/ritushishir/nepali-canonical@main/name-of-places/municipalities.json
```

**JavaScript**

```js
const url =
  "https://cdn.jsdelivr.net/gh/ritushishir/nepali-canonical@main/name-of-places/municipalities.json";
const data = await fetch(url).then((res) => res.json());

const kathmandu = data.Bagmati.districts.find(
  (d) => d.district_name_english === "Kathmandu"
);
console.log(kathmandu.municipalities.map((m) => m.municipality_name_nepali));
```

**Python**

```python
import json
import urllib.request

url = "https://cdn.jsdelivr.net/gh/ritushishir/nepali-canonical@main/name-of-places/municipalities.json"
data = json.load(urllib.request.urlopen(url))

for district in data["Bagmati"]["districts"]:
    print(district["district_name_english"], len(district["municipalities"]))
```

You can also download or vendor the files directly from this repository.

## 📐 Data Format

`municipalities.json` is keyed by province name in English:

```json
{
  "Bagmati": {
    "province_name_english": "Bagmati",
    "province_name_nepali": "बागमती",
    "districts": [
      {
        "district_name_english": "Kathmandu",
        "district_name_nepali": "काठमाडौँ",
        "municipalities": [
          {
            "municipality_name_english": "Kathmandu",
            "municipality_name_nepali": "काठमाडौँ",
            "type": "Metropolitan City",
            "type_nepali": "महानगरपालिका",
            "ward_count": 32,
            "ward_count_nepali": "३२"
          }
        ]
      }
    ]
  }
}
```

`provinces.json` provides simple name lists plus per-province details:

```json
{
  "names_in_nepali": ["कोशी", "मधेश", "बागमती", "..."],
  "names_in_english": ["Koshi", "Madhesh", "Bagmati", "..."],
  "names_with_number_of_districts": [
    { "name_in_nepali": "कोशी", "name_in_english": "Koshi", "number_of_districts": 14 }
  ]
}
```

## 🛣️ Roadmap

- Stable official IDs for provinces, districts, and local levels
- Flat files and CSV exports alongside the nested JSON
- Automated validation of the data in CI
- npm and PyPI packages
- Commonly used digital terms (e.g., "Home" → `गृह`, "Settings" → `सेटिङहरू`)
- Official names of landmarks and other places

## 📚 Sources

**Official totals.** The data matches the official counts of local levels and wards published by Nepal's Ministry of Federal Affairs and General Administration (MoFAGA):

- [स्थानीय तह (Local Levels) portal: sthaniya.gov.np/gis](https://sthaniya.gov.np/gis/): 6 metropolitan cities, 11 sub-metropolitan cities, 276 municipalities, 460 rural municipalities (753 local levels), 77 districts, and 6,743 wards. Last checked October 2026.

**Official list of local levels (Nepali).** MoFAGA also publishes every local level with its Nepali name, district, type, and province:

- [स्थानीय तहहरुको वेवसाईटको विवरण: sthaniya.gov.np/gis/website](https://sthaniya.gov.np/gis/website): used to confirm which local levels exist and their current names, including renames such as Dodhara Chandani (formerly Mahakali) in Kanchanpur.
- [स्थानीय तहको केन्द्र तथा नाम परिवर्तनको विवरण: mofaga.gov.np/lg-changes](http://mofaga.gov.np/lg-changes): changes to local-level names and headquarters.

> **Note on spelling:** The official list is the authority on *which* local levels exist and *what* they are called, but its spellings are not always consistent (for example, `ब`/`व` and `ङ`/`ङ्ग` are used interchangeably, and some entries contain hidden zero-width characters). Spellings in this repository are standardized, so they may differ slightly from that list.

There is no official government list of English names. Where English spellings vary, each local level's own official website (linked from the list above) is the best reference.

**Cross-checks.** These sources were used to verify individual local levels, ward counts, and names:

- [sagautam5/local-states-nepal](https://github.com/sagautam5/local-states-nepal): an open dataset of provinces, districts, and local levels with ward counts
- [Municipalities of Nepal](https://en.wikipedia.org/wiki/Municipalities_of_Nepal) and [List of rural municipalities in Nepal](https://en.wikipedia.org/wiki/List_of_rural_municipalities_in_Nepal) on English Wikipedia
- Ward-level tables on [Nepali Wikipedia](https://ne.wikipedia.org/) pages for individual local levels

## 🤝 Contributing

Found a spelling that doesn't match the official one? Please [open an issue](https://github.com/ritushishir/nepali-canonical/issues) and include a source (e.g., a government publication or website) so the correction can be verified.

## 📄 License

This dataset is licensed under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). See [LICENSE](LICENSE) for the full text.

You are free to use, share, and adapt it, including commercially, as long as you give credit. For example:

> Data from [nepali-canonical](https://github.com/ritushishir/nepali-canonical), licensed under CC BY 4.0.
