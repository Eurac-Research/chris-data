# CHRIS Publications Data

This repository contains the publications data for the CHRIS study website.

## JSON Structure

The publications are stored as a JSON object where each key is the DOI of the publication.

### Publication Object

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `title` | string | ✅ | The full title of the publication |
| `journal` | string | ✅ | Name of the journal |
| `year` | string | ✅ | Publication year (e.g., `"2025"`) |
| `volume` | string | ❌ | Journal volume number |
| `issue` | string | ❌ | Journal issue number |
| `pages` | string | ❌ | Page range (e.g., `"5434"` or `"123-145"`) |
| `pre` | boolean | ❌ | Whether this is a preprint (`true`) or peer-reviewed (`false`) |
| `doi` | string | ✅ | The DOI identifier (without `https://doi.org/` prefix) |
| `abstract` | string | ❌ | Publication abstract (supports formatting, see below) |
| `authors` | string[] | ✅ | Array of author names (e.g., `["Förster F", "Emmert D"]`) |
| `source_study` | string[] | ❌ | Array of source study names (e.g., `["CHRIS baseline"]`) |
| `pdate` | string | ❌ | Publication date in ISO format (e.g., `"2025-07-02"`) |
| `ar` | string | ❌ | Research area identifier |

### Abstract Formatting

The `abstract` field supports limited formatting:

| Syntax | Result | Example |
|--------|--------|---------|
| `**text**` | **Bold** | `**important**` |
| `*text*` | *Italic* | `*emphasis*` |
| `` `text` `` | `Code` | `` `gene_name` `` |
| `[text](url)` | Link | `[Nature](https://nature.com)` |
| `<br>` | Line break | `Line one<br>Line two` |
| `<sup>text</sup>` | Superscript | `10<sup>-8</sup>` |
| `<sub>text</sub>` | Subscript | `H<sub>2</sub>O` |
| `* item` | List item | `<br>* First item<br>* Second item` |

**Note:** List items must be preceded by `<br>` to render correctly.

### Contributing

When adding or modifying publications:

Do not change the JSON structure — all fields must follow the schema above
Use the DOI as the key — this ensures uniqueness
Keep author names consistent — use format "LastName Initials" (e.g., "Förster F")
Use ISO dates — format pdate as "YYYY-MM-DD"
Escape special characters — JSON requires escaping quotes and backslashes

### Example

```json
{
  "10.1038/s41467-025-61330-y": {
    "title": "Genome-wide association meta-analysis of human olfactory identification discovers sex-specific and sex-differential genetic variants.",
    "journal": "Nature communications",
    "year": "2025",
    "volume": "16",
    "issue": "1",
    "pages": "5434",
    "pre": false,
    "doi": "10.1038/s41467-025-61330-y",
    "abstract": "Smelling is a human sense, expressing **strong sexual dimorphisms**.<br><br>Key findings:<br>* Loci were located within clusters of olfactory receptors<br>* Two loci were **female-specific**<br><br>Significance threshold: p < 5 × 10<sup>-8</sup>",
    "authors": [
      "Förster F",
      "Emmert D",
      "Horn K"
    ],
    "source_study": ["CHRIS baseline"],
    "pdate": "2025-07-02",
    "ar": "511"
  }
}
