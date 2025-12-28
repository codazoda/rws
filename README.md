# Real Work Score (RWS)

A minimal Linux CPU benchmark that outputs a single score (MB/s) using gzip.

## Quick start

```bash
url -fsSL https://rws.joeldare.com | bash
```

## Why this exists

- I have a mix of low-power machines (Pi Zero, thin clients, old minis) and I
  needed a tiny, copy-paste benchmark that produces one comparable number.
- The goal is fast, repeatable sizing for rough workload decisions, not a deep
  or comprehensive benchmark.

## More information

See the script itself for additional flags and more information.

## Building

Because this is served from GitHub pages we need the script to be copied to index.html, which GitHub will serve as text/plain. I've added a git alias to accomplish this. To build the project run the following command and then add, commit, and push the files.

```bash
git build
```
