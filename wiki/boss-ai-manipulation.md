# Boss AI Manipulation
Boss AI Manipulation refers to when two (or more) boss AIs are run at the same time.

This can be achieved by having an entity whose npc number is outside the bounds of the regular npc table (anything above 360), and has crossed into the boss table.

In Cave Story freeware, this means that "entities" 361-370 are bosses. In other engines this range will be different.

## OOB NPC/Boss numbers

361. Null

362. Omega

363. Balfrog

364. Monster X

365. Core

366. Ironhead

367. Sisters

368. Undead Core

369. Heavy Press

370. Ballos Ball

## Chart of 2 AI combinations

It is possible to have more than 2 boss AIs running at the same time, this is just for convenience.

The first column represents the boss assigned to the current map, and the first row represents what boss has been <CNPed/placed with an OOB npc number.

|             | Omega | Balfrog | Monster X | Core | Ironhead | Sisters | Undead Core | Heavy Press | Ballos Ball |
|:-----------:|:-----:|:-------:|:---------:|:----:|:--------:|:-------:|:-----------:|:-----------:|:-----------:|
| Omega       | 2x    |         |           |      |          |         | Crash       |             |             |
| Balfrog     |       | 2x      |           |      |          | Crash   |             |             |             |
| Monster X   |       |         | 2x        |      |          | Crash   |             |             |             |
| Core        |       |         |           | 2x   |          | Crash   | Crash       |             |             |
| Ironhead    |       |         |           |      | 2x       | Crash   |             |             |             |
| Sisters     |       |         |           |      |          | 2x      |             |             |             |
| Undead Core |       |         | Crash     |      |          | Crash   | 2x          |             |             |
| Heavy Press |       |         |           |      |          | Crash   |             | 2x          |             |
| Ballos Ball |       |         |           |      |          | Crash   |             |             | 2x          |

All bosses put with themselves result in twice the speed+projectiles. Balfrog will also turn intangible and not be able to hop very well.

All descriptions below this point were originally written by DoubleThink

## Omega
Omega + Core (Trashed Omega):

A mess of 2+ sprites joined together. Smaller hitbox, only on left side. Takes one cycle to appear, after which it sticks out when trying to bury itself. Moves along the ground rather than jumping during second phase. Defeating triggers the normal ending sequence??

### Omega + Ballos:

Fires first attack offscreen, locks on and smashes down from above, then does nothing. Can't seem to damage even if you get caught under it.

### Omega + Monster X:

Omega's body replaces Monster X's body, and no tracks are visible, but other than that functions roughly as normal. Phase 1 appears to skip itself though. On death, repeatedly explodes garbage sprites down left.

### Omega + Sisters:

Omega becomes a glitchy mess in the top left of the map (around 0,0). Phase 2 will allow him to hop as he normally would.

## Balfrog
### Balfrog + Omega:

Small tunnelling noise at start, followed by regular Balfrog fight except he's undamageable.

### Balfrog + Monster X:

Doesn't move when jumping. Still undamageable.

### Balfrog + Core:

Very small jumps. Undamageable.

### Balfrog + Ironhead (Unstable Balrog Dance Form):

Immediately flies forward to your position spawning a single Critter fishie, then continues trying to move right. Escapes to the side after spawning one full wave of fishies and never returns. Can be damaged! Game continues as normal if you can kill it in time.

### Balfrog + Undead Core:

Spawns one ceiling-tracking projectile and then fight continues much like the regular Core combo (small jumps, undamageable).

### Balfrog + Heavy Press:

Smoke wave in middle of screen + one Critter Bute spawned on right, then nothing.

### Balfrog + Ballos:

Lock-on teleporting frog jumps! Still undamageable, unfortunately.

## Monster X
### Monster X + Omega:

Normal X fight except it's got an extra pair of treads attached to its lower right side.

### Monster X + Balfrog:

Main body is invisible. Will switch direction once after catching then continue to the left forever.

### Monster X + Core (Hydraulic Chaser):

