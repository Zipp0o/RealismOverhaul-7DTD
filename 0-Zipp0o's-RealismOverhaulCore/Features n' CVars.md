# Zipp0o`s Realism Overhaul  
### Complete Feature Guide & CVAR Reference

A full overhaul that transforms 7 Days to Die into a deeper, simulation driven survival experience.



## ⚠️ Important
This is a **CORE mod**.  
Other mods may depend on it.



## 🧠 What This Mod Does

Realism Overhaul turns 7 Days to Die into a more simulation heavy survival experience with:

	- A real calendar + season framework  
	- Lunar driven blood moon scheduling  
	- Seasonal day length and moon behavior  
	- Dynamic weather data exposed to CVars  
	- Atmosphere, fog, sky, and lighting overhauls  
	- HUD/compass data extensions  
	- Visual realism locks (brightness + shadow floor for servers)  



## ⚙️ Features

### 🌍 Calendar, Seasons, Lunar, CVar ENGINE...

	- Full Gregorian calendar progression from game day to real date  
	- Leap year support  
	- Month/day/day of year tracking  
		- Astronomical season boundaries:
		- Spring starts Mar 20  
		- Summer starts Jun 21  
		- Autumn starts Sep 1  
		- Winter starts Dec 21  
	- Dynamic day length + night length by season  
	- Day of week tracking (Monday start)  
	- Date key CVars (`IsDecember25`, `Date1225`, etc.)  
	- Lunar cycle computation (synodic month model)  
	- Lunisolar metadata outputs (year/month/day/leap flags)  
	- Blood moon strength calculation from lunar phase window position  
	- CVar caching and throttled updates for performance  
	- Biome detection CVars  
	- Weather state CVars (temp/wind/rain/snow/fog/clouds/storm)



### 🌕 Lunar blood moon scheduling and scaling

	- Overrides vanilla blood moon day scheduling with lunar based day selection 
	- Runtime re-sync to prevent vanilla scheduler drift 
	- Seasonal dusk/dawn integration for blood moon time checks  
	- Strict blood moon visibility handling for sky rendering hooks  
	- Pre dusk blood moon visual ramp-in  
	- Blood moon party scaling by `LunarBloodMoonStrength`:
	- Adjusts `enemyActiveMax`  
	- Adjusts party spawner `maxAlive`  



### 🌅 Seasonal dawn / dusk controller

	- Seasonal dawn/dusk hours pushed into `SkyManager`  
	- Daily refresh and safe time update windows  
	- Shared helper used by blood moon/thunder windows  



### 🌙 Moon, sky, and nighttime darkness stack

	- 7-phase moon system tied to lunar phase outputs  
	- Phase dependent moon light intensities  
	- Phase dependent lightning multipliers  
	- Moon brightness and moon ambient overrides  
	- Moon sprite phase correction and shader direction updates  
	- Night ambient darkening for low/new moon nights  
	- Cloud moon lighting adjustments  
	- Blood moon sprite scale boost  



### 🌫 Fog color system

	- Night fog darkness multiplier by moon phase  
	- Smooth dusk and dawn blending in/out  



### 🎨 Ambient lighting and color atmosphere

	- Season specific ambient presets for:
	- Outdoor equator/sky/ground  
	- Indoor equator/sky/ground  
	- Moon ambient influence  
	- Seasonal sun color palette blending (spring/summer/autumn/winter)  
	- Smooth palette interpolation across season progress  
	- Time of day aware dawn/day/dusk/night spectrum blending  



### 🧭 Compass / hud binding extensions

	#### Custom bindings for:
	
	- Calendar strings  
	- Season strings  
	- Weekday + short weekday  
	- Moon phase, lunar day/month, lunar compact  
	- Moon age and phase color  
	- Full moon forecast by month  
	- Remaining full moon window nights in current month  
	- Weather icons + icon colors  
	- Day color with blood moon override logic  
	- Compass compatibility patch for dual temperature labels



### 🌑 Night UI dimming

	- Dynamic nighttime UI darkening based on:
	- Night progress  
	- Moon phase darkness  
	- Separate background/foreground opacity controls  
	- Smooth transition speed  
	- Label color multiplier patch  
	- Optional disable via CVar  



### 🔒 Visual realism enforcement

- Brightness lock to `0.5`  
- Shadow quality clamped to minimum enabled level (Low/HardOnly floor)  



## 🧪 CVAR LIST (PUBLISH SECTION)



### Calendar and time CVars

- `AbsoluteDay` (absolute game day index starting at 1)  
- `YearNumber` (current Gregorian calendar year)  
- `DayOfYear` (day number inside current year)  
- `MonthNumber` (current month number, 1-12)  
- `DayOfMonth` (current day of month)  
- `DaysInMonth` (number of days in current month)  
- `DaysPerYear` (365 or 366 for leap years)  
- `IsLeapYear` (1 when current year is leap year)  
- `CurrentHour` (current in-game hour, 0-23)  
- `TimeHM` (current time in HHMM integer format)  
- `DayLength` (current daylight duration in hours)  
- `NightLength` (current night duration in hours)  
- `DayFraction` (time-of-day as 0.0-1.0 day progress)  



### Season CVars

- `IsSpring` (1 when current season is spring)  
- `IsSummer` (1 when current season is summer)  
- `IsAutumn` (1 when current season is autumn)  
- `IsWinter` (1 when current season is winter) 
 
- `SeasonDayIndex` (day index inside current season, 0-based)  
- `SeasonProgress` (season progress from 0.0 to 1.0)  
- `DaysPerSeason` (length of current season in days)  
- `SeasonOffsetDays` (day-of-year where current season starts)  
- `SeasonDayOfYearStart` (first day-of-year of current season)  
- `SeasonDayOfYearEnd` (last day-of-year of current season)  
- `CalendarStartOffsetDays` (season start index override, 0-3)  



