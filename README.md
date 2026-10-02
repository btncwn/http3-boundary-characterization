# HTTP/3-to-HTTP/1.1 Boundary Handling

## A Source-Led Characterization of Six Open-Source Stacks

**Author:** Turhan Acar  
**Manuscript date:** 2 October 2026  
**Status:** Research preprint; not peer reviewed.  
**License:** [CC BY 4.0](LICENSE.txt)

[Read the paper (PDF)](paper/main.pdf) · [LaTeX source](paper/main.tex) · [Claim matrix](evidence/claim-matrix.md) · [Source identities](evidence/source-pins.md)

## About this study

HTTP/3 front ends forwarding requests to HTTP/1.1 origins must reconcile body-byte accounting, stream completion, downstream framing, and backend connection reuse. This paper maps those four obligations at specified source revisions across six illustrative cases: HAProxy, nginx, Envoy/QUICHE, Caddy/quic-go, nghttp3/ngtcp2 through nghttpx, and Apache Traffic Server.

The contribution is a bounded, inspectable comparison of named source paths and explicit evidence gaps. The accompanying matrix distinguishes supported local properties, partial evidence, and open paths. These are evidence states, not product-security ratings.

## Scope and limitations

- No new vulnerability, dynamic experiment, or implementation-wide assurance is claimed.
- The sample is illustrative, not a systematic or representative survey of all HTTP/3 implementations.
- Source conclusions apply only to the named revisions, paths, and conditions; they do not automatically transfer to other releases or library consumers.
- An open path is an evidence gap, not a finding of vulnerability or safety. The Caddy body-framing question remains open.
- The HAProxy and Caddy engineering contributions discussed in the appendix are separate correctness artifacts, not proof of the central body-framing claims.
- No attack payload, stimulus generator, operational exploit instructions, or dynamic reproduction harness is included.

For exact qualifications and references, use the paper. The evidence notes are reading aids, not an empirical dataset.

## Citation and archive

Repository: <https://github.com/btncwn/http3-boundary-characterization>

Archive DOI: [10.5281/zenodo.23110774](https://doi.org/10.5281/zenodo.23110774)

The DOI has been reserved for the Zenodo record. It becomes registered when that record is published; reserving an identifier does not itself establish publication or peer review. Until it resolves, use the repository and the supplied PDF. Machine-readable manuscript citation metadata is provided in [CITATION.cff](CITATION.cff), using its `preferred-citation` entry.

## Files and integrity

- `paper/main.pdf`: the supplied manuscript PDF.
- `paper/main.tex`: self-contained LaTeX source, including the bibliography.
- `evidence/claim-matrix.md`: claim boundaries and inspected links.
- `evidence/source-pins.md`: full source commit identities and qualifications.
- `CENSUS.md`: the complete distribution file list and count.
- `EXACT-SET.sha256`: checksums for the distribution payload and adjacent sidecars.

The SHA-256 identities of the supplied manuscript files are:

```text
3fe64984464b337dbaa8cfaddeb0e89a91c961a6f09ad78cac44913f0a49ce49  paper/main.tex
692a50e448220914cceee9d957668dc81581d1ec9799abdb1abbdb3e75f0d845  paper/main.pdf
```

From the extracted distribution directory, verify the manifest and its listed members:

```sh
shasum -a 256 -c EXACT-SET.sha256.sha256
shasum -a 256 -c EXACT-SET.sha256
```

Checksums detect changes against this distribution; they are not a digital signature, proof of scientific correctness, or independent acceptance. `CENSUS.md` also lists the expected files, because checksum verification alone does not reject extra files. A separately rebuilt PDF may have different bytes; use the supplied PDF when referring to this exact version.

## Assistance and responsibility

Anthropic Claude and OpenAI Codex substantially assisted source navigation, cross-checking, drafting, and document preparation, as disclosed in the paper. Turhan Acar directed the work and is responsible for its claims, citations, and publication decision. AI-assisted checks do not constitute independent academic peer review. No AI system is an author.

## License and feedback

The original manuscript and accompanying original documentation are licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Linked upstream code, standards, papers, and advisories retain their own licenses; this repository does not relicense them.

Corrections to this paper are welcome through the repository's Issues tab, if enabled. Please identify the section, source revision, and supporting public reference. Do not post unpublished vulnerability details here; use the relevant project's security-reporting process instead.
