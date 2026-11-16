• Assumptions:
1) 500 hours of video uploaded per minute
2) 5-minute average video
3) 120 MB per minute raw (uploaded)
4) 6 MB per minute stored (compressed)
5) 10 MB per minute streamed
6) Upload-to-view ratio 1:300
7) Decimal units (1 GB = 1,000 MB); average load, not peak

• Storage Estimation:
Video uploaded per minute = 500 hr × 60 = 30,000 video-min/min
Storage per minute = 30,000 video-min/min × 6 MB/min = 180 GB/min
Storage per year = 180 GB × 60 × 24 × 365 ≈ 94.6 PB/year (before replication)

• Bandwidth Estimation:
Bandwidth = video-minutes per minute × MB per video-minute (× view ratio for streaming)

Upload bandwidth = 30,000 video-min/min × 120 MB/min = 3.6 TB/min = 60 GB/s ≈ 480 Gbps

Streaming bandwidth = 30,000 video-min/min × 10 MB/min × 300 views = 90 TB/min = 1.5 TB/s ≈ 12 Tbps (average)

• Takeaway:
Streaming (12 Tbps) is about 25× upload (0.48 Tbps), so egress and CDN capacity drive the design.
