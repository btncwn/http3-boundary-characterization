# Claim matrix

The canonical wording and bibliography are in `../paper/main.tex`. This note is a source-inspection crosswalk, not an empirical dataset or a product-security rating.

A = delivered-byte accounting; C = completion validation; F = HTTP/1 body framing; R = backend reuse. S = supported local property at the named path; P = partial evidence; O = open or uninspected. Even four S entries are not an exhaustive proof of end-to-end security.

| Case | A | C | F | R | Conditions and ceiling |
|---|---|---|---|---|---|
| HAProxy remediation changes | O | S (fix) | O | P (fix) | Two public changes at distinct commits; not one fully traced deployment. No independence claim. |
| nginx | S | S | S | O | Native H3 request-body path and standard HTTP proxy body writer; ordinary buffered case. Arbitrary modules, changed buffering, and reuse/error interleavings are not established. |
| Envoy/QUICHE | S | S | O | O | Post-remediation Envoy consumer; headers-only conclusion requires `envoy.reloadable_features.quic_validate_headers_only_content_length` enabled. Not a QUICHE-wide result. |
| Caddy/quic-go | O | O | O | O | No qualifying body-desynchronization result. Later upgraded-stream correctness patch is a different question. |
| nghttp3/ngtcp2 through nghttpx | S | S | S | S | Named library callbacks, nghttpx writer and detach predicate only; no transfer to arbitrary library consumers. |
| Apache Traffic Server | S | O | O | O | Actual delivered DATA bytes at the pinned adaptor only. FIN disposition, aggregate body validation, H1 forwarding and pooling are unresolved. |

## Inspected links and stopping points

### HAProxy

- `86a4ebc761a278838e8cb06f3a292282ba704c65`: frame-completeness checks in `src/h3.c`, including FIN/EOM and DATA-loop handling.
- `4721a96f161b83cbb5015d15821e84e16fe21151`: separate short-message hardening in `src/mux_h1.c`.
- These support complementary remediation statements. They do not establish a pre-existing independent defense on the affected path. This paper does not reconstruct all four obligations in one built release tree.
- Stable fixed-version statements use the official 3.3 and 3.4 changelogs; the public CVE record supplies the affected ranges and development-version boundary.

### nginx

At `ef0aa967dce9d30b824d4c839d3579d2a17e0666`:

- `ngx_http_v3_parse_data`: declaration retained as parser state.
- `ngx_http_v3_request_body_filter`: copied amount bounded by available bytes and remaining payload; completion rejects leftover frame bytes and declared-length mismatch.
- Standard `ngx_http_proxy_body_output_filter`: chunk size from actual buffer contents; terminal chunk from the final-buffer marker.
- No complete pool/reuse trace or exhaustive alternate-module/configuration search is supplied. The source version is 1.31.7 development, not a claim about a shipped 1.31.7 binary.

### Envoy/QUICHE

At Envoy `bfd41cd54d81cad5975b0443ab9c59543f1bbe18`:

- `OnInitialHeadersComplete` invokes zero-byte end-stream accounting before decoding completed headers under the named guard.
- `updateReceivedContentBytes` checks aggregate length at end-stream; `OnBodyAvailable` accounts delivered data separately.
- Guard registration is default-on but operator-disableable. Disabled-guard configurations are outside the favorable headers-only conclusion.
- No H1 serializer or connection-pool proof follows from these predicates. QUICHE `5c9cc6b37f55a97071077a6190bf4f0bc7a09c1f` is the dependency identity, not a library-wide safety certificate.

### Caddy/quic-go

The baseline identity is Caddy v2.11.4 at `e2eee6a7fce366321294c9c2a79f3146891dcbdf`. No wire-equivalence, same-connection victim-safety, or body-containment claim is made. The accepted PR #8027 squash `9be8fb279444ec633ae2eea4590a180e1143c8f6` is later and is not present in that baseline. It addresses upgraded-stream half-close behavior, not the open H3 body question.

### nghttp3/ngtcp2 through nghttpx

- nghttp3 `2304973e5a0c8b1fa4bb380b47945a000357f87f`: DATA callbacks receive the available payload span; incomplete-frame end input is rejected; request `MSG_END` invokes content-length validation before clean completion.
- nghttpx `140157a8d751e9e8b0cc15bf9bc0e2ee0c1ed987`: H3 callbacks forward that span; the HTTP downstream writer sizes chunks from actual input; clean end-stream performs end-of-upload.
- `Downstream::can_detach_downstream_connection` requires complete request and response states and drained request buffers, with further upgrade/close restrictions. The close path consults the predicate before pooling.
- ngtcp2 `3c23148ef32596cb75720b94615d9650cdec5391` records transport provenance. The consumer conclusions do not transfer to `mod_http3` or other integrations.

### Apache Traffic Server

At `ca133303832de2cb0c1d5b2ea38c9d2cc5d53820`, an 11.0.0 development tree:

- `Http3DataFrame::_parse` establishes complete-frame readiness; `Http3FrameDispatcher` bounds the reader and consumes available bytes.
- `Http3StreamDataVIOAdaptor::handle_frame` transfers actual bytes; `finalize` records completed delivery.
- This addresses only early credit in the local DATA path. Neither exact FIN disposition nor full H1 re-framing/reuse is established. No vulnerability inference is made from that gap.
- The 9.2.15/10.1.4 and 9.2.13/10.1.2 HTTP/1 advisory floors refer to distinct issues; neither closes the H3 gaps.

## Excluded evidence

Unretained historical observations and instrument-error runs are non-results. They contribute no response counts, timing data, framing verdict, or confidence increment. Upstream correctness tests are cited as existing upstream artifacts, not newly executed results. There was no new dynamic test or source-wide exhaustive search for this manuscript preparation.
