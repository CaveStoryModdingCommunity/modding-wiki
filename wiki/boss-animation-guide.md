# <BOA Reference Guide
BOA is a TSC command that is used to animate major bosses.

<BOAwwww

Maps can only have one major boss.

## Balfrog


```
0000: resets position and fully invulnerable
0001: appears to have him slide in the direction he was moving? Also makes him
      impossible to harm, which makes it harder to test how much HP he might
      have
0010: sits there with mouth open; fully invulnerable; contact deals damage
0020: sits there with mouth open; fully invulnerable; contact deals damage, also
      flashing
0100: starts boss-fight patterns; constantly generates frogs falling from the
      ceiling
0130: defeat animations; Balrog automatically seems to leave the area, which deletes
      him
Note: using 0010 or 0020 after 0130 {maybe 0100?} seems to make Balfrog fall down
      and through tiles. After that, using 0100 seems to make Balfrog try to jump
      (unsuccessfully).
```

## Ballos
~~~
0000: makes him vanish?
0001: freezes frame; it seems that if he uses that falling skull attack that it
      will continuously be used
0100: makes a crosshair at the player's location. Ballos then falls there, then
      opens eyes
0200: Starts boss fight animations
0220: Ballos closes eyes again and lands
0300: Ballos is surrounded by those weird eye minion things, these remain if other
      BOAs are used. These also stack
0311: Ballos moves clockwise; starts boss fight animations of third phase, like
      the above, those minions remain if BOA'd to something else
(This one can be interesting - it looks like that if none of those eye minion
 things are there, and this is used, he instead goes to his fourth phase with the
 spikes and the moving platforms and the Butes. Thereafter, using 0300 and then
 0311, he will move clockwise around the room with those eyes and those platforms.
 Alternatively, using 0200 after 0300 will make Ballos jump around.)
1000: Ballos' death animation; this removes all those spikes
Core
0000: resets the Core entirely (even if made invisible)
0001: freezes frames (as does 0015 and 0020)
0200: starts boss fight animations
0500: creates a lot of smoke and moves Core slowly (?) to a specific point in the
      map (somewhere around X:0062 Y:0011)
0600: teleports it away and makes it invisible (using BOA0200 makes it possible
      to fight it with the mini-cores, while the Core itself is invisible)
~~~

## Dragon Sisters

```
0000: not sure what exactly it does, but it moves them around at random; they are
      stationary after this but they still attack. 0002 - 0019 and 0022 - 0025
      does the same, it seems, as does 0200, 0300, 0500 and 0600. This might
      change the movement of the Dragon Sisters somewhat; it's possible to have
      them move in a clockwise elliptical direction
0001: they stop moving in a clockwise direction
0020: they appear, starts boss fight animations. They move in a clockwise circular
      direction.
0100: they start quickly moving in a clockwise direction again
0400: they slowly begin moving in a clockwise direction
0700: Freezes them in place?
1000: death animation; this deletes them. Even in this state, however, they seem
      to deal contact damage.
```

## Heavy Press

```
0000: resets position (as does 0010)
0001: freeze frame in mid-air
0020: stationary, with smoke
0030: falls a short distance; after that it remains still with smoke; it won't
      fall beyond Y:0030 however, and this doesn't destroy tiles
0100: starts boss fight animations regardless of position
0500: death animations; falls (and kills) and destroys seven specific tiles
      (between X:0007 Y:0014 and X:0013 Y:0014). It will fall a little further
      than Y:0030 though; any contact with it, even from the side, deals 127
      damage
```

## Ironhead

```
0000: resets Ironhead to normal
0001: freezes it; still deals damage and can still be killed; seems to prevent
      those fish from spawning
1000: death animation
Note: Ironhead spawns automatically if it is the room boss. The Y co-ordinate
      seems to follow the player's.
```

## Monster X

```
0000: Turns Monster X invisible? (except for the wheels) after BOA0010'd it will
      slide in the direction it was moving previously. If using BOA0010 after it,
      it might look weird
0001: Makes Monster X appear (if the boss' HP bar is visible, it will look like
      Monster X is very damaged); after BOA0010'd it will slide in the direction
      it was moving previously; using this while Monster X's shutter is open might
      make it look weird, but this will restore the green things that fire at the
      player
0010: Start its boss animations; if done after the four green things are destroyed,
      it won't be restored. 0011, 0100, 0200 does this as well.
0012: Opens its eyes (even if the shutter is closed)
0300: Opens its shutter and starts boss fight patterns. 0400 does this too.
0400: Fires out a few more projectiles than normal and slightly quicker. Normal boss fight patterns are still in effect.
0500: Causes it to fire several projectile shots at the start. After that, regular boss fight patterns resume.
0600: Opens its shutter and acts as though it no longer has those four green
      things; those missile fish will appear and it starts boss fight patterns,
      continuing as normal depending on its HP and the green things.
0666: Stays completely still. The same thing happens with 0700, 0800 and 0900.
1000: Instant death
1001: Screen shakes, smoke, then it just turns into a giant cat (without the
      explosion)
```

## Omega

```
0000: resets its position and appears to make it a background object
0001: freezes frames (as does 0002 - 0019, 0021 - 0026)
0020: appears and starts boss fight patterns. Using it again will make Omega will
      go higher than it should, though when it goes back down, it will appear at
      normal height. Using this when it starts jumping, it will remain jumping,
      rather than go back to its default state of hiding in the sand. However, it
      will still come out of the sand (or thin air, or whatever the case may be).
      On death, it is deleted.
0050: immediately attacks using its first phase attack; starts boss fight patterns
0150: death animation; strangely, it doesn't appear to be used in the script itself.
Undead Core
0000: freezes sprite in current frame, slides in direction it was moving in when
      BOA'd. The same applies to 0002 - 0014, 0016 - 0019 and 0021 - 0029.
0001: moves sprite to ~ X:0033 Y:0004 in an inactive, motionless state. Mini-cores
      are also motionless.
0015: activates the first face, like in the cutscene in Cave Story (with smoke).
      Cannot be damaged. Slides in direction it was moving in when BOA'd.
0020: activates the first face, starts boss fight patterns, using 0001 will make
      the mini-cores move around a bit weird when using 0020 again. Also spawns
      those semi-solid mini-cores (the ones that can be jumped on) from the right;
      any other BOA will make those stop
0500: death animation; can cause weirdness if BOA'd during the animation (like
      being partially off-screen when BOA0020'd). If the animation finishes
      playing, the Undead Core is entirely deleted and the mini-cores destroyed;
      to be able to use the BOA command on it again, leave then re-enter the map
```

## Related Pages

[CNP Manipulation (TSC)]()