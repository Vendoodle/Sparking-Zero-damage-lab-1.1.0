# Sparking! ZERO Community Damage Lab — v1.1.1

**This is the finished version of the offline damage calculator and character reference I built for Dragon Ball: Sparking! ZERO.**

v1.1.1 is mostly the result of finally making the information that was already in the project talk to itself properly. The calculator now understands more of the native move data, the Lab is actually useful as a notebook, and the number on screen can explain where it came from instead of living in a separate universe from the research behind it.

The data still targets **game build 24953175** and covers **241 playable fighters and forms**. v1.1.0 is staying up too; this is a new release, not a replacement for the old files.

## What changed

- The calculator no longer demands per-hit data just because a move has an animation with multiple hits. If the game gives us a valid total and the selected mechanic can work from that total, the calculator can use it without inventing fake hit values.
- Normal Throws now use their native move data across the roster where the execution is understood. Several other source-backed named moves and numbered sequences were recovered too.
- Buffs now use the fields they actually modify instead of being treated like generic percentages slapped onto an already-rounded damage number.
- Known source/reference disagreements stay visible instead of being quietly massaged until the numbers look prettier.
- Existing support for costume replacements, DP scaling, armor, extra-Ki, Devilmite/Wickedness and giant cinematic/contact behavior is still here.

One of the checks that finally nailed the Throw path was Tora against Goku (Z - Early):

| **Tora’s state** | **Damage** |
| --- | --- |
| Neither | 1,188 |
| Saiyan Spirit | 1,313 |
| Low health | 1,313 |
| Both | 1,438 |

That sequence matches the reconstructed native path and shows why the calculator should work from the underlying move data rather than multiplying a rounded display number. It is evidence for this interaction, not a claim that every buff in the game behaves the same way.

## The Lab is finally a Lab

- **Manual Tests:** now opens as the actual global lab notebook. You can see the recorded gameplay tests in one place, filter them down to the current matchup, or clear the filter and browse everything. Reconstructed values are not presented as if they were manual observations.
- **Sources & Provenance:** now follows the current calculation. It shows the move representation, baseline/source, modifiers being used, matchup/special route, supporting observations and whatever uncertainty is still left.
- **Confidence / evidence:** now uses the same evidence model across the calculator, Manual Tests and provenance. A character baseline, matchup check and skill-interaction check no longer get flattened into the same vague idea of “tested.”
- **Cursed Internals:** is still there. The normal provenance view is readable; the raw machinery stays in the basement for anyone who insists on opening the basement.

Also fixed: the DP 10 cutoff, the nearly invisible disabled extra-Ki text, and the stale version label in the technical research console.

## What it still does not pretend to know

Some conditional Throws, incomplete Rush strings, beam/repeat behavior and weird special mechanics are still provisional or unresolved. Those are current limits of the model, not promises that another update is coming.

Recorded/reference totals are still useful when the full native path is not available, but that does not automatically make every buff transformation safe. If two sources disagree, the disagreement stays visible.

**Contact only** still means the opening contact against a giant. It does not include later knockback or terrain collisions. Partial cinematics do not quietly absorb unresolved landing damage either.

The goal is the same as before: if the tool knows enough to give you a defensible number, it does. If it does not, it tells you instead of making one up.

## Downloads

**Windows x64**: `SparkingZeroCommunityDamageLab-1.1.1-win-x64.zip`. Extract the ZIP and run `SparkingZeroCalculator.exe`. No separate .NET install or copy of the game is needed.

**Linux x86-64**: `SparkingZeroCommunityDamageLab-1.1.1-linux-x64-wine.zip` or the matching tar.gz. Extract it and run `sh ./start.sh`. Wine 11.0 and the app runtime are bundled; compatible desktop/system libraries are still required.

**macOS**: there is no validated macOS package.

Both supported builds contain the same offline v1.1.1 application and data.

Release hashes are included in CHECKSUMS.sha256.

GitHub’s automatic Source code downloads are the repository documentation, not the program. Use the release packages if you actually want the calculator.

**v1.1.0 is still available.** If you want both versions, extract v1.1.1 into its own folder and keep them side by side.