Only one leg top and bottom, top has double treads. Body will attempt to move toward you like the Core does. Will stop on the 6th direction change instead of the 3rd, after which the body will trigger the Core defeat animation (closing its eyes, which then remain closed) and return to its initial position before starting the chase pattern again, skipping any way to be damaged. Liable to crash.

### Monster X + Ironhead:

One extra tread on its lower right side. Central parts will do a whacky disjointed teleport and rejoin and the extra tread will start animating at the first direction change, then it continues left unstopping. Spawns one wave of white sheet fishies on its way out. Will disappear once it travels a fair distance, to be followed by a completely inert copy of itself right after that that continues forever.

### Monster X + Heavy Press (Monster Stack):

Has extra treads and the main body stacked up above the wheels. Will keep going until the 5th direction change, often (but not always) firing off a lightning bolt as it does (that doesn't reach the ground), then it will do the Heavy Press -127 drop and fall off screen. No apparent way to damage it before it leaves the fight in limbo.

### Monster X + Ballos:

Stays completely in place and pounds the ground using Ballos 2's pattern style. Does no damage and takes no damage.

## Core
### Core + Omega:

Normal fight except some of the graphics are a bit messed up (front of the Core is red during its closed cycle, mini cores stay blue-flashed sometimes, defeat animation has extra sprite pieces).

### Core + Balfrog:

Boss immediately descends downwards offscreen and never returns. Mini cores follow after first open cycle.

### Core + Monster X:

Boss immediately flies straight to the left and then the game crashes.

### Core + Ironhead:

Normal fight except a small part of the back of the Core doesn't flash properly when taking damage.

### Core + Heavy Press:

Boss immediately disappears, presumably somewhere to the left because that's where the mini cores fly off to.

### Core + Ballos (Pound Gunner):

Core continuously tries to slam like Ballos 2 as it floats toward you. Can also produce Ballos' shockwaves depending on where it lands. There are only 3 mini cores which stay locked in place around the main Core, each of which will fire off a single set of their spinning shots in between jump attempts. Will never open up, so can never be damaged. Would probably work better in a flatter room.

## Ironhead
### Ironhead + Omega:

Normal fight, zero changes that I can see.

### Ironhead + Balfrog:

Disappears downwards again. Fishies also stop spawning after the second wave.

### Ironhead + Monster X:

Boss never appears, fishies stop after first wave.

### Ironhead + Core:

Normal fight except Ironhead is way slower than usual.

### Ironhead + Undead Core:

Same as above, except he starts in the backward-moving part of his attack pattern rather than the forward-moving one.

### Ironhead + Heavy Press:

Normal fight, except accompanied by lightning attack noises offscreen and single Ikachan-Bute spawns.

### Ironhead + Ballos:

Fight starts as normal, then Ironhead lock-on teleports to your positon, falls off screen and then the spawns stop.

## Sisters
### Sisters + Omega:

Invisible, damageable Omega appears right above where you spawn, shoots out one set of brown falling projectiles and then moves offscreen.

### Sisters + Monster X:

A broken sprite flies off to the left making shooting sounds and then the game crashes.

### Sisters + Core (Sisters' Backup Replacements):

Only the sister on the right is visible at first, with its head and body the wrong way around. After it starts moving the other sister will fly to a spot based on your vertical position (?) and stay there unless shot. First sister will also zip left and then rotate and fire as normal, second sister will constantly try to shoot until her mouth is closed. When damaged, she'll move backwards to the right and eventually offscreen in a Core-ish fashion. They can still be beaten by shooting the first sister, but while the screen goes white during their defeat the game will crash.

### Sisters + Ironhead (Invisiblehead):

Sisters will initially appear, but then quickly disappear. Waves of Behemoth-head fishies will continually spawn along the right wall and fly backwards after a moment. Something invisible and damageable will move on and off the right side of screen in Ironhead's pattern. Constant fireball shooting noise in the background, occasionally white projectiles fly left in the lower half of the screen. Game can be continued as normal if you can manage to beat the unseen boss!

### Sisters + Undead Core (Dragon Wall):

Both sisters appear fairly close to each other with their heads slightly disjointed, and remain locked in step with each other as they slowly trek right (!!) until the far one is fully off screen, using the UC's floor/ceiling grenade attack. They will then move back to their starting position and repeat. Sometimes they'll try to use the spinning projectile attack, which won't spawn. Their expressions change much as the UC's would between its different attacks. No way to damage them.

### Sisters + Heavy Press:

Single sister appears right over the player as the fight starts, then immediately disappears.

### Sisters + Ballos:

Singler sister appears right over the player again, then turns into a double sister and falls through the floor. Keeps firing fireballs, which can be seen pinging off the bottom of the room.

## Undead Core
### Undead Core + Omega:

Instantly explodes (boss HP bar never appears).

### Undead Core + Balfrog:

Descends straight down off screen.

### Undead Core + Core (Unfixed Core):

Much more like a regular Core fight. Moves back and forward like UC but tracks the player vertically. Rapidly moves through regular Core's attacks somewhat inconsistently, including summoning a current! It does this as a solo attack, instead combining the laser balls with UC's spinning projectile attack. If it gets to low health and tries to use UC's laser attack, it will fail and instead start using nothing but the floor and ceiling grenades from then on. Does close up and block damage frequently, sometimes for extended periods (like right near the start), but never makes the fight unwinnable.

### Undead Core + Ironhead:

Normal fight with no apparent changes.

### Undead Core + Ballos:

Fight starts as normal, but then it will slowly move down and hide in the wall making Ballos thumps and can no longer be damaged.

## Heavy Press

*Extra note: It's hard to tell what counts as "winning" these fights or not because dropping down to the Plantation sideroom never triggers the block-destroying animation that opens the way to the Seal Chamber in this mod.*

### Heavy Press + Omega:

Normal fight except the bottom of the sprite is a bit messed up.

### Heavy Press + Balfrog:

The combined falling power makes Heavy Press drop before the map even finishes fading in, doing 10 damage and sending the player straight down to the Plantation.

### Heavy Press + Monster X (Press On Rails):

Heavy Press starts on the right and tracks the player on a horizontal path through the walls like Monster X, firing off a lightning bolt with each direction change. After the 3rd move it will activate its falling animation wherever it ends up, before it can take any damage.

### Heavy Press + Core:

Normal fight with some lightning bolt sprite artifacts. When it beaten it drifts slightly to the right then falls down really slowly.

### Heavy Press + Ironhead (Chunkyhead):

Much like the Sisters + Ironhead combo. Heavy Press remains visible, flashing as it moves in and out of the right side of the arena. Its entire body is now a hitbox. Spawns of Bute fishies will alternate between the right side wall and flying in from the far right of screen. The blocks that usually hide Heavy Press will keep trying to "update" themselves inconsistently. Upon defeat it will cause some momentary lag then drop down from wherever it is.

### Heavy Press + Undead Core:

Manages to fade in but then crashes before anything can happen.

### Heavy Press + Ballos:

Locks on and then falls down right away and gets stuck in the floor. Doesn't end the fight and can't be damaged.

## Ballos
### Ballos + Omega:

Normal fight with part of an extra head stuck on his bottom-right corner and a smaller hitbox (can shoot both eyes, but can't shoot through both of them at once).

### Ballos + Balfrog:

Starts by falling through the floor, but then reappears with a red-flashed right side and starts jump-falling halfway out of the floor using Ballos 2's pattern. Can't be damaged. Will push you far down into the ground if you stand under him.

### Ballos + Core:

Ballos with several extra attachments will slowly move down toward the player, bouncing in this fashion while also trying to hover like the Core. Will shoot dark flappy Core projectiles at the end of each set of bounces. Can't be damaged.

### Ballos + Ironhead:

Normal fight with only a small bit of extra sprite and a normal hitbox.

### Ballos + Undead Core (Ultimate Unholy Combination):

Starts visible on the far right, then locks on and drops down very slowly. More of a sprite tower than a blob. Moves back and forth across the screen like UC while releasing shockwaves like Ballos 2. Can't be damaged.

### Ballos + Heavy Press:

Normal fight pattern with most of an extra face attached and a single extra broken Bute spawn at the start. Can be shot but won't take any damage from it.

## Related Pages

[BOA (TSC)](boss-animation-guide)