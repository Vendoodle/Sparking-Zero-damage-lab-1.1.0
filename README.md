# Sparking! ZERO Community Damage Lab

I made an offline damage calculator and character reference for **Dragon Ball: Sparking! ZERO**.

**v1.1.1 is the finished version.**

Pick an attacker, defender, costume and move, turn on whatever is actually active, and it gives you the damage. There’s also a Character Map, costume/move changes, Wickedness data, the manual testing behind everything, and a progressively more cursed amount of technical information if you keep digging.

The data is built around **game-data build 24953175** and covers **241 playable fighters and forms**.

This whole thing started because I like Supreme Kai.

That’s it. That’s the origin story.

*“Why the hell does this tiny purple Kai hit like a freight train?”*

That sent me down a rabbit hole.

Then I made a spreadsheet.

Then the spreadsheet got bigger.

Now there is software.

I have no one to blame but myself.

## What’s actually in here

- **Damage Calculator:** pick the matchup and move, set whatever effects are active, and get the result. It handles the supported attack modifiers, defenses/resistances, costumes, low-health effects, Sparking states, extra-stock Sparking Boost, extra-Ki Super boosting and DP matchup scaling where they actually apply.
- **Character Map:** lets you browse the fighters/forms and see their moves, skills, supported passives, Wickedness, costume relationships and transformation access where I could identify it.
- **Costumes & Effects:** because some costumes are apparently incapable of just being cosmetic. This shows the ones that actually change moves or transformation behavior.
- **Manual Tests:** the lab notebook. These are the actual gameplay tests I performed or recorded, all in one place. You can filter them down to the current matchup or just browse everything. Reconstructed values are not mixed in and presented as if I manually tested them.
- **Sources & Provenance:** if you want to know why the calculator believes a number, this is where you look. It shows what move representation is being used, where the baseline came from, what modifiers were applied, what manual evidence exists and what parts are still uncertain.
- **Cursed Internals:** exactly what it sounds like. Rawer data, calculations and the ugly machinery behind the friendly result. There’s also an entire separate research console hiding in there because apparently we lost control of the situation at some point.

You absolutely do not need Cursed Internals to use the calculator.

Some of you are going to click it immediately anyway.

## The damage model got a lot less stupid

One of the biggest changes in v1.1.1 is that the calculator now uses the amount of information the calculation actually needs.

Previously, some moves could have a perfectly good recorded damage value and still become unavailable as soon as a buff was selected because the calculator wanted per-hit data it didn’t actually need.

Throws were the glaring example.

The game already had native Throw data. The calculator just wasn’t using it.

So now, if the source gives us a valid aggregate value, the calculator can use that aggregate value where the mechanic allows it. It does not invent fake hit values just because an animation happens to hit more than once.

If a mechanic genuinely needs individual damage terms, though, those still have to be known.

**use the data we actually have instead of demanding data the calculation doesn’t need.**

Buffs got the same treatment. They now use the fields they actually modify instead of getting treated like generic percentages slapped onto an already-rounded damage number.

For example, I manually checked Tora’s Throw against Goku (Z - Early):

| **Tora’s state** | **Damage** |
| --- | --- |
| Neither | 1,188 |
| Saiyan Spirit | 1,313 |
| Low health | 1,313 |
| Both | 1,438 |

Those values line up with the game data and the reconstructed calculation path.

That does not mean every buff works like this.

It means this one does, and now the calculator knows why.

## If it doesn’t know, it says so

This has been one of my rules for the project from the beginning:

**I would rather give you no number than give you a convincing fake one.**

v1.1.1 is better at distinguishing between something reconstructed from the game data, something directly observed in testing, something supported but still provisional, something where more than one answer is possible, and something the calculator genuinely cannot resolve yet.

Not every fighter/move/effect combination needs its own manual test before the calculator can use a rule that is already supported by the underlying data.

At the same time, one successful test does not magically prove every similar-looking interaction in the game.

The app keeps those distinctions now.

Manual Tests, Sources & Provenance and the calculator result all use the same evidence model, so the number and the reason for trusting that number are no longer living in separate universes.

Recorded/reference totals are also kept when they are still useful. If the native reconstruction and an existing reference disagree, that disagreement stays visible instead of quietly changing one number until everything looks pretty.

Some conditional Throws, incomplete Rush strings, beam/repeat behavior and weird special mechanics are still provisional or incomplete.

That’s fine.

That’s what the labels are for.

## Giants are still weird

Rush attacks against giants are handled separately because the game handles them separately.

Some can play their full cinematic.

Some hit once and then get rejected.

**Contact only** means exactly that: the opening contact damage. It does not secretly include later knockback or terrain collisions.

If the available data cannot support a modified contact result accurately, the calculator marks it incomplete instead of making something up.

Devilmite Beam also keeps its Wickedness handling, including ranges where the available resistance information leaves more than one supported result.

## Downloads

Get **v1.1.1** from the release page:  
https://github.com/Vendoodle/Sparking-Zero-damage-lab-1.1.0/releases/tag/v1.1.1

### Windows x64

Download:

`SparkingZeroCommunityDamageLab-1.1.1-win-x64.zip`

Extract the whole ZIP and run:

`SparkingZeroCalculator.exe`

No separate .NET install or copy of the game is required.

### Linux x86-64

Download the v1.1.1 Linux ZIP or tar.gz, extract it, then run:

`sh ./start.sh`

Wine 11.0 and the app runtime are bundled. It is the same calculator and data as the Windows build, just running through Wine. The first launch takes a little longer while it sets up its private Wine environment.

Compatible 64-bit Linux desktop/system libraries are still required; there’s a guide in the package.

### macOS

There is no validated macOS package.

Both supported builds work offline.

Release hashes are included in `CHECKSUMS.sha256`.

GitHub’s automatic Source code downloads are just the repository documentation, not the application, so grab one of the release packages if you actually want to use the program.

**v1.1.0 is still available** on its original release page:  
https://github.com/Vendoodle/Sparking-Zero-damage-lab-1.1.0/releases/tag/v1.1.0

If you want to keep both, extract v1.1.1 into its own folder.
