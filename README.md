# PT XYZ — Fleet Selection Decision Support System (AHP-TOPSIS)

A web-based Decision Support System (DSS) that helps **PT XYZ**, a logistics company based in Manado, North Sulawesi, Indonesia, select the optimal Light Duty Truck for fleet ownership using an integrated **AHP-TOPSIS** methodology.

Built with Laravel + MySQL as a Multi-Criteria Decision Making (MCDM) final project at Universitas Kristen Petra.

> **Note:** "PT XYZ" is an anonymized stand-in for the real client, used for public portfolio purposes. The city (Manado) and all analysis/data reflect the actual project.

## Background

PT XYZ serves Indomaret and Alfamidi distribution routes across North Sulawesi, Gorontalo, and North Maluku — terrain dominated by narrow, hilly roads. The company currently leases all 12 of its trucks and is evaluating a transition to fleet ownership. Choosing the right truck involves trade-offs between purchase price, fuel efficiency, payload capacity, and spare parts availability — criteria that often conflict with each other.

This system applies a structured, two-stage MCDM approach:

- **AHP (Analytic Hierarchy Process)** — derives objective criteria weights from the owner's expert judgment via pairwise comparison, validated through a Consistency Ratio (CR) check.
- **TOPSIS (Technique for Order Preference by Similarity to Ideal Solution)** — ranks truck alternatives based on their distance to the ideal best and worst solutions, using the weights from AHP.

## Criteria

| Code | Criterion | Type | Unit |
|------|-----------|------|------|
| C1 | Purchase Price | Cost | Million IDR |
| C2 | Fuel Efficiency | Benefit | km/L |
| C3 | Payload Capacity | Benefit | Ton |
| C4 | Spare Parts Availability | Benefit | Score (1–10) |

**AHP-derived weights** (CR = 0.0326, consistent): Payload Capacity (56.6%) > Fuel Efficiency (27.4%) > Spare Parts Availability (11.3%) > Purchase Price (4.6%) — reflecting the owner's priority on operational performance over upfront cost.

## Result

Out of 10 evaluated Light Duty Truck alternatives, **Isuzu Elf NMR 71** ranked first (V = 0.8931), driven by its combination of best-in-class fuel efficiency (12 km/L) and highest payload capacity (8.25 ton) — the two highest-weighted criteria.

| Rank | Alternative | Score (V) |
|------|-------------|-----------|
| 1 | Isuzu Elf NMR 71 | 0.8931 |
| 2 | Isuzu Elf NMR 71 L (Long Chassis) | 0.7979 |
| 3 | Hino Dutro 136 HD | 0.6848 |

Full calculation breakdown, decision matrix, and analysis available in [`docs/`](./docs).

## Features

- Dashboard with current recommendation and quick stats
- Alternative (truck) management — add, edit, delete
- TOPSIS results page showing decision matrix, normalized matrix, weighted matrix, ideal solutions, and final ranking

## Tech Stack

- Laravel (PHP)
- MySQL (via Docker)
- Blade templates

## Getting Started

```bash
git clone https://github.com/leonardjust14/ahp-topsis-truck-fleet-selection.git
cd ahp-topsis-truck-fleet-selection
docker-compose up -d
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate --seed
php artisan serve
```

Visit `http://localhost:8000`.

## Project Team

Final project for Multiple Criteria Decision Making (MCDM), Information Systems Business, Universitas Kristen Petra (2026).

| Name | Role |
|------|------|
| **Leonard Caesar Justin** (Leo) | Field context & analysis — problem identification, criteria definition (payload, fuel efficiency, price, spare parts availability), owner interviews/questionnaires for AHP pairwise comparison judgments, and end-to-end AHP-TOPSIS implementation (raw data → consistency check → final ranking) |
| **John Dave Limanto** | Frontend & backend development (Laravel) |
| **Rayner Orville Wijaya** | Frontend & backend development (Laravel) |
| **Ariel Andhika Dumais** | Frontend & backend development (Laravel) |