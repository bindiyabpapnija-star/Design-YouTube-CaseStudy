# Design YouTube: Case Study

A system-design case study for a YouTube-style video platform.

## Contents

| File | Description |
| --- | --- |
| [Capacity_estimation.md](Capacity_estimation.md) | Back-of-the-envelope storage and bandwidth estimates |

## Capacity estimation at a glance

Assumptions: 500 hours of video uploaded per minute, 5-minute average video, 6 MB per minute stored, 10 MB per minute streamed, upload-to-view ratio 1:300. Decimal units, average load.

| Estimate | Result |
| --- | --- |
| Storage | 180 GB/min, about 94.6 PB/year (before replication) |
| Upload bandwidth | about 480 Gbps |
| Streaming bandwidth | about 12 Tbps (average) |

Streaming is about 25x upload, so egress and CDN capacity drive the design.
