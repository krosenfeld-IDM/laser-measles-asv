# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an ASV (Airspeed Velocity) benchmarking repository for the laser-measles project. ASV is a Python library for benchmarking Python packages over their lifetime, tracking performance changes across commits.

## Repository Structure

- `asv.conf.json` - Main ASV configuration file defining project settings, benchmarking parameters, and environment setup
- `benchmarks/` - Directory containing benchmark implementations
  - `benchmarks.py` - Example benchmark classes (TimeSuite, MemSuite) showing ASV benchmark patterns
  - `laser_core/` - Directory for laser-core specific benchmarks
  - `laser_measles/` - Directory for laser-measles specific benchmarks

## Key ASV Commands

Run benchmarks for current commit:
```bash
asv run
```

Run benchmarks for specific commits/ranges:
```bash
asv run v1.0..v1.1
```

Generate HTML report:
```bash
asv publish
asv preview
```

Compare performance between commits:
```bash
asv compare <commit1> <commit2>
```

Find performance regressions:
```bash
asv find <commit1> <commit2>
```

## Configuration Details

- Target project: laser-measles (https://github.com/InstituteforDiseaseModeling/laser-measles)
- Environment: virtualenv-based
- Python version: defaults to current Python (3.10+ required per README)
- Benchmarks stored in: `benchmarks/` directory
- Results stored in: `results/` directory (default)
- HTML output: `html/` directory (default)

## Benchmark Development

ASV benchmarks follow specific patterns:
- Time benchmarks: methods prefixed with `time_`
- Memory benchmarks: methods prefixed with `mem_`
- Setup methods: `setup()` and `setup_cache()` for initialization
- Benchmark classes can include setup/teardown methods and parameterization

New laser-measles benchmarks should be added to the `benchmarks/laser_core/` directory.