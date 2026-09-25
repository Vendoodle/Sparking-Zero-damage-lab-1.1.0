# Sparking! ZERO Community Damage Lab

A source-backed damage calculator and combat-data reference for **Dragon Ball: Sparking! ZERO**.

Built against game build **24953175** and covering all **241 playable characters/forms**.

## What it does

- Calculates damage from native game values instead of relying only on imported totals.
- Uses extracted Combatives `Power` values and character-specific damage scaling.
- Supports character/class modifiers, buffs, low-health effects, Sparking, Super Boost, resistances, armor, charge scaling, target modifiers, and optional DP matchup scaling where the move's source path is mapped.
- Uses float32 arithmetic and per-source-application rounding for supported damage paths.
- Preserves unresolved or unmapped data instead of guessing.
- Includes character, move, costume, passive, transformation, and provenance/reference information.

## Damage model

```text
D = Σ ceil(P_i × A × B × H_i × C × I × max(0, 1 − r) × Q × G)

A = DPDamageScale + AttackTypeScale + Σ additive attack buffs

G = 1 + 0.035 × (attacker DP − defender DP)   [DP scaling on]
G = 1                                        [DP scaling off]
```

This is the standard native damage path. Move-specific rules and source-defined aggregate inputs retain their own handling. `Damage_Formula.txt` in the Windows package provides the compact variable definitions and worked example.

## Download v1.1.3

[Download the Windows x64 package](https://github.com/Vendoodle/Sparking-Zero-damage-lab-1.1.0/releases/download/v1.1.3/SparkingZeroDamageLab-v1.1.3-Windows.zip) or visit the [v1.1.3 release page](https://github.com/Vendoodle/Sparking-Zero-damage-lab-1.1.0/releases/tag/v1.1.3).

Extract the ZIP before running the calculator. SHA-256 checksums are available with the release. This release provides the Windows package; a v1.1.3 Linux package has not been validated.

GitHub's automatic **Source code** archives contain this repository's documentation. Use the Windows package above to get the application.

## Run on Windows

Open `SparkingZeroCalculator.exe`. The portable package includes its runtime and game-data snapshot.

For the Bardock Training controls, set **MATCHUP DP** to **On**. The included CSV files contain the validation results and character coverage sorted by character ID. Run `Generate Reports.cmd` to regenerate the reference and observation comparisons.

See [RELEASE_NOTES.md](RELEASE_NOTES.md) for v1.1.3 changes and validation.
