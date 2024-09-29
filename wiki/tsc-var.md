
# VAR command

This document outlines the behavior and standard implementation of the `<VAR` command, a 3rd-party TSC command that lets the user set numeric variables instead of just single bits.

There are several different implementations of this command that are implemented slightly differently, but perform many of the same actions.

## AVA (Freeware DLL)
One of the many features that come with the [AVA modloader patch](ava). Variables are stored internally as 32 bit integers, and appended among other things to the save file. *(Note that saves made with AVA break compatability with vanilla!)* There are currently 100 avalable in a static array.

- `VARxxxx:yyyy` - `VARiable`, Set variable `xxxx` to `yyyy`
- `VA+xxxx:yyyy` - `VAriable +`, Add number `yyyy` to variable `xxxx`
- `VA-xxxx:yyyy` - `VAriable -`, Subtract number `yyyy` from variable `xxxx`
- `VA*xxxx:yyyy` - `VAriable *`,  Multiply number `yyyy` with variable `xxxx`
- `VA\xxxx:yyyy` - `VAriable \`, Divide number `yyyy` into variable `xxxx` *(integer only, dangling decimals will be trimmed!)*
- `VAJwwww:xxxx:yyyy:zzzz` - `VAriable Jump`, compare **raw number number** `wwww` to `xxxx` using operation `yyyy`, and jumping to `zzzz` if true. (also see [addressing](#addressing))

    `yyyy` operations:
    - `0000` - `wwww` == `xxxx`
    - `0001` - `wwww` != `xxxx`
    - `0002` - `wwww` > `xxxx`
    - `0003` - `wwww` < `xxxx`
    - `0004` - `wwww` >= `xxxx`
    - `0005` - `wwww` <= `xxxx`
    - `0006+` - doesn't jump

- `VAZxxxx:yyyy` - `VAriable Zero`, Sets `yyyy` number of variables starting at `xxxx` to zero
- `VNDxxxx:yyyy:zzzz` - `Variable raNDom`, Assigns `zzzz` to a random number between `xxxx` and `yyyy`
- `VIJxxxx:yyyy:zzzz` - `Variable Increment Jump`, Increments variable `xxxx` by 1 until `xxxx` is >= `yyyy`, then it zeros `xxxx` and jumps to `zzzz`

### Addressing
Any numeric arguments for any TSC prefixed with `V` will instead use the corresponding variable at that address.

Example:
```
<FAI0004 // fades in with direction "4"
<FAIV010 // fades in using the value of variable 10
```

## TSC+ (ASM Hack)
This is a hack for freeware bundled with most releases of [Booster's Lab](boosters-lab). Variables are stored internally as a 16 bit integer, and are saved in the profile, reusing flags `6000`-`8000`. There are 124 *(0-123)* avalable for use. Flags beyond this are considered *out-of-bounds* and will affect other parts of memory!

- `VARxxxx:yyyy` - Set variable `xxxx` to `yyyy`
- `VAOxxxx$yyyy` - Perform operation `$` between `xxxx` and `yyyy`
  
    Valid operations: `+, -, *, %` *(note: `%` is NOT modulus here)*
- `VAJwwww:xxxx:yyyy:zzzz` - compare **raw number number** `wwww` to `xxxx` using operation `yyyy`, and jumping to `zzzz` if true. (also see [addressing](#addressing-1))

    `yyyy` operations:
    - `0000` - `wwww` == `xxxx`
    - `0001` - `wwww` != `xxxx`
    - `0002` - `wwww` > `xxxx`
    - `0003` - `wwww` < `xxxx`
    - `0004` - `wwww` >= `xxxx`
    - `0005` - `wwww` <= `xxxx`
    - `0006` - always jumps
- `RNDxxxx:yyyy:zzzz` - `RaNDom`, Assigns `zzzz` to a random number between `xxxx` and `yyyy`


### Addressing
Any numeric arguments for any TSC prefixed with `V` will instead use the corresponding variable at that address.

Example:
```
<FAI0004 // fades in with direction "4"
<FAIV010 // fades in using the value of variable 10
```