### Month CVars

- `IsJanuary` (1 when current month is January)  
- `IsFebruary` (1 when current month is February)  
- `IsMarch` (1 when current month is March)  
- `IsApril` (1 when current month is April)  
- `IsMay` (1 when current month is May)  
- `IsJune` (1 when current month is June)  
- `IsJuly` (1 when current month is July)  
- `IsAugust` (1 when current month is August)  
- `IsSeptember` (1 when current month is September)  
- `IsOctober` (1 when current month is October)  
- `IsNovember` (1 when current month is November)  
- `IsDecember` (1 when current month is December)  



### Day-of-week CVars

- `IsMonday` (1 when current weekday is Monday)  
- `IsTuesday` (1 when current weekday is Tuesday)  
- `IsWednesday` (1 when current weekday is Wednesday)  
- `IsThursday` (1 when current weekday is Thursday)  
- `IsFriday` (1 when current weekday is Friday)  
- `IsSaturday` (1 when current weekday is Saturday)  
- `IsSunday` (1 when current weekday is Sunday)  



### Time-of-day state CVars

- `IsMorning` (1 during dawn-to-noon morning window)  
- `IsDaytime` (1 during daytime window before dusk)  
- `IsNighttime` (1 during nighttime window)  



### Date-key CVars

- `Is{MonthName}{Day}` (example: `IsMarch22`, `IsDecember25`)  
- `DateMMDD` (example: `Date0322`, `Date1225`)  



### 🌙 Lunar Cycle System

- `LunarDay` — Day number in current lunar month  
- `LunarMonth` — Lunar month index in repeating cycle  
- `LunarPhase7` — Coarse moon phase bucket (0–6)  
- `LunarPhase01` — Continuous moon phase (0.0–1.0)  
- `MoonAgeDays` — Days since last new moon  
- `LunarSynodicDays` — Synodic month length constant  



### 🌑 Lunar Event & Trigger System

- `LunarNearNewMoon` — 1 when near configured new-moon window  
- `IsLunar1` to `IsLunar12` — Monthly lunar bucket flags  



### 🧭 Lunisolar Calendar System

- `LunarUseLunisolarMonths` — Enables lunisolar calendar mode  
- `LunisolarYear` — Computed lunisolar year index  
- `LunisolarMonthNumber` — Computed lunisolar month number  
- `LunisolarIsLeapMonth` — 1 when current month is leap month  
- `LunisolarLeapMonthIndex` — Leap month slot index  
- `LunisolarMonthId` — Monotonic lunisolar month ID  
- `LunisolarMonthDay` — Day number in current lunisolar month  
- `LunisolarMonthLength` — Month length (29 or 30 days)   


### Lunar tuning CVars

- `LunarEpochShiftDays` (phase offset in days for lunar cycle alignment)  
- `LunarNewMoonWindowDays` (half-window size in days used for near new moon checks)  


### Blood moon CVars

- `BloodMoonTonight` Active blood moon state flag (1 = active, 0 = inactive) 
- `LunarBloodMoonTonight`  Compatibility alias for `BloodMoonTonight`  
- `LunarBloodMoonStrength` (lunar blood moon intensity scaling factor)  
- Runtime range is `0.0` to `1.0` (auto calculated by the mod, not normally set manually)  
- `0.0` = outside lunar blood moon window, `1.0` = peak strength (center of full-moon run)  
- Practical thresholds for XML tuning: `>=0.2` any activity, `>=0.5` medium+, `>=0.8` peak nights  



### Weather CVars

- `WeatherTemp` (current ambient temperature value)  
- `WeatherWind` (current wind strength/speed)  
- `WeatherRain` (current rain intensity)  
- `WeatherSnow` (current snow intensity)  
- `WeatherFog` (current fog density value)  
- `CloudThickness` (current cloud coverage thickness value)  
- `IsStormActive` (1 when active storm state is detected)  



### Biome CVars

- `IsPineForest` (1 when player is in pine forest biome)  
- `IsDesert` (1 when player is in desert biome)  
- `IsBurntForest` (1 when player is in burnt forest biome)  
- `IsSnow` (1 when player is in snow biome)  
- `IsWasteland` (1 when player is in wasteland biome)  




### UI / gameplay CVars

- `CrosshairEnable` (1 enables crosshair, 0 hides crosshair (0 = default))  
- `ui_disable_dimming` (1 disables night UI dimming system)  
- `ui_night_bg_opacity` (target nighttime background opacity)  
- `ui_night_fg_opacity` (target nighttime foreground opacity)  




## Compass binding keys

- `season`  
- `dayseason`  
- `calendar`  
- `calendarfull`  
- `calendarcompact`  
- `monthname`  
- `monthshort`  
- `yearnumber`  
- `dayofmonth`  
- `dayofyear`  
- `weekday`  
- `weekdayshort`  
- `rain`  
- `snow`  
- `storm`  
- `rainiconcolor`  
- `snowiconcolor`  
- `stormiconcolor`  
- `daycolor`  
- `lunarday`  
- `lunarmonth`  
- `lunarcompact`  
- `lunarphase7`  
- `moonphase`  
- `moonphasename`  
- `moonphaseshort`  
- `lunarphase01`  
- `moonagedays`  
- `lunarnearnewmoon`  
- `moonphasecolor`  
- `fullmoonforecast`  
- `fullmoondaysmonth`  


If you like my work, support me on: https://www.paypal.com/paypalme/zipp00

