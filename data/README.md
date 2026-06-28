# Data (local only — not committed)

The dataset is **not** stored in this repo (too large for GitHub, and `.gitignore`
excludes it). Download it here on your own machine.

## Dataset: CIC-IDS2017 (primary candidate)
- Source: Canadian Institute for Cybersecurity (search "CIC-IDS2017").
- Use the **pre-extracted CSV feature files** (a few GB), NOT the raw PCAP (~200GB+).
- Place the CSVs in this `data/` folder after downloading.

## Alternative: UNSW-NB15 (smaller, also fine)
- Source: UNSW Canberra. Comes as labelled CSV feature sets.

## Why it's not in git
GitHub rejects files > 100MB and these datasets are multiple GB. Keeping data out of
version control is standard practice; this README + the loader code make the work fully
reproducible without storing the files.
