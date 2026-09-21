# Sparking! ZERO Community Damage Lab — 1.1.0

**This is the finished version of the offline damage calculator and character reference I built for Dragon Ball: Sparking! ZERO.**

Pick an attacker, defender, costume and move, then compare the result. The project combines manual gameplay testing, community reference information and data pulled from game build **24953175**, covering 241 playable fighters and forms.

## What this release contains

- **Damage Calculator:** handles the move you picked, attacker and defender stats, class tuning, costume replacements, supported skills/passives, low-health states, Sparking, Sparking Boost and its after-effect, Boost Super, and matchup DP scaling where it applies.
- **Character Map:** browse fighters/forms and see their moves, skills, supported passive bonuses, Wickedness levels, costume relationships and transformation access where I could identify it.
- **Costumes & Effects:** tracks outfits that actually change gameplay, including replacement moves and changes tied to transformations.
- **Devilmite Beam:** uses the recorded Wickedness data anywhere I had enough information to calculate it. Confirmed immune characters are level 0, and some resistance combinations show a range instead of pretending there is one exact answer.
- **Advanced / Lab:** contains the tests, sources and notes behind the calculator, including places where the available data still leaves gaps.
- **Cursed Internals:** exposes the uglier records and calculation details underneath the normal UI. There is also an entire separate technical research console tucked inside if you really want to dig through the machinery.
- **Giants / Rush attacks:** 1.1.0 finishes the giant/Rush work I was able to resolve. Some Rush attacks can still play their full cinematic against giants; others only land their opening hit before the cinematic is rejected, so those cases are handled separately. That covers 2,838 neutral Rush/giant combinations, including six supported giant cinematic variants and Tapion’s calibrated one-hit giant route.

## Reading the results

If the calculator knows the answer, it gives you the best result I could support from the available data. If it doesn’t, it says so.

Results are labeled as reconstructed, recorded checks, estimates or incomplete. Missing information stays missing instead of borrowing another move’s damage just to fill the box. A range means there is still something I can’t resolve cleanly enough to collapse it into one number.

**Contact only** means the opening contact damage against a giant. It does not include later knockback or terrain collisions. If a damage-changing state still can’t be calculated reliably for that contact-only case, it stays incomplete.

That still doesn’t mean every possible matchup or engine behavior has been reproduced. The data in this release targets game build **24953175**.

## Choose a download

- **Windows x64:** `SparkingZeroCommunityDamageLab-1.1.0-win-x64.zip`. Extract it and open `SparkingZeroCalculator.exe`; no separate .NET or game installation is required.
- **Linux x86-64:** choose either `SparkingZeroCommunityDamageLab-1.1.0-linux-x64-wine-r1.zip` or `SparkingZeroCommunityDamageLab-1.1.0-linux-x64-wine-r1.tar.gz`. Extract it and run `sh ./start.sh`. Wine 11.0 and the app runtime are bundled; compatible Linux system/desktop libraries are still required. The earlier Linux assets remain only for existing links; choose **r1**.
- **macOS:** no validated macOS package is included in this release.

Both packages work offline.

Windows hashes are in `CHECKSUMS.sha256`; Linux r1 hashes are in `LINUX-r1-CHECKSUMS.sha256`. GitHub’s automatic **Source code** archives contain repository documentation rather than the application. Source code is not included in the downloadable packages.

## Release state

**1.1.0 is where I’m calling the project finished for now.** I don’t have a planned update schedule and I’m not promising continued development. If the community actually ends up interested enough to pull me back into it later, I may come back to it, but this release stands on what it contains now.

The project changed so fast that the intermediate builds were never a neat public release sequence. Public sharing basically stopped around 1.0.2, so 1.1.0 is the finished state of the project rather than the next patch in a normal update cycle.
