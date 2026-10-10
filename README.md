# SM64 Island 1.1 TAS files

Input files (`.m64`) and savestates (`.st`) for the individual-star TASes of **Super Mario 64 Island 1.1**
(30 Stars project). Times follow SM64LuaRedux's timer (fade-in to star dance).

## Files: standard savestates and names (2026-10-08)

Every TAS now starts from a **standard savestate** and is named `<state>.<star>.<time>.m64`. Mupen pairs a movie
with the `.st` named like its first part (`lp_1.bully.15_83.m64` plays from `lp_1.st`).

- **Level states:** `<course>_<act>.st` (`bom_1`, `sk_6`, `lp_1`, `wjt_2`, ...), plus `sa`, `bs` and `ba` (Secret
  Area, the Bowser stage, the Bowser arena), which have no act select.
  - Each sits on the act select's first frame: the movie presses Start on input 26, the first input the menu
    accepts, and the level loads 17 frames later.
  - Every state has the 30-star save (no star-count text boxes) and the act's cursor already set.
  - Single-star movies use ideal RNG: a state's RNG seed may be set for the movie that needs it (`bom_6.st`: seed
    29428 for the red coins + 100c clone; `sk_6.st`: seed 18125 for the 8 Red Coins Again + 100c). The full run's
    RNG comes from the stitched run instead.
- **Castle states:** `castle_start` (file load), `castle_spawn1_star`, `castle_spawn2_star`, `castle_spawn1_death`.
  - Each sits on the castle's first frame. `castle_start` sits one frame earlier, because the castle's load frame
    already takes input (the dive).
  - Castle movements are named `<castle state>.to_<course>.<N>f.m64`.
- **Every movie ends on the frame before the next level's first frame.** So movies append one after another with
  no edits, ready for stitching the full run.
- **Times:** SM64LuaRedux's timer, unchanged by the rebase: every movie was checked frame by frame in Mupen against
  the movie it replaces.
- **`archive/<folder>/`:** superseded times, the old-format originals and their savestates, unchanged.
- **`castle-movement/poweron.169f.m64`:** power-on to `castle_start` (off the sheet; needed for stitching).

## Playing a movie

- Use Mupen64 (mupen64-rr-lua 1.5.x) with the Super Mario 64 Island 1.1 ROM.
- Keep each `.m64` in the same folder as its `.st`. Mupen plays `a.b.c.m64` from `a.b.c.st`, else `a.b.st`, else `a.st`,
  so several movies share one savestate (e.g. all `lp_1.*.m64` start from `lp_1.st`).

## Notes

