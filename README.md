# Real Work Score (RWS)

A minimal Linux CPU benchmark that outputs a single score (MB/s) using gzip.

Why this exists:
- I have a mix of low-power machines (Pi Zero, thin clients, old minis) and I
  needed a tiny, copy-paste benchmark that produces one comparable number.
- The goal is fast, repeatable sizing for rough workload decisions, not a deep
  or comprehensive benchmark.

Quick start (no args = all cores, 1024 MB):
curl -fsSL https://rws.joeldare.com | bash

Other examples:
curl -fsSL https://rws.joeldare.com | bash -s -- --single
curl -fsSL https://rws.joeldare.com | bash -s -- --multi
