#!/usr/bin/env bash
#
# Real Work Score (RWS)
#
# A tiny CPU+memory throughput benchmark for quick, comparable numbers.
# It streams zeroes through gzip and reports MB/s so you can compare machines
# or verify performance changes.
#
# Quick start (no args = all cores, 1024 MB):
#   curl -s https://rws.joeldare.com | bash
#
# Other Examples:
#   curl -s https://rws.joeldare.com | bash -s -- --single
#   curl -s https://rws.joeldare.com | bash -s -- --multi --cores 4
#   curl -s https://rws.joeldare.com | bash -s -- --list-cpus
#
# Flags:
#   --single          run one stream (single-core)
#   --multi           run one stream per core
#   --mb N            total MB to process (default 1024)
#   --cores N         number of cores for --multi
#   --cpus LIST       explicit CPU list (reserved for future use)
#   --pin CPU         pin to a specific CPU (reserved for future use)
#   -q, --quiet       suppress non-score output (if any)

set -euo pipefail

MB=1024
MODE=""
CORES=""
PIN=""
CPUS=""
QUIET=0
LIST_CPUS=0

usage() {
  cat <<'EOF'
Usage:
  real-work-score --list-cpus
  real-work-score --single [--mb 1024] [--pin CPU] [-q]
  real-work-score --multi  [--mb 1024] [--cores N | --cpus LIST] [-q]
EOF
}

have() { command -v "$1" >/dev/null 2>&1; }
default_cores() { getconf _NPROCESSORS_ONLN 2>/dev/null || nproc 2>/dev/null || echo 1; }
now_ns() { date +%s%N; }
score_from_elapsed() {
  awk -v mb="$MB" -v ns="$1" 'BEGIN{printf "%.1f\n", mb/(ns/1e9)}'
}

expand_cpu_list() {
  local IFS=',' part
  for part in $1; do
    [[ "$part" =~ ^[0-9]+-[0-9]+$ ]] && seq ${part%-*} ${part#*-} || echo "$part"
  done
}

list_cpus() {
  command -v lscpu >/dev/null && lscpu -e || echo "lscpu not available"
}

while [[ $# -gt 0 ]]; do
  case "$1" in
    --list-cpus) LIST_CPUS=1; shift ;;
    --single) MODE="single"; shift ;;
    --multi) MODE="multi"; shift ;;
    --mb) MB="$2"; shift 2 ;;
    --cores) CORES="$2"; shift 2 ;;
    --pin) PIN="$2"; shift 2 ;;
    --cpus) CPUS="$2"; shift 2 ;;
    -q|--quiet) QUIET=1; shift ;;
    *) usage; exit 1 ;;
  esac
done

(( LIST_CPUS )) && { list_cpus; exit 0; }

if [[ -z "$MODE" ]]; then
  MODE="multi"
fi

run_pipeline() {
  dd if=/dev/zero bs=1M count="$1" 2>/dev/null | gzip -9 >/dev/null
}

if [[ "$MODE" == "single" ]]; then
  s=$(now_ns)
  run_pipeline "$MB"
  e=$(now_ns)
  score_from_elapsed $((e-s))
  exit 0
fi

CORES="${CORES:-$(default_cores)}"
base=$((MB/CORES)); rem=$((MB%CORES))
s=$(now_ns)
for i in $(seq 1 "$CORES"); do
  c="$base"; ((i<=rem)) && c=$((c+1))
  run_pipeline "$c" &
done
wait
e=$(now_ns)
score_from_elapsed $((e-s))
