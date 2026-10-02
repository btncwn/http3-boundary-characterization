# Immutable source identities

This inventory is mechanically derived from the canonical manuscript appendix. A commit identifies source, not a tested binary. Development snapshots, fixes, backports, and release identities have distinct roles. Exact file/function anchors are in the manuscript bibliography and the accompanying claim matrix.

| Component / purpose | Full identity and qualification |
|---|---|
| HAProxy H3 completeness | [86a4ebc761a278838e8cb06f3a292282ba704c65](https://github.com/haproxy/haproxy/commit/86a4ebc761a278838e8cb06f3a292282ba704c65); code fix in `src/h3.c`. |
| HAProxy H1 reuse hardening | [4721a96f161b83cbb5015d15821e84e16fe21151](https://github.com/haproxy/haproxy/commit/4721a96f161b83cbb5015d15821e84e16fe21151); separate code fix in `src/mux_h1.c`. |
| nginx source snapshot | [ef0aa967dce9d30b824d4c839d3579d2a17e0666](https://github.com/nginx/nginx/commit/ef0aa967dce9d30b824d4c839d3579d2a17e0666); source version 1.31.7, development snapshot. |
| Envoy source snapshot | [bfd41cd54d81cad5975b0443ab9c59543f1bbe18](https://github.com/envoyproxy/envoy/tree/bfd41cd54d81cad5975b0443ab9c59543f1bbe18); 1.40.0-dev. |
| QUICHE dependency | [5c9cc6b37f55a97071077a6190bf4f0bc7a09c1f](https://github.com/google/quiche/tree/5c9cc6b37f55a97071077a6190bf4f0bc7a09c1f); Envoy dependency; conclusions remain consumer-specific. |
| Envoy headers-only repair | [59c7458d4dc48705d4f7b74f8a92912b5ca79822](https://github.com/envoyproxy/envoy/commit/59c7458d4dc48705d4f7b74f8a92912b5ca79822); runtime-guarded code fix. |
| Caddy baseline | [e2eee6a7fce366321294c9c2a79f3146891dcbdf](https://github.com/caddyserver/caddy/tree/e2eee6a7fce366321294c9c2a79f3146891dcbdf); v2.11.4, body question open. |
| nghttp3 | [2304973e5a0c8b1fa4bb380b47945a000357f87f](https://github.com/ngtcp2/nghttp3/tree/2304973e5a0c8b1fa4bb380b47945a000357f87f); development snapshot. |
| ngtcp2 | [3c23148ef32596cb75720b94615d9650cdec5391](https://github.com/ngtcp2/ngtcp2/tree/3c23148ef32596cb75720b94615d9650cdec5391); transport provenance. |
| nghttp2 / nghttpx | [140157a8d751e9e8b0cc15bf9bc0e2ee0c1ed987](https://github.com/nghttp2/nghttp2/tree/140157a8d751e9e8b0cc15bf9bc0e2ee0c1ed987); frontend source snapshot. |
| ATS H3 inspection | [ca133303832de2cb0c1d5b2ea38c9d2cc5d53820](https://github.com/apache/trafficserver/tree/ca133303832de2cb0c1d5b2ea38c9d2cc5d53820); development tree, experimental H3. |
| ATS CVE-2026-24033 code fixes | 10.1.x: [bb7f7263dff737c2c895dbb225b5415f93b804d1](https://github.com/apache/trafficserver/commit/bb7f7263dff737c2c895dbb225b5415f93b804d1). 9.2.x backport: [e44213f8ec0d1df65de99a15fe2f59c16e01f30b](https://github.com/apache/trafficserver/commit/e44213f8ec0d1df65de99a15fe2f59c16e01f30b). |
| ATS CVE-2025-65114 code fixes | 10.1.x: [7c2c689e5843a3be70b775600b125a2957422209](https://github.com/apache/trafficserver/commit/7c2c689e5843a3be70b775600b125a2957422209). 9.2.x backport: [e5accd7929c5cb96a01cc9afda1f6336dab59b64](https://github.com/apache/trafficserver/commit/e5accd7929c5cb96a01cc9afda1f6336dab59b64). |
| ATS release identities | 10.1.4: [f8be6725daee427fbf88f166f14b10cb5525b220](https://github.com/apache/trafficserver/commit/f8be6725daee427fbf88f166f14b10cb5525b220); 9.2.15: [f671e525110be50452f607fc1f2657f3dba7fe3b](https://github.com/apache/trafficserver/commit/f671e525110be50452f607fc1f2657f3dba7fe3b). 10.1.2: [fd932cb399f0b18d1044700d34bc028edabcb82d](https://github.com/apache/trafficserver/commit/fd932cb399f0b18d1044700d34bc028edabcb82d); 9.2.13: [2c83b07b60ec73e4aa48abc10e82b248e3f2a23b](https://github.com/apache/trafficserver/commit/2c83b07b60ec73e4aa48abc10e82b248e3f2a23b). These are not the code fixes above. |
| HAProxy correctness contribution | [4ddf219bb399334e00a0b9af2b155884befd4b04](https://github.com/haproxy/haproxy/commit/4ddf219bb399334e00a0b9af2b155884befd4b04); response validation, `BUG/MINOR`. |
| Caddy correctness contribution | [9be8fb279444ec633ae2eea4590a180e1143c8f6](https://github.com/caddyserver/caddy/commit/9be8fb279444ec633ae2eea4590a180e1143c8f6); accepted squash merge for PR #8027. |

The final Caddy PR branch head `2ec7211b42e2bff1c32741b6e271a92bc2da690a` is a base-branch merge, not the author’s accepted feature pin. The squash merge listed above is the contribution identity. The Caddy body path is open, and no quic-go-wide conclusion is claimed.

