# v1.1.3 — Validated Damage Model

This release strengthens the existing damage model with verified native Combatives inputs, expanded move coverage, and additional gameplay validation.

## Major changes

- Integrated freshly extracted native Combatives `Power` verification into the calculation path.
- Confirmed all **1,353 Power terms** already used by the model against the game data.
- Verified character DP damage scaling and attack class/type modifiers in the native baseline calculation.
- Validated additive attack buffs and low-health modifiers with the Bardock controls.
- Validated Super Boost and Sparking interactions across the reported Bardock states.
- Added explicit **Mode default / On / Off** matchup DP controls, including in Training.
- Added five separately rounded source applications for the shared beam, using the existing float32 arithmetic and per-application ceiling behavior.
- Expanded native calculation coverage across the playable roster, including **59 Super 1 source bindings** sharing the validated projectile definition.
- Improved shared projectile and move-source mapping.
- Preserved blank Power values as unknown instead of converting them to zero.
- Separated source-backed calculations, manual observations, retained references, and unresolved cases.

## Validation

- **71,345 extracted rows** audited across **241 playable characters/forms**
- **1,353 / 1,353** existing Combatives Power terms matched
- **16 / 16 Bardock validation totals** reproduced exactly
- **8,170 automated regression checks passed**

Revenger Blaster testing confirmed five separately rounded **1,140-Power applications** for its shared projectile, rather than rounding only after the final total is assembled. Fangs of Fury reproduced **16,310** and **18,640** through its existing **6,700-Power aggregate** calculation.

## Result

The calculator derives supported damage results from native source values and validated rules. Older imported totals remain comparison evidence and fallbacks for incomplete mappings.
