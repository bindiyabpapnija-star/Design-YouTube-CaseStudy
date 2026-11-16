# Design YouTube: Capacity Estimation

Back-of-the-envelope storage and bandwidth estimates for a YouTube-scale video platform.

## Assumptions

| # | Assumption | Value |
| --- | --- | --- |
| 1 | Video uploaded | 500 hours per minute |
| 2 | Average video length | 5 minutes |
| 3 | Raw size (uploaded) | 120 MB per video-minute |
| 4 | Stored size (compressed) | 6 MB per video-minute |
| 5 | Streamed size | 10 MB per video-minute |
| 6 | Upload-to-view ratio | 1 : 300 |
| 7 | Units and load | Decimal (1 GB = 1,000 MB); average load, not peak |

## Storage

```text
Video uploaded per minute = 500 hr × 60        = 30,000 video-min/min
Storage per minute        = 30,000 × 6 MB      = 180 GB/min
Storage per year          = 180 GB × 60 × 24 × 365
                          ≈ 94.6 PB/year (before replication)
```

## Bandwidth

General formula:

```text
Bandwidth = video-minutes per minute × MB per video-minute  (× view ratio for streaming)
```

**Upload (ingress)**

```text
30,000 video-min/min × 120 MB/min = 3.6 TB/min = 60 GB/s ≈ 480 Gbps
```

**Streaming (egress)**

```text
30,000 video-min/min × 10 MB/min × 300 views = 90 TB/min = 1.5 TB/s ≈ 12 Tbps (average)
```

## Summary

| Estimate | Result |
| --- | --- |
| Storage per minute | 180 GB/min |
| Storage per year | ≈ 94.6 PB/year (before replication) |
| Upload bandwidth | ≈ 480 Gbps (0.48 Tbps) |
| Streaming bandwidth | ≈ 12 Tbps (average) |

## Takeaway

> Streaming (12 Tbps) is about **25× upload** (0.48 Tbps), so egress and CDN capacity drive the design.
