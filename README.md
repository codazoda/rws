# Real Work Score (RWS)

A minimal CPU benchmark that outputs a single score (MB/s) so you know how fast it _zips_.

## Quick start

```bash
curl -fsSL https://rws.joeldare.com | bash
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

## Example Results

I got the following results from this script.

| Machine               | CPU                             | Cores   | RWS    |
|-----------------------|---------------------------------|---------|--------|
| 2024 MacBook Air (M3) | Apple M3 (4.05/2.75 GHz)        | 8 (4/4) | 2452.4 |
| Orange Pi 5 Plus      | ARM Cortex A76/A55 (2.4/1.8GHz) | 8 (4/4) |  625.2 |
| Raspberry Pi 400      | ARM Cortex-A72 (1.8GHz)         | 4       |  172.3 |
| HP t5203 Thin Client  | AMD GX-212JC (1.2GHz)           | 2       |   75.5 |
