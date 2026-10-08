# SM64 Island 1.1 TAS files

Input files (`.m64`) and savestates (`.st`) for the individual-star TASes of **Super Mario 64 Island 1.1**
(30 Stars project). Times follow SM64LuaRedux's timer (fade-in to star dance).

## Playing a movie

- Use Mupen64 (mupen64-rr-lua 1.5.x) with the Super Mario 64 Island 1.1 ROM.
- Keep each `.m64` in the same folder as its `.st`. Mupen plays `a.b.c.m64` from `a.b.c.st`, else `a.b.st`, else `a.st`,
  so several movies share one savestate (e.g. all `lp_course3_3.*.m64` start from `lp_course3_3.st`).

## Notes

- **The 8 Red Coins Again + 100c**: two records, and only the old one needs SM64Lua's swim button.
  - `100c.skykingdom.swim_baked.m64` (90.27) was recorded with SM64Lua's swim on and desyncs without it. Its copy has
    those A presses written into the inputs, so it plays on its own. **Turn SM64Lua's swim button off** for it.
  - `100c.skykingdom.swim_baked.85_73.m64` (85.73) is a new route, recorded without swim; the `swim_baked` in its name
    is only inherited from the file it was branched from. It needs nothing special. Not optimised yet. Redux timer
    5144 VIs = 85.73, star dance on sample 2650 (verified 2026-10-06 in Mupen with no SM64Lua loaded).
- **Bowser Stage** and **Throws** are one movie (`bowser_stage.m64`): the stage, then the fight.
  `bowser_stage.throws.36_27.m64` is the same stage with the faster fight. `bowser_stage.12_10.m64` has both the
  faster stage (no extra idle frame) and the faster fight. Bowser Stage is timed from SM64Lua's timer start to the
  first frame Mario's action is DISAPPEARED (entering the pipe, not the later level change); Throws from the timer's restart on the arena fade-in to the frame
  Mario enters DISAPPEARED from the Grand Star warp.
- **Hide in the Mountain → DSG** (`star5.dsg.17_40.m64`): the death star glitch, for the full-game TAS. Timed
  from the fade-in to the first frame of the death fade (sample 540), counting that frame (17.40 if the timer
  stops on it instead; DSG timing is a convention). Slower than the 14.60 on
  its own, but Mario has control in the castle 26 frames sooner (a death exit instead of the star dance and course
  exit). Built programmatically (the out-of-bounds death is sub-unit precise), so it has no rerecord count of its
  own; the header still carries the 14.60 movie's.
