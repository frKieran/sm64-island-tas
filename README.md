# SM64 Island 1.1 TAS files

Input files (`.m64`) and savestates (`.st`) for the individual-star TASes of **Super Mario 64 Island 1.1**
(30 Stars project). Times follow SM64LuaRedux's timer (fade-in to star dance).

## Playing a movie

- Use Mupen64 (mupen64-rr-lua 1.5.x) with the Super Mario 64 Island 1.1 ROM.
- Keep each `.m64` in the same folder as its `.st`. Mupen plays `a.b.c.m64` from `a.b.c.st`, else `a.b.st`, else `a.st`,
  so several movies share one savestate (e.g. all `lp_course3_3.*.m64` start from `lp_course3_3.st`).

## Notes

- **The 8 Red Coins Again + 100c** (`100c.skykingdom.swim_baked.m64`): the original was recorded with SM64Lua's swim
  button on and desyncs without it. This copy has those A presses (22 samples, 592-662) written into the inputs, so
  it plays on its own. **Turn SM64Lua's swim button off** for it.
- **Bowser Stage** and **Throws** are one movie (`bowser_stage.m64`): the stage, then the fight.
- The Son of Whomp King (Toriku) is not here yet.
- `castle-movement/`: level re-entries. Timed from the first frame of control after the exit to the painting entry.
  `sky kingdom re-enter.m64` does not reach the painting on playback (Mario idles after a dialog at the exit).

## Stars

| Star | Time | .m64 | .st |
|---|---|---|---|
| Big Bob-Omb Fight Back | 41.37 | [bom_course1.king.41_37.m64](1-bob-omb-mountain/bom_course1.king.41_37.m64) | [bom_course1.st](1-bob-omb-mountain/bom_course1.st) |
| Hide in the Mountain | 14.6 | [star5.mountain.14_60.m64](1-bob-omb-mountain/star5.mountain.14_60.m64) | [star5.st](1-bob-omb-mountain/star5.st) |
| Climb the House | 6.13 | [bom_course1.climb.6_13.m64](1-bob-omb-mountain/bom_course1.climb.6_13.m64) | [bom_course1.st](1-bob-omb-mountain/bom_course1.st) |
| Fly with Fly Guy | 18.13 | [star5.flyguy.18_13.m64](1-bob-omb-mountain/star5.flyguy.18_13.m64) | [star5.st](1-bob-omb-mountain/star5.st) |
| The Locked Hole | 5.43 | [star5.locked.5_43.m64](1-bob-omb-mountain/star5.locked.5_43.m64) | [star5.st](1-bob-omb-mountain/star5.st) |
| Find the 8 Red Coins + 100c | 52.2 | [bom_course1.100c+reds.52_20.m64](1-bob-omb-mountain/bom_course1.100c%2Breds.52_20.m64) | [bom_course1.st](1-bob-omb-mountain/bom_course1.st) |
| At the Other End of the Kingdom | 20.17 | [course2.other_end_of_kingdom.20_17.m64](2-sky-kingdom/course2.other_end_of_kingdom.20_17.m64) | [course2.st](2-sky-kingdom/course2.st) |
| In the Wall | 19.77 | [inthewall_2.m64](2-sky-kingdom/inthewall_2.m64) | [inthewall_2.st](2-sky-kingdom/inthewall_2.st) |
| Listen to What the Bob-omb Has to Say to You | 10.57 | [listentowhatthebobombhastosaytoyou.dsg_idea.m64](2-sky-kingdom/listentowhatthebobombhastosaytoyou.dsg_idea.m64) | [listentowhatthebobombhastosaytoyou.st](2-sky-kingdom/listentowhatthebobombhastosaytoyou.st) |
| The Four Pillars | 19.6 | [fourpillars.19_60.m64](2-sky-kingdom/fourpillars.19_60.m64) | [fourpillars.st](2-sky-kingdom/fourpillars.st) |
| The 8 Red Coins Again + 100c | 90.27 | [100c.skykingdom.swim_baked.m64](2-sky-kingdom/100c.skykingdom.swim_baked.m64) | [100c.st](2-sky-kingdom/100c.st) |
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
| Red Coins | 22.77 | [secretarea.reds.22_77.m64](secret-area/secretarea.reds.22_77.m64) | [secretarea.st](secret-area/secretarea.st) |
| Parkour | 9.97 | [secretarea1.box.9_97.m64](secret-area/secretarea1.box.9_97.m64) | [secretarea1.st](secret-area/secretarea1.st) |
| Bowser Stage |  | [bowser_stage.m64](battle-of-the-hope/bowser_stage.m64) | [bowser_stage.st](battle-of-the-hope/bowser_stage.st) |
| Throws |  | [bowser_stage.m64](battle-of-the-hope/bowser_stage.m64) | [bowser_stage.st](battle-of-the-hope/bowser_stage.st) |
