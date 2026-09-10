# Protalyze

A web-based protein sequence analysis platform that lets users search, align, and analyse protein families across taxonomic groups. This was built as a university coursework project and ran on a university server during the course. The live version is no longer available, but will be soon.

## What it does

Users enter a protein family and a taxonomic group, and the system fetches sequences from NCBI, runs alignment and motif detection, and generates a range of visual outputs. Results are stored with a unique ID so they can be revisited without re-running the analysis.

**Core features:**
- Get protein sequences from NCBI by protein family and taxonomic group
- Quality filters: exclude partial sequences, fragments, or non-manually curated entries
- Multiple sequence alignment using Clustal Omega
- Motif detection using EMBOSS tools
- Optional statistical and visual analyses
- Export results (sequences, alignments, motif hits, plots)
- Guest mode (session-based, 24h retention) and registered user accounts

**Analysis outputs:**
- Dataset statistics (sequence count, length distribution, GC content)
- Sequence length distribution plot
- Residue conservation plot
- Amino acid composition plot
- Sequence similarity heatmap
- Conserved region plot

## Tech stack

| Layer | Technology |
|---|---|
| Backend | PHP |
| Frontend | HTML, CSS |
| Analysis | Python (Biopython, Matplotlib, NumPy) |
| Database | Relational DB (MySQL/MariaDB) |
| Sequence retrieval | NCBI Entrez |
| Alignment | Clustal Omega |
| Motif detection | EMBOSS |

## Project structure

```
├── index.php               # Search page (protein + taxon input)
├── seq.php                 # Sequence retrieval and storage
├── align.php               # Alignment results
├── motif.php               # Motif scanning results
├── analysis.php            # Optional analysis selector
├── plot.php                # Plot rendering endpoint
├── previous.php            # Saved analyses browser
├── export.php              # Download results
├── download.php            # File download handler
├── read.php                # Sequence viewer
├── dash.php                # User dashboard
├── db.php                  # Database connection
├── analysis_functions.php  # Core analysis logic
├── menu.php                # Navigation
├── header.php              # Page header
├── styles.php              # CSS styles
├── loginu.php              # Login
├── logout.php              # Logout
├── about.php               # System description
├── help.php                # Help page
├── credits.php             # Credits
├── contact.php             # Contact page
├── populate_example.php    # Loads example dataset
├── stats_biopython.py      # Sequence statistics
├── plot_lengths.py         # Length distribution plot
├── plot_conservation.py    # Conservation plot
├── plot_aa_comp.py         # Amino acid composition plot
├── plot_heatmap.py         # Similarity heatmap
├── plot_conserved_regions.py # Conserved region plot
├── example_sequences.fasta # Example input sequences
├── example_alignment.fasta # Example alignment output
├── example_motifs.txt      # Example motif results
└── plogo.png               # Logo
```

## Running locally

**Requirements:**
- PHP 8+
- Python 3 with Biopython, Matplotlib, NumPy
- Clustal Omega (`clustalo` on PATH)
- EMBOSS suite (`patmatmotifs` on PATH)
- MySQL or MariaDB

**Setup:**
1. Clone the repo and place it in your web server's root (e.g. `htdocs` or `www`)
2. Create a database and import the schema
3. Update `db.php` with your database credentials
4. Make sure `clustalo` and `patmatmotifs` are installed and accessible
5. Navigate to `index.php` in your browser

To try it out without setting anything up, use the built-in example dataset on the search page (Glucose-6-Phosphatase, Aves).

## Example dataset

An example dataset is included for Glucose-6-Phosphatase in Aves. Click "Use Example Dataset" on the search page to load it directly.