- `castle-movement/`: level re-entries. Timed from the first frame of control after the exit to the painting entry.
  `sky kingdom re-enter.m64` is unfinished: its savestate is the first star, so the 1-star text box plays at the exit
  and the movie ends with Mario idle.
  - `start.to sk.68f.m64` + `start.st` (wowpow): Start → Sky Kingdom (the file-load spawn), 68 frames from the file-load spawn (the first
    non-white frame) to the warp (the first DISAPPEARED frame).
  - `lobby.to_sk.67f.m64` + `lobby.st`: Start → Sky Kingdom, 2.23 (134 VIs on SM64LuaRedux's timer; wowpow's route
    is 136 from the same start). It's wowpow's route, re-aimed: a steeper turn and some long-jump drift cross the
    alcove edge a frame sooner. Built programmatically, so it has no rerecord count of its own; the header keeps
    wowpow's.
    - `lobby.st` is the state one frame before the castle loads. Start new file-load movies from it. The load frame
      itself already takes input, so a dive is possible on it.
    - `poweron.lobby.168f.m64` (power-on) is how `lobby.st` is made since 2026-10-08: Start on each menu's first
      accepting frame (the title takes it from input 117, the file select on its first frame, 135), so the castle
      loads a frame (2 VIs) sooner than with `poweron.lobby.169f.m64`, which pressed Start on every even sample and
      waited for 118 at the title. The Start movies play identically from the new `lobby.st`.
  - `lobby.to_bob.69f.m64` + `lobby.st`: Start → Bob-omb Mountain, 2.30 (138 VIs). The same opening (dive, rollout,
    walking turn, long jump), touching the warp just after landing on its platform. The warp is about 110 units
    farther from the spawn than Sky Kingdom's, so it takes 2 frames more. Built programmatically.
  - `lobby.to_sa.74f.m64` + `lobby.st`: Start → Secret Area, 2.47 (148 VIs), the same time as Toriku and wowpow's.
    The warp sits at the back of an alcove 133 units above the lobby floor, so it takes two long jumps; the second
    drifts sideways to get around the Toad standing next to the alcove (its push knocks Mario off course).
    Built programmatically.
  - `spawn1.to_sk.54f.m64` + `spawn1.st`: Spawn 1 → Sky Kingdom (= the Sky Kingdom re-entry), 1.80 (54 frames, first
    idle frame to the warp). Two long jumps; the second touches the warp in the air.
    - `spawn1.st` is `sky kingdom re-enter.st` with one RAM value changed (prevNumStarsForDialog = numStars), so
      the 1-star text box doesn't play. Any first-room star exit lands Mario in the same state.
    - It's written in Mupen 1.4's gzip format, because Mupen can't save a state from before a movie's first frame;
      1.5 loads it.
    - Built programmatically, so it has no rerecord count of its own.
  - `spawn1.to_sk.53f.m64` + `spawn1.st`: Spawn 1 → Sky Kingdom, 1.77 (53 frames), a frame under the 54. It opens
    with Toriku's punch start (B at idle on the control frame: the punch sets speed 10 at once, and walking on the
    next frame keeps it), then 7 walking frames turning toward the west, a long jump and a second long jump one
    frame after landing. Built programmatically.
  - `spawn1.to_sa.61f.m64` + `spawn1.st`: Spawn 1 → Secret Area, 2.03 (61 frames, first idle frame to the warp).
    Three walking frames, a long jump, and a second long jump on the landing frame that rises into the alcove.
    Built programmatically.
  - `spawn1.to_sa.60f.m64` + `spawn1.st`: Spawn 1 → Secret Area, 2.00 (60 frames), a frame under the 61 with the
    punch start, then 4 walking frames, a long jump and a second long jump on the landing frame. Built
    programmatically.
  - Spawn 1 after the death exit (the DSG): `spawn1d.st` is the state one frame before the castle loads after
    `1-bob-omb-mountain/star5.dsg.17_40.m64`'s death; Mario lands at (−8.54, −380, 463.92) facing 0x7F49 and has
    control 112 frames later. Timed like the re-entries (first idle frame to the warp). Built programmatically.
    - `spawn1d.to_sk.53f.m64`: → Sky Kingdom, 1.77 (no punch: Mario faces south, and the landing is 8.5 units closer).
    - `spawn1d.to_bob.56f.m64`: → Bob-omb Mountain, 1.87.
    - `spawn1d.to_sa.61f.m64`: → Secret Area, 2.03.
  - BLJs past the 12-star door, from a Spawn 1 star exit (`spawn1blj.st` = Toriku's savestate; control on sample 160):
    - `spawn1blj.to_lp.106f.m64` (Toriku): Spawn 1 → Lava Plaza, 3.53. A punch start and a long jump onto the stairs,
      a turnaround, a backward long jump into the low tunnel under the hallway railing, six BLJ presses pinned there,
      and a hyperspeed launch across room 1 through the room-1 / room-2 wall (a frame-start wall push at x ≈ 1180, not
      the 12-star door). His original route, as he made it (RCP lag factor set to 0).
    - `spawn1blj.to_lp.97f.m64` (MiloboloWF, Toriku): Spawn 1 → Lava Plaza, 3.23 (97 frames). Toriku's route with
      MiloboloWF's long-jump start (crouch slide on the second frame after the punch, long jump on the third), neutral
      sticks on the stair landing so the turnaround happens on a lower step, a backward long jump that lands a frame
      sooner, neutral sticks between the BLJ presses (holding the stick costs launch speed) and a launch a frame
      sooner at −245. Built programmatically (the same time as MiloboloWF's own movie).
    - `spawn1blj.to_wjt.107f.m64` (Toriku's inputs, mirrored): Spawn 1 → Walljump Training, 3.57. His Lava Plaza
      inputs mirrored across the lobby's centre, each stick refitted to the camera, which isn't symmetric.
    - `spawn1blj.to_wjt.99f.m64` (MiloboloWF, Toriku): Spawn 1 → Walljump Training, 3.30 (99 frames). A 98-frame
      Lava Plaza plan of the same kind, mirrored to the west railing; the Walljump warp is farther, so a frame more.
      Built programmatically.
  - `spawn2.to_bowser.86f.m64` + `spawn2.st` (Kieran): Spawn 2 → Battle of the Hope, 2.87 (86 frames, first idle frame
    to the pipe). A backflip toward the 30-star doors, a ledge grab and soft bonk that clip past the door, then a
    jump kick into the pipe.
  - `spawn2.to_bowser.84f.m64` + `spawn2.st` (Kieran): Spawn 2 → Battle of the Hope, 2.80 (84 frames). Kieran's door
    clip unchanged, then a punch, a jump and a jump kick into the pipe's side wall instead of over its rim: falling
    through y 330 just past the ~50-thick wall, the two faces' pushes add up and put Mario inside, below the rim.
    Built programmatically.
  - `spawn2.to_wjt.47f.m64` + `spawn2.st`: Spawn 2 → Walljump Training, 1.57 (47 frames, first idle frame to the
    warp), one frame under the Lava Plaza re-entry (the Walljump warp is 72 units closer to Spawn 2). Three walking
    frames and two long jumps, like `re-enter lava plaza.m64`. `spawn2.st` is a copy of `re-enter lava plaza.st` (the
    room-2 exit, no text box), named so Mupen pairs it with the `spawn2.*` movies. Built programmatically.

## Stars

| Star | Time | .m64 | .st |
|---|---|---|---|
| Big Bob-Omb Fight Back | 38.27 | [bom_course1.king.38_27.m64](1-bob-omb-mountain/bom_course1.king.38_27.m64) | [bom_course1.st](1-bob-omb-mountain/bom_course1.st) |
| Hide in the Mountain | 14.6 | [star5.mountain.14_60.m64](1-bob-omb-mountain/star5.mountain.14_60.m64) | [star5.st](1-bob-omb-mountain/star5.st) |
| Hide in the Mountain → DSG (full run) | 17.43 | [star5.dsg.17_40.m64](1-bob-omb-mountain/star5.dsg.17_40.m64) | [star5.st](1-bob-omb-mountain/star5.st) |
| Climb the House | 6.13 | [bom_course1.climb.6_13.m64](1-bob-omb-mountain/bom_course1.climb.6_13.m64) | [bom_course1.st](1-bob-omb-mountain/bom_course1.st) |
| Fly with Fly Guy | 18.13 | [star5.flyguy.18_13.m64](1-bob-omb-mountain/star5.flyguy.18_13.m64) | [star5.st](1-bob-omb-mountain/star5.st) |
| The Locked Hole | 5.43 | [star5.locked.5_43.m64](1-bob-omb-mountain/star5.locked.5_43.m64) | [star5.st](1-bob-omb-mountain/star5.st) |
| Find the 8 Red Coins + 100c | 52.2 | [bom_course1.100c+reds.52_20.m64](1-bob-omb-mountain/bom_course1.100c%2Breds.52_20.m64) | [bom_course1.st](1-bob-omb-mountain/bom_course1.st) |
| The Son of Whomp King | 31.77 | [whompnew.31_77.m64](2-sky-kingdom/whompnew.31_77.m64) | [whompnew.st](2-sky-kingdom/whompnew.st) |
| At the Other End of the Kingdom | 17.33 | [inthewall_2.other_end_of_kingdom.17_33.m64](2-sky-kingdom/inthewall_2.other_end_of_kingdom.17_33.m64) | [inthewall_2.st](2-sky-kingdom/inthewall_2.st) |
| In the Wall | 16.97 | [inthewall_2.16_97.m64](2-sky-kingdom/inthewall_2.16_97.m64) | [inthewall_2.st](2-sky-kingdom/inthewall_2.st) |
| Listen to What the Bob-omb Has to Say to You | 10.23 | [listentowhatthebobombhastosaytoyou.10_23.m64](2-sky-kingdom/listentowhatthebobombhastosaytoyou.10_23.m64) | [listentowhatthebobombhastosaytoyou.st](2-sky-kingdom/listentowhatthebobombhastosaytoyou.st) |
| The Four Pillars | 19.6 | [fourpillars.19_60.m64](2-sky-kingdom/fourpillars.19_60.m64) | [fourpillars.st](2-sky-kingdom/fourpillars.st) |
| The 8 Red Coins Again + 100c | 85.73 | [100c.skykingdom.swim_baked.85_73.m64](2-sky-kingdom/100c.skykingdom.swim_baked.85_73.m64) | [100c.st](2-sky-kingdom/100c.st) |
| Burn the Big Bully | 15.83 | [lp_course3_3.burn_the_big_bully.15_83.m64](3-lava-plaza/lp_course3_3.burn_the_big_bully.15_83.m64) | [lp_course3_3.st](3-lava-plaza/lp_course3_3.st) |
| In the Corner | 14.13 | [lp_course3_3.in_the_corner.14_13.m64](3-lava-plaza/lp_course3_3.in_the_corner.14_13.m64) | [lp_course3_3.st](3-lava-plaza/lp_course3_3.st) |
| At the Top of the Volcano | 11.83 | [lp_course3_3.at_the_top_of_the_volcano.11_83.m64](3-lava-plaza/lp_course3_3.at_the_top_of_the_volcano.11_83.m64) | [lp_course3_3.st](3-lava-plaza/lp_course3_3.st) |
| The Mysterious "S" | 13.13 | [lp_course3_3.the_mysterious_s.13_13.m64](3-lava-plaza/lp_course3_3.the_mysterious_s.13_13.m64) | [lp_course3_3.st](3-lava-plaza/lp_course3_3.st) |
| The Wooden Platform | 7.63 | [lp_course3_2.the_wooden_platform.7_63.m64](3-lava-plaza/lp_course3_2.the_wooden_platform.7_63.m64) | [lp_course3_2.st](3-lava-plaza/lp_course3_2.st) |
| You Know What Red Coins + 100c | 48.9 | [lp_course3_2.reds+100c.48_90.m64](3-lava-plaza/lp_course3_2.reds%2B100c.48_90.m64) | [lp_course3_2.st](3-lava-plaza/lp_course3_2.st) |
| At the Top of the Tower | 20.2 | [wjt_course4_1.at_the_top_of_the_tower.pipe1_fastLJ2_kick4exit_clip.3f_faster.m64](4-walljump-training/wjt_course4_1.at_the_top_of_the_tower.pipe1_fastLJ2_kick4exit_clip.3f_faster.m64) | [wjt_course4_1.st](4-walljump-training/wjt_course4_1.st) |
| At the Bottom of the Tower | 17.4 | [wjt_course4_2.at_the_bottom_of_the_tower.pipe1_fastLJ2_kick4exit_clip.4f_faster.m64](4-walljump-training/wjt_course4_2.at_the_bottom_of_the_tower.pipe1_fastLJ2_kick4exit_clip.4f_faster.m64) | [wjt_course4_2.st](4-walljump-training/wjt_course4_2.st) |
| Hide in the 2nd Platform | 13.83 | [wjt_course4_1.hide_in_the_2nd_platform.DTpunch_directclip.14f_faster.m64](4-walljump-training/wjt_course4_1.hide_in_the_2nd_platform.DTpunch_directclip.14f_faster.m64) | [wjt_course4_1.st](4-walljump-training/wjt_course4_1.st) |
| Hide in the 4th Platform | 16.27 | [wjt_course4_1.hide_in_the_4th_platform.pipe1_fastLJ2_kick4exit_clip.3f_faster.m64](4-walljump-training/wjt_course4_1.hide_in_the_4th_platform.pipe1_fastLJ2_kick4exit_clip.3f_faster.m64) | [wjt_course4_1.st](4-walljump-training/wjt_course4_1.st) |
| Hide in the 3rd Platform | 19.3 | [wjt_course4_1.hide_in_the_3rd_platform.pipe1_fastLJ2_kick4exit_clip.3f_faster.m64](4-walljump-training/wjt_course4_1.hide_in_the_3rd_platform.pipe1_fastLJ2_kick4exit_clip.3f_faster.m64) | [wjt_course4_1.st](4-walljump-training/wjt_course4_1.st) |
| You Already Know Red Coins + 100c | 64.73 | [course4_100c.pipe1_diverollout_terraceDJ_reds34_638.11f_faster.3fend.m64](4-walljump-training/course4_100c.pipe1_diverollout_terraceDJ_reds34_638.11f_faster.3fend.m64) | [course4_100c.st](4-walljump-training/course4_100c.st) |
| Red Coins | 22.4 | [secretarea.reds.22_40.m64](secret-area/secretarea.reds.22_40.m64) | [secretarea.st](secret-area/secretarea.st) |
| Parkour | 9.97 | [secretarea1.box.9_97.m64](secret-area/secretarea1.box.9_97.m64) | [secretarea1.st](secret-area/secretarea1.st) |
| Bowser Stage | 12.1 | [bowser_stage.12_10.m64](battle-of-the-hope/bowser_stage.12_10.m64) | [bowser_stage.st](battle-of-the-hope/bowser_stage.st) |
| Throws | 36.27 | [bowser_stage.throws.36_27.m64](battle-of-the-hope/bowser_stage.throws.36_27.m64) | [bowser_stage.st](battle-of-the-hope/bowser_stage.st) |
