# Lunar phase

Calculate phase of the moon using Julian date.

# Getting Started

To install, execute:

    npm i lunarphase-js

Then, import into a project as:

```js
import { Moon } from "lunarphase-js";
```

# Usage

In the lunar calendar there are 8 phases each synodic month, which is the number of days to complete the cycle. This time between two identical syzygies is equivalent to 29.53059 Earth days.

Lunar phases, in order:

| Phase           | Northern Hemisphere | Southern Hemisphere |
| --------------- | ------------------- | ------------------- |
| New             | 🌑                  | 🌑                  |
| Waxing Crescent | 🌒                  | 🌘                  |
| First Quarter   | 🌓                  | 🌗                  |
| Waxing Gibbous  | 🌔                  | 🌖                  |
| Full            | 🌕                  | 🌕                  |
| Waning Gibbous  | 🌖                  | 🌔                  |
| Last Quarter    | 🌗                  | 🌓                  |
| Waning Crescent | 🌘                  | 🌒                  |

## Julian Day

Convert to and from Gregorian Dates to Julian Days via the `JulianDay` module.

API Reference:

| Function   | Output                   | Description                |
| ---------- | ------------------------ | -------------------------- |
| fromDate() | 2459357.5380029744       | Convert date to Julian Day |
| toDate()   | 2021-05-23T05:56:10.418Z | Convert Julian Day to date |

To convert a date to Julian Day:

```js
import { JulianDay } from "lunarphase-js";

const date = new Date();
const julian = JulianDay.fromDate(date);
```

To convert a Julian Day to a date:

```js
import { JulianDay } from "lunarphase-js";

const julian = 2459356.529302257;
const date = JulianDay.toDate(julian);
```

## Lunar Phases

API Reference:

| Function          | Output              | Description                                |
| ----------------- | ------------------- | ------------------------------------------ |
| lunarPhase()      | Waxing Gibbous      | Get lunar phase for a given date           |
| lunarPhaseEmoji() | 🌖                  | Get emoji of lunar phase for a given date  |
| isWaxing()        | true                | Whether the moon is waxing                 |
| isWaning()        | false               | Whether the moon is waning                 |
| lunarAge()        | 11.367344279004676  | Earth days since the last new moon         |
| lunarAgePercent() | 0.38497186542446116 | Percentage through the lunar synodic month |
| lunationNumber()  | 1217                | Brown Lunation Number (BLN)                |

For a specific date, pass a date object to a function

```js
import { Moon } from "lunarphase-js";

const date = new Date();
const phase = Moon.lunarPhase(date);
```

Otherwise, current date will be used

```js
import { Moon } from "lunarphase-js";

const phase = Moon.lunarPhase();
```

### Lunar Phase

To get the current lunar phase from the `LunarPhase` enum (ex: "Full")

```js
const phase = Moon.lunarPhase();
```

### Lunar Phase Emoji

To get the current lunar phase emoji from the `LunarEmoji` enum (ex: "🌕"):

```js
const phaseEmoji = Moon.lunarPhaseEmoji();
```

As phases are inverted between Northern and Southern Hemispheres, optionally pass a `Hemisphere` to the function:

```js
import { Moon } from "lunarphase-js";
import { Hemisphere } from "lunarphase-js";

const date = new Date();
Moon.lunarPhaseEmoji(date, Hemisphere.Northern);
```

To get emoji for other lunar phases, pass a `LunarPhase` enum:

```js
const emoji = Moon.emojiForLunarPhase(Moon.LunarPhase.Full);
```

Optionally pass a `Hemisphere` to the function:

```js
import { Moon } from "lunarphase-js";
import { LunarPhase } from "lunarphase-js";
import { Hemisphere } from "lunarphase-js";

Moon.emojiForLunarPhase(LunarPhase.FirstQuarter, Hemisphere.Southern);
```

### Waxing

Whether the moon is waxing (ex: false)

```js
const waxing = Moon.isWaxing();
```

### Waning

Whether the moon is waning (ex: true)

```js
const waning = Moon.isWaning();
```

### Lunar Age

To get the lunar age (ex: 16.54412413414952)

```js
const age = Moon.lunarAge();
```

### Lunar Age Percent

To get the percentage through the lunar cycle (ex: 0.5602368519132597)

```js
const agePercent = Moon.lunarAgePercent();
```

### Lunation Number

Brown Lunation Number (BLN), per Ernest William Brown's lunar theory, defining Lunation 1 as the first new moon of 1923 at approximately 02:41 UTC, January 17, 1923

```js
const lunationNumber = Moon.lunationNumber();
```