- **The 8 Red Coins Again + 100c**: two records, and only the old one needs SM64Lua's swim button.
  - `archive/2-sky-kingdom/100c.skykingdom.swim_baked.m64` (90.27) was recorded with SM64Lua's swim on and desyncs without it. Its copy has
    those A presses written into the inputs, so it plays on its own. **Turn SM64Lua's swim button off** for it.
  - `sk_6.reds100c.79_30.m64` (79.30, 2026-10-10): 3.80 s faster than the 83.10 (228 VIs), on Kieran's macro changes.
    - Both whomps on the way are killed with the fast 10-coin method: Mario stands at a corner of the lying whomp where
      Island's 4× level bounds make its back's floor reach past its walls, and alternates jumps that land on the back in
      the same frame with frames off it (a stand-on coin every 2 frames), then ground pounds for the other 5. The
      second whomp's kill starts straight out of a long jump's land stop at its back's 1×1 north-west corner cell.
    - The climb onto the second whomp's platform is a glitchy wall kick off the y 320 hexagon step; red 4 is taken in a
      dive on a faster run to BLJ 2: the rollout stops on the house's east wall and drifts back west, and after the
      quick turn the first long jump stops on its west wall (fv 0), which starts the BLJ.
    - The BLJ's speed is stopped at red 5 by walking off the platform's edge and landing back (Kieran's idea), not a
      jump; red 5's rim is a dive grind (re-fitted on that stop, with fuller quarter steps and no braking frame), and red 6 is an out-and-back with the first two blue coins taken on the way out (Kieran's jump, dive and rollout
      line) and a turn-around side flip at red 6; a speed kick (A held) on the way back to red 7's slope.
    - Red 7 to red 8 was modelled (the butt slide air's turn, the freefall, the speed kick, the walk-turn) and searched
      in the exact simulator: the butt slide air turns right then slightly left so the freefall faces 540 units more
      west, and the speed kick strafes south, so it lands nearer red 8; the jumps onto red 8's ledge are re-fitted so
      the 100-coin star is grabbed at the same spot (the final trip unchanged), one frame earlier.
    - The archway coin line is skipped (the second whomp's 5 extra coins replace it); red 7, the bridge line, and red 8
      as the 100th coin, then a triple jump grabs the 100-coin star. The camera is turned the other way for the red 8
      approach, so the dance ends facing west and the final trip (re-searched) starts with route 2's punch. The
      100-coin star's save prompt is answered "No" (saving lags 21 VIs).
    - It plays from `sk_6.st` with an ideal entry RNG seed (gRandomSeed16 = 18125), which makes every whomp coin land.
      Older: the 79.33, the 79.47, the 79.53, the 79.63, the 79.83 and the 80.18 in `archive/2-sky-kingdom/seed18125/`, the 83.10 in
      `seed46221/` (seed 46221), the 83.73 in `seed41202/`, and the 85.73
      and 85.20 with the archived `sk_6.st` (seed 7556).
    - Recorded without swim; it needs nothing special. Optimisation is still in progress. Redux timer 4758 VIs =
      79.30, red coin star dance on sample 2424 (verified in Mupen).
- **Find the 8 Red Coins + 100c** (`bom_6.reds100c.49_10.m64`, 2026-10-09): 93 frames faster than the 52.20 and 6
  faster than the 49.30 (the older movies are in `archive/1-bob-omb-mountain/`; the 49.30's state is
  `archive/1-bob-omb-mountain/bom_6.49_30.st`). It clones the red coin star: Mario
  grabs bob-omb #3, throws it onto the wedge north of R8's pillar, punches it as it explodes so he holds its vacant
  slot, and takes R8 and the bob-omb's own coin as the 100th four frames apart (Double Star Spawn), so the red coin
  star loads into the slot he holds and is collected right after the 100c dance. It plays from the red coin act's
  state `bom_6.st` with an ideal entry RNG seed (gRandomSeed16 = 29428; single stars use ideal RNG).
  The viewing camera (redone 2026-10-09 after a review) keeps Mario in view: R (Mario cam) for the dive through the
  first house's window and through the blue house, with C held to steer it round the stair blocks; 8-direction turns
  after the blue house (its roof, then the mountain the camera sat inside) and for the clone setup (the stumps), back to
  the original angle after the 100c time stop. Every stick is re-aimed to the camera it reads (in the Mario cam to the
  nearest equivalent direction), and every coin, the star and the timing are unchanged.
  Redux timer 2946 VIs = 49.10, star dance exit on sample 1517.
- **Bowser Stage** (`bs.stage.12_13.m64`, from `bs.st`) and **Throws** (`ba.throws.36_30.m64`, from `ba.st`)
  are separate movies since 2026-10-08: the stage ends on the frame before the arena loads, and the fight
  starts there. The old combined movies (`bowser_stage*.m64`) are in `archive/battle-of-the-hope/`.
  Bowser Stage is timed from SM64Lua's timer start to the first frame Mario's action is DISAPPEARED
  (entering the pipe, not the later level change); Throws from the timer's restart on the arena fade-in to
  the frame Mario enters DISAPPEARED from the Grand Star warp.
- **Hide in the Mountain → DSG** (`bom_5.mountain_dsg.17_43.m64`): the death star glitch, for the full-game TAS. Timed
  from the fade-in to the first frame of the death fade (sample 540), counting that frame (17.40 if the timer
  stops on it instead; DSG timing is a convention). Slower than the 14.60 on
  its own, but Mario has control in the castle 26 frames sooner (a death exit instead of the star dance and course
  exit). Built programmatically (the out-of-bounds death is sub-unit precise), so it has no rerecord count of its
  own; the header still carries the 14.60 movie's.
- `castle-movement/`: level re-entries. Timed from the first frame of control after the exit to the painting entry.
  `sky kingdom re-enter.m64` is unfinished: its savestate is the first star, so the 1-star text box plays at the exit
  and the movie ends with Mario idle.
  - `archive/castle-movement/start.to sk.68f.m64` + `archive/castle-movement/start.st` (wowpow): Start → Sky Kingdom (the file-load spawn), 68 frames from the file-load spawn (the first
    non-white frame) to the warp (the first DISAPPEARED frame).
  - `castle_start.to_sk.67f.m64` + `castle_start.st`: Start → Sky Kingdom, 2.23 (134 VIs on SM64LuaRedux's timer; wowpow's route
    is 136 from the same start). It's wowpow's route, re-aimed: a steeper turn and some long-jump drift cross the
    alcove edge a frame sooner. Built programmatically, so it has no rerecord count of its own; the header keeps
    wowpow's.
    - `archive/castle-movement/lobby.st` is the state one frame before the castle loads. Start new file-load movies from it. The load frame
      itself already takes input, so a dive is possible on it.
    - `poweron.169f.m64` (power-on) is how `archive/castle-movement/lobby.st` is made since 2026-10-08: Start on each menu's first
      accepting frame (the title takes it from input 117, the file select on its first frame, 135), so the castle
      loads a frame (2 VIs) sooner than with `archive/castle-movement/poweron.lobby.169f.m64`, which pressed Start on every even sample and
      waited for 118 at the title. The Start movies play identically from the new `archive/castle-movement/lobby.st`.
  - `castle_start.to_bom.69f.m64` + `castle_start.st`: Start → Bob-omb Mountain, 2.30 (138 VIs). The same opening (dive, rollout,
    walking turn, long jump), touching the warp just after landing on its platform. The warp is about 110 units
    farther from the spawn than Sky Kingdom's, so it takes 2 frames more. Built programmatically.
  - `castle_start.to_sa.74f.m64` + `castle_start.st`: Start → Secret Area, 2.47 (148 VIs), the same time as Toriku and wowpow's.
    The warp sits at the back of an alcove 133 units above the lobby floor, so it takes two long jumps; the second
    drifts sideways to get around the Toad standing next to the alcove (its push knocks Mario off course).
    Built programmatically.
  - `archive/castle-movement/spawn1.to_sk.54f.m64` + `archive/castle-movement/spawn1.st`: Spawn 1 → Sky Kingdom (= the Sky Kingdom re-entry), 1.80 (54 frames, first
    idle frame to the warp). Two long jumps; the second touches the warp in the air.
    - `archive/castle-movement/spawn1.st` is `sky kingdom re-enter.st` with one RAM value changed (prevNumStarsForDialog = numStars), so
      the 1-star text box doesn't play. Any first-room star exit lands Mario in the same state.
    - It's written in Mupen 1.4's gzip format, because Mupen can't save a state from before a movie's first frame;
      1.5 loads it.
    - Built programmatically, so it has no rerecord count of its own.
  - `castle_spawn1_star.to_sk.53f.m64` + `castle_spawn1_star.st`: Spawn 1 → Sky Kingdom, 1.77 (53 frames), a frame under the 54. It opens
    with Toriku's punch start (B at idle on the control frame: the punch sets speed 10 at once, and walking on the
    next frame keeps it), then 7 walking frames turning toward the west, a long jump and a second long jump one
    frame after landing. Built programmatically.
  - `archive/castle-movement/spawn1.to_sa.61f.m64` + `archive/castle-movement/spawn1.st`: Spawn 1 → Secret Area, 2.03 (61 frames, first idle frame to the warp).
    Three walking frames, a long jump, and a second long jump on the landing frame that rises into the alcove.
    Built programmatically.
  - `castle_spawn1_star.to_sa.60f.m64` + `castle_spawn1_star.st`: Spawn 1 → Secret Area, 2.00 (60 frames), a frame under the 61 with the
    punch start, then 4 walking frames, a long jump and a second long jump on the landing frame. Built
    programmatically.
  - Spawn 1 after the death exit (the DSG): `archive/castle-movement/spawn1d.st` is the state one frame before the castle loads after
    `1-bob-omb-mountain/star5.dsg.17_40.m64`'s death; Mario lands at (−8.54, −380, 463.92) facing 0x7F49 and has
    control 112 frames later. Timed like the re-entries (first idle frame to the warp). Built programmatically.
    - `castle_spawn1_death.to_sk.53f.m64`: → Sky Kingdom, 1.77 (no punch: Mario faces south, and the landing is 8.5 units closer).
    - `castle_spawn1_death.to_bom.56f.m64`: → Bob-omb Mountain, 1.87.
    - `castle_spawn1_death.to_sa.61f.m64`: → Secret Area, 2.03.
  - BLJs past the 12-star door, from a Spawn 1 star exit (`archive/castle-movement/spawn1blj.st` = Toriku's savestate; control on sample 160):
    - `archive/castle-movement/spawn1blj.to_lp.106f.m64` (Toriku): Spawn 1 → Lava Plaza, 3.53. A punch start and a long jump onto the stairs,
      a turnaround, a backward long jump into the low tunnel under the hallway railing, six BLJ presses pinned there,
      and a hyperspeed launch across room 1 through the room-1 / room-2 wall (a frame-start wall push at x ≈ 1180, not
      the 12-star door). His original route, as he made it (RCP lag factor set to 0).
    - `archive/castle-movement/spawn1blj.to_lp.97f.m64` (MiloboloWF, Toriku): Spawn 1 → Lava Plaza, 3.23 (97 frames). Toriku's route with
      MiloboloWF's long-jump start (crouch slide on the second frame after the punch, long jump on the third), neutral
      sticks on the stair landing so the turnaround happens on a lower step, a backward long jump that lands a frame
      sooner, neutral sticks between the BLJ presses (holding the stick costs launch speed) and a launch a frame
      sooner at −245. Built programmatically (the same time as MiloboloWF's own movie).
    - `archive/castle-movement/spawn1blj.to_lp.96f.m64` (Kieran, Toriku): Spawn 1 → Lava Plaza, 3.20 (96 frames). Kieran's slide-kick start
      (punch, slide kick east, rollout, dive: idle on the step a frame sooner than the long-jump start) on Toriku's
      route. Kieran's movie held the BLJ pin with off-axis sticks and launched at −232; here only the first press is
      off-axis (12°, enough to stay pinned) and the other presses are straight back, so the launch reaches −245.6 and
      the flight takes 8 frames instead of 9. Built programmatically.
    - `castle_spawn1_star.to_lp.95f.m64` (Kieran, Toriku): Spawn 1 → Lava Plaza, 3.17 (95 frames). The same start; the backward
      long jump is strained sideways (north-west, then south-east, at the angle that keeps its speed) so it lands
      within one slide frame of the pin, a frame sooner; the first press 22° off straight back holds the pin, the rest
      go straight back, launch at −243.7. Robust to the camera. Built programmatically.
    - `archive/castle-movement/spawn1blj.to_wjt.107f.m64` (Toriku's inputs, mirrored): Spawn 1 → Walljump Training, 3.57. His Lava Plaza
      inputs mirrored across the lobby's centre, each stick refitted to the camera, which isn't symmetric.
    - `archive/castle-movement/spawn1blj.to_wjt.99f.m64` (MiloboloWF, Toriku): Spawn 1 → Walljump Training, 3.30 (99 frames). A 98-frame
      Lava Plaza plan of the same kind, mirrored to the west railing; the Walljump warp is farther, so a frame more.
      Built programmatically.
    - `archive/castle-movement/spawn1blj.to_wjt.97f.m64` (Kieran, Toriku): Spawn 1 → Walljump Training, 3.23 (97 frames). Kieran's slide-kick
      start mirrored to the west side (the user's idea), pinned under the west railing with a single slide frame,
      straight-back presses, launch at −246. Built programmatically.
    - `castle_spawn1_star.to_wjt.96f.m64` (Kieran, Toriku): Spawn 1 → Walljump Training, 3.20 (96 frames). The same, with the
      approach re-aimed on the west stairs (the slide kick's dive and rollout land on the west banister) and a
      launch at −245 with no friction frame. Built programmatically.
  - `archive/castle-movement/spawn2.to_bowser.86f.m64` + `archive/castle-movement/spawn2.st` (Kieran): Spawn 2 → Battle of the Hope, 2.87 (86 frames, first idle frame
    to the pipe). A backflip toward the 30-star doors, a ledge grab and soft bonk that clip past the door, then a
    jump kick into the pipe.
  - `archive/castle-movement/spawn2.to_bowser.84f.m64` + `archive/castle-movement/spawn2.st` (Kieran): Spawn 2 → Battle of the Hope, 2.80 (84 frames). Kieran's door
    clip unchanged, then a punch, a jump and a jump kick into the pipe's side wall instead of over its rim: falling
    through y 330 just past the ~50-thick wall, the two faces' pushes add up and put Mario inside, below the rim.
    Built programmatically.
  - `castle_spawn2_star.to_bs.83f.m64` + `castle_spawn2_star.st` (Kieran): Spawn 2 → Battle of the Hope, 2.77 (83 frames). The same door
    clip, then the pipe's south vertex: the jump kick's first quarter step on its second-to-last frame lands exactly
    on x = 92.0, the edge the pipe's two south outer faces share, where both faces push and Mario is carried inside a
    frame sooner. The two sticks were solved in the emulator against the live camera (float-exact), so the movie is a
    one-off, not a re-runnable recipe. Built programmatically.
  - `castle_spawn2_star.to_wjt.47f.m64` + `castle_spawn2_star.st`: Spawn 2 → Walljump Training, 1.57 (47 frames, first idle frame to the
    warp), one frame under the Lava Plaza re-entry (the Walljump warp is 72 units closer to Spawn 2). Three walking
    frames and two long jumps, like `castle_spawn2_star.to_lp.48f.m64`. `archive/castle-movement/spawn2.st` is a copy of `archive/castle-movement/re-enter lava plaza.st` (the
    room-2 exit, no text box), named so Mupen pairs it with the `spawn2.*` movies. Built programmatically.

## Stars

| Star | Time | .m64 | .st |
|---|---|---|---|
| Big Bob-Omb Fight Back | 38.27 | [bom_1.king.38_27.m64](1-bob-omb-mountain/bom_1.king.38_27.m64) | [bom_1.st](1-bob-omb-mountain/bom_1.st) |
| Hide in the Mountain | 14.6 | [bom_5.mountain.14_60.m64](1-bob-omb-mountain/bom_5.mountain.14_60.m64) | [bom_5.st](1-bob-omb-mountain/bom_5.st) |
| Hide in the Mountain → DSG (full run) | 17.43 | [bom_5.mountain_dsg.17_43.m64](1-bob-omb-mountain/bom_5.mountain_dsg.17_43.m64) | [bom_5.st](1-bob-omb-mountain/bom_5.st) |
| Climb the House | 6.13 | [bom_1.climb.6_13.m64](1-bob-omb-mountain/bom_1.climb.6_13.m64) | [bom_1.st](1-bob-omb-mountain/bom_1.st) |
| Fly with Fly Guy | 18.13 | [bom_5.flyguy.18_13.m64](1-bob-omb-mountain/bom_5.flyguy.18_13.m64) | [bom_5.st](1-bob-omb-mountain/bom_5.st) |
| The Locked Hole | 5.43 | [bom_5.locked.5_43.m64](1-bob-omb-mountain/bom_5.locked.5_43.m64) | [bom_5.st](1-bob-omb-mountain/bom_5.st) |
| Find the 8 Red Coins + 100c | 49.1 | [bom_6.reds100c.49_10.m64](1-bob-omb-mountain/bom_6.reds100c.49_10.m64) | [bom_6.st](1-bob-omb-mountain/bom_6.st) |
| The Son of Whomp King | 31.77 | [sk_1.whompking.31_77.m64](2-sky-kingdom/sk_1.whompking.31_77.m64) | [sk_1.st](2-sky-kingdom/sk_1.st) |
| At the Other End of the Kingdom | 17.33 | [sk_1.otherend.17_33.m64](2-sky-kingdom/sk_1.otherend.17_33.m64) | [sk_1.st](2-sky-kingdom/sk_1.st) |
| In the Wall | 16.97 | [sk_1.inthewall.16_97.m64](2-sky-kingdom/sk_1.inthewall.16_97.m64) | [sk_1.st](2-sky-kingdom/sk_1.st) |
| Listen to What the Bob-omb Has to Say to You | 10.23 | [sk_1.listen.10_23.m64](2-sky-kingdom/sk_1.listen.10_23.m64) | [sk_1.st](2-sky-kingdom/sk_1.st) |
| The Four Pillars | 19.6 | [sk_1.pillars.19_60.m64](2-sky-kingdom/sk_1.pillars.19_60.m64) | [sk_1.st](2-sky-kingdom/sk_1.st) |
| The 8 Red Coins Again + 100c | 79.33 | [sk_6.reds100c.79_33.m64](2-sky-kingdom/sk_6.reds100c.79_33.m64) | [sk_6.st](2-sky-kingdom/sk_6.st) |
| Burn the Big Bully | 15.83 | [lp_1.bully.15_83.m64](3-lava-plaza/lp_1.bully.15_83.m64) | [lp_1.st](3-lava-plaza/lp_1.st) |
| In the Corner | 14.13 | [lp_1.corner.14_13.m64](3-lava-plaza/lp_1.corner.14_13.m64) | [lp_1.st](3-lava-plaza/lp_1.st) |
| At the Top of the Volcano | 11.83 | [lp_1.volcano.11_83.m64](3-lava-plaza/lp_1.volcano.11_83.m64) | [lp_1.st](3-lava-plaza/lp_1.st) |
| The Mysterious "S" | 13.13 | [lp_1.mysterious_s.13_13.m64](3-lava-plaza/lp_1.mysterious_s.13_13.m64) | [lp_1.st](3-lava-plaza/lp_1.st) |
| The Wooden Platform | 7.63 | [lp_1.platform.7_63.m64](3-lava-plaza/lp_1.platform.7_63.m64) | [lp_1.st](3-lava-plaza/lp_1.st) |
| You Know What Red Coins + 100c | 48.9 | [lp_1.reds100c.48_90.m64](3-lava-plaza/lp_1.reds100c.48_90.m64) | [lp_1.st](3-lava-plaza/lp_1.st) |
| At the Top of the Tower | 20.2 | [wjt_1.toptower.20_20.m64](4-walljump-training/wjt_1.toptower.20_20.m64) | [wjt_1.st](4-walljump-training/wjt_1.st) |
| At the Bottom of the Tower | 17.4 | [wjt_2.bottomtower.17_40.m64](4-walljump-training/wjt_2.bottomtower.17_40.m64) | [wjt_2.st](4-walljump-training/wjt_2.st) |
| Hide in the 2nd Platform | 13.83 | [wjt_1.platform2.13_83.m64](4-walljump-training/wjt_1.platform2.13_83.m64) | [wjt_1.st](4-walljump-training/wjt_1.st) |
| Hide in the 4th Platform | 16.27 | [wjt_1.platform4.16_27.m64](4-walljump-training/wjt_1.platform4.16_27.m64) | [wjt_1.st](4-walljump-training/wjt_1.st) |
| Hide in the 3rd Platform | 19.3 | [wjt_1.platform3.19_30.m64](4-walljump-training/wjt_1.platform3.19_30.m64) | [wjt_1.st](4-walljump-training/wjt_1.st) |
| You Already Know Red Coins + 100c | 64.73 | [wjt_2.reds100c.64_73.m64](4-walljump-training/wjt_2.reds100c.64_73.m64) | [wjt_2.st](4-walljump-training/wjt_2.st) |
| Red Coins | 22.4 | [sa.reds.22_40.m64](secret-area/sa.reds.22_40.m64) | [sa.st](secret-area/sa.st) |
| Parkour | 9.97 | [sa.parkour.9_97.m64](secret-area/sa.parkour.9_97.m64) | [sa.st](secret-area/sa.st) |
| Bowser Stage | 12.13 | [bs.stage.12_13.m64](battle-of-the-hope/bs.stage.12_13.m64) | [bs.st](battle-of-the-hope/bs.st) |
| Throws | 36.3 | [ba.throws.36_30.m64](battle-of-the-hope/ba.throws.36_30.m64) | [ba.st](battle-of-the-hope/ba.st) |
