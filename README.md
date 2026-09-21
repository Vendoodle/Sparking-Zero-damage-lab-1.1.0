# Sparking! ZERO Community Damage Lab

I made an offline damage calculator and character reference for **Dragon Ball: Sparking! ZERO**.

Pick an attacker, defender, costume and move, set whatever states are actually active, and let the calculator do the math. You can compare matchup DP scaling on or off, account for the supported buffs/passives/Sparking states, check costume changes, or just use the Character Map when you want to know what a character actually has without digging through a pile of separate resources.

The data here is built around **game-data build 24953175** and covers **241 playable fighters and forms**.

**1.1.0 is where I’m calling the project finished for now.** I don’t have an update schedule and I’m not promising continued development. If people actually end up caring about it enough to drag me back into the rabbit hole later, maybe I come back to it. No promises.

## What’s actually in here

- **Damage Calculator:** this is the part that does all the math I got tired of doing by hand. It handles the selected move, attacker stats/class tuning, defender resistances, costume replacements, supported skills and passives, low-health states, Sparking, Sparking Boost, its after-effect, Boost Super, and matchup DP scaling where it applies.
- **Character Map:** browse every fighter/form and see their moves, skills, supported passive bonuses, Wickedness level, costume relationships and transformation access where I could identify it.
- **Costumes & Effects:** because some outfits are apparently not content with just being outfits. This tracks the ones with actual gameplay changes, including replacement moves and changes that carry into transformations.
- **Wickedness / Devilmite Beam:** recorded Wickedness levels, confirmed level-0 immunity, and damage calculations where the available data supports them. If physical and energy resistance leave more than one possible answer, you get a range instead of a fake precise number.
- **Advanced / Lab:** the tests, sources, calibration work and notes behind the calculator. If you want to know why I trust a number—or why I don’t—this is where that stuff lives.
- **Cursed Internals:** exactly what it sounds like. This is the much less friendly view of the records and calculations under the hood. If you keep digging, there is also an entire separate technical research console hidden in there. You do not need any of this to use the normal calculator. It is there for the people who see “show me the cursed internals” and immediately click it.

## Giants and Rush attacks

Giants were the last annoying thing I wanted to finish before calling this done.

Some Rush attacks can still play their full cinematic against a giant. Others only land the opening hit before the cinematic gets rejected. **1.1.0 handles those separately instead of pretending they behave the same way.**

That work covers **2,838 neutral Rush/giant combinations**. Six Rush variants have supported giant cinematic routes, and Tapion’s **Brave Sword Attack** has its own calibrated one-hit giant route.

If the calculator says **Contact only**, that means exactly that: the opening contact damage. It does not quietly add later knockback or terrain collision damage.

And if a buff/boost state changes damage but I do not have enough information to calculate that specific rejected-contact interaction accurately, the result stays **incomplete**.

## If the tool doesn’t know, it tells you

This was important to me from the beginning: I would rather give you **no number** than give you a convincing-looking number I cannot actually support.

When the full calculation path can be reconstructed from the game data, that is what the calculator uses. Manual gameplay tests are there to check the reconstruction and fill in pieces the files do not explain cleanly. Community/reference totals are still useful where the internal path is incomplete.

Results are labeled so you can tell whether something is reconstructed, a recorded check, an estimate or incomplete. Missing information stays missing instead of borrowing some other move’s damage just to fill the box. A range means there is still a detail I cannot resolve honestly enough to collapse it into one number.

This is a community research tool, not a claim that I have reproduced every single thing the game engine can possibly do.

## Downloads

Grab **1.1.0** from the [release page](https://github.com/Vendoodle/Sparking-Zero-damage-lab-1.1.0/releases/tag/v1.1.0).

**Windows x64:** download `SparkingZeroCommunityDamageLab-1.1.0-win-x64.zip`, extract it, and open `SparkingZeroCalculator.exe`. It works offline and does not need a separate .NET install or a copy of the game.

**Linux x86-64:** use the **r1** package: `SparkingZeroCommunityDamageLab-1.1.0-linux-x64-wine-r1.zip` or `.tar.gz`, extract it, then run `sh ./start.sh`. Wine 11.0 and the app runtime are bundled, so you do not need to install Wine or .NET separately. I validated r1 on Debian 13 x86-64 under X11/Xvfb + Openbox; I have not tested every distro and desktop combination, so I’m not going to pretend I have.

**macOS:** there is no validated macOS package in this release.

Hashes are included with the downloads. GitHub’s automatic **Source code** archives are the repository documentation, not the application itself, so use the release packages above if you actually want the program.

## How this got out of hand

This project started because **Supreme Kai was weirdly strong** and I wanted to know why.

That turned into manual damage testing. Then hidden classes. Then spreadsheets. Then comparing what I was seeing against community data. Then digging through the game files because apparently I needed to know what the numbers were actually doing.

Eventually the spreadsheet stopped being enough, so now there is software.

Somewhere along the way it picked up a full Character Map, costume and move-change tracking, Wickedness data, giant-specific Rush handling, deeper research pages, and an entire second research console hiding underneath the normal calculator because apparently nobody involved knew when to stop.

Several intermediate builds existed while all of this was changing quickly, but public distribution was effectively interrupted around **1.0.2**. So no, 1.0.3 → 1.0.4 → 1.0.5 → 1.1.0 was not some neat public release cycle. Those were research builds happening while the thing was still mutating.

**1.1.0 is just the point where I finished what I actually wanted to finish and shipped it.**

This project started because Supreme Kai was weirdly strong.

**Now there is software.**
