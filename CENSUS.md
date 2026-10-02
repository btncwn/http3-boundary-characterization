# Distribution census

This distribution contains 18 regular files in three directories (the root, `paper/`, and `evidence/`). There are no symlinks or hidden files. The local distribution is owned by Turhan Acar; directory modes are `0555` and file modes are `0444`. A hosting service or extraction tool may represent permissions differently.

The eight payload files are:

1. `README.md`
2. `CITATION.cff`
3. `LICENSE`
4. `CENSUS.md`
5. `paper/main.pdf`
6. `paper/main.tex`
7. `evidence/claim-matrix.md`
8. `evidence/source-pins.md`

Each payload has one adjacent `.sha256` sidecar, giving eight more files. Each sidecar contains one SHA-256 digest and its adjacent file's bare basename.

`EXACT-SET.sha256` contains the 16 root-relative entries for those eight payloads and eight sidecars. Its own adjacent `EXACT-SET.sha256.sha256` is the eighteenth file. Neither manifest file is listed inside the manifest, avoiding self-reference. No other file is part of this distribution.

All manuscript source, PDF, evidence notes, and license content are supplied as complete files. This package requires no external local directory to read its contents. The bibliography links to public upstream sources for source inspection. No dynamic dataset or reproduction harness is included.

The checksum set describes file integrity, not academic peer review or publication status. Creating or copying this distribution does not publish a GitHub repository or a Zenodo record.
