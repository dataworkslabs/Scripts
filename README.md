# Screenplay Structure Analysis

An exploratory data analysis of fourteen screenplays — eleven 
critically acclaimed films and three lower-rated comparison films. 
The central question: do great screenplays share a common structure, 
or only a common structural discipline?

## Films Analyzed

**Acclaimed**
| Title | Writer(s) | Year |
|-------|-----------|------|
| Ikiru | Hashimoto, Kurosawa, Oguni | 1952 |
| Thelma & Louise | Callie Khouri | 1991 |
| Boogie Nights | Paul Thomas Anderson | 1997 |
| Eyes Wide Shut | Stanley Kubrick | 1999 |
| Moonlight | Barry Jenkins | 2016 |
| Get Out | Jordan Peele | 2017 |
| Parasite | Bong Joon-ho & Han Jin-won | 2019 |
| Portrait of a Lady on Fire | Céline Sciamma | 2019 |
| Aftersun | Charlotte Wells | 2022 |
| Sentimental Value | Joachim Trier & Eskil Vogt | 2025 |
| Sinners | Ryan Coogler | 2025 |

**Comparison**
| Title | Writer(s) | Year | RT Score |
|-------|-----------|------|----------|
| The Mummy | Koepp, McQuarrie, Kussman | 2017 | 24% |
| Amsterdam | David O. Russell | 2022 | 33% |
| Don't Worry Darling | Katie Silberman | 2022 | 38% |

## Project Structure
```
├── data/
│   ├── screenplays/               ← PDF screenplay files
│   ├── screenplays.html           ← Metadata table (hand-built)
│   ├── screenplays.json           ← Metadata (hand-built)
│   └── script_structure_dataset.csv  ← Hand-coded story beat sheet
├── Project_2.Rmd                  ← Full analysis
├── Project_2_Approach.Rmd         ← Approach document
└── README.md
```

## Datasets

**Metadata** — title, writers, year, genre, runtime, page count, 
Rotten Tomatoes score, and original vs. adapted. Built by hand in 
both HTML and JSON, loaded and compared in R.

**Story beat sheet** — six structural moments coded by hand for each 
screenplay: inciting incident, Act I break, midpoint, Act II break, 
climax, and resolution. All positions recorded as page numbers and 
converted to percentages of total script length for cross-film 
comparison.

**PDF extraction** — dialogue exchange frequency and average lines per 
page extracted programmatically using pdftools and stringr. Four films 
were excluded from extraction-based metrics due to scanned PDFs with 
no extractable text.

## Visualizations

- Estimated act structure with act break positions
- Beat interval heatmap — where each screenplay spends its pages
- Climax to resolution length — post-climax runway by film

## Key Finding

Structural timing alone does not explain quality. The comparison films 
hit broadly similar structural marks to the acclaimed films. What 
appears to differ is harder to quantify — the purposefulness of what 
happens between those marks. Great scripts in this sample share 
structural discipline more than structural uniformity.

## Tools

- **R / RStudio** — data loading, cleaning, extraction, analysis
- **ggplot2** — all visualizations
- **Quarto** — final report, published to RPubs

## Packages
```r
pdftools     # PDF text extraction
stringr      # string parsing
rvest        # loading HTML
jsonlite     # loading JSON
tidyr        # reshaping
dplyr        # data manipulation
ggplot2      # visualization
readr        # CSV loading
purrr        # functional tools
```

## Notes

Ikiru appears in the metadata and act structure analysis but is 
omitted from the beat interval heatmap and ending compression chart 
due to an unresolved Act II break that could not be coded with 
confidence. Four screenplays — Boogie Nights, Portrait of a Lady on 
Fire, Thelma & Louise, and one additional title — had PDF scan issues 
that made text extraction unreliable. Those values are recorded as NA 
and noted where relevant.
