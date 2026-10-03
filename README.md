# nepali-canonical

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A definitive, open-source collection of Nepali words, place names, and administrative divisions for developers, data scientists, and content creators.

---

## 🤔 Why Does This Repository Exist?

The Nepali language has many words that can be transliterated into English in multiple ways. This creates inconsistency in digital products, databases, and user interfaces. Furthermore, even within the Nepali script, there can be ambiguity about the official or most common spelling.

A classic example is the name of a province, **Koshi**. Which is the correct Nepali spelling?

- `कोशि`
- `कोशी`
- `कोसी`

Without a standard, different applications will store and display this data differently, leading to confusion and data integrity issues. This repository serves as a **single source of truth** to solve that problem.

## 🎯 Our Goal

To create and maintain a high-quality, accurate, and accessible dataset that provides standardized spellings for:

- Nepal's administrative divisions (provinces, districts, municipalities).
- Commonly used words and phrases in the digital world.
- Official names of places and landmarks.

## 🗂️ What's Included?

This repository contains data structured for easy use, primarily in JSON format. The core data includes:

- **Administrative Divisions:**
  - Provinces
  - Districts
  - Metropolitan Cities (`महानगरपालिका`)
  - Sub-Metropolitan Cities (`उप-महानगरपालिका`)
  - Municipalities (`नगरपालिका`)
  - Rural Municipalities (`गाउँपालिका`)
- **Common Digital Terms:** (e.g., "Home" -> `गृह`, "Settings" -> `सेटिङहरू`)

## 🚀 How to Use

You can directly use the JSON files in your projects.

For example, to get a list of districts/municipalities in Bagmati Province, you might parse the `municipalities.json.json` file.

**Example Snippet (`municipalities.json.json`):**

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
          // ... list of municipalities in Kathmandu
        ]
      },
      {
        "district_name_english": "Lalitpur",
        "district_name_nepali": "ललितपुर",
        "municipalities": [
          // ... list of municipalities in Lalitpur
        ]
      }
    ]
  }
}
```
