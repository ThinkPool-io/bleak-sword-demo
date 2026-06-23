# BLEAK SWORD — Bloodborne-coded vertical slice (design v1)

**Date:** 2026-06-23 · **Status:** approved (Max), building.

## Caveman (plain-English intent)
A single brutal sword duel. You face one gothic-horror duelist on a tiny lantern-lit
stage you look down into. It swings; you read the swing and deflect at the last
instant; land enough deflects and you break its guard and gut it. Miss, and it guts
you. Sekiro's timing in Bloodborne's bloody coat.

## Pillars
- **Duel, not crowd.** One lock-on 1v1 fought to a posture-break.
- **Read the animation, not a meter.** No red-circle telegraph — every attack is a
  real wind-up pose the player learns.
- **Aggression is rewarded.** Bloodborne rally + quickstep make standing your ground
  pay off.

## Decisions (from the client interview)
| Topic | Choice |
|---|---|
| Camera / stage | ¾-iso tabletop shadowbox, layered fore/mid/background parallax; static frame, shakes on hit, pushes in on the kill. One arena. |
| Movement | Lock-on always on; left/right strafe + quickstep dodge (Bloodborne sidestep, short i-frames). Auto-face the duelist. |
| Core loop | Sekiro-style parry/deflect → build enemy **posture** → stagger → **visceral riposte** (huge damage / kill). |
| Lethality | **Posture meter + small HP pool** for both fighters. |
| Bloodborne mechanics | **Rally/Regain** (attack right after a hit to win the health back) + **Quickstep** dodge. Both IN. |
| Enemy attacks | **4 tells:** light slash (tight parry), heavy overhead (big tell), thrust (lunge, off-rhythm), + one **unblockable** (perilous) that must be quickstepped, not parried. |
| Art | Style **8 versions of the duelist** first; 32px tall; chunky-readable Terraria pixel construction on the **bleak ash/black/blood palette** with Bloodborne gothic-horror flavor. Winner sets the direction for hero + future enemies. |
| Tech | Single `index.html`, canvas, no build step, hostable as one GitHub Pages link. Structured (sprite / entity / combat-FSM / render modules) so it can wrap into a WKWebView iOS shell later. No iOS work now. |
| Scope (this slice) | Diorama renders · arrow lock-on movement + quickstep · duelist cycles all 4 tells · parry→posture-break→visceral kill · rally works · player can die. Playable end-to-end vs one boss. |

## Delivery rule
Every visual artifact (sprite gallery, the playable slice) ships as a **hosted
shareable URL** (GitHub Pages), curl-verified 200 before the link is sent. Never a
local path. (Mirrors the thinkpool `/code` link rule.)

## Build order
1. **Sprite gallery** — `sprites.html`: 8 distinct duelist style options, 32px,
   procedural pixel art, labeled, shown large + at stage scale. → Max picks a winner.
2. **Playable slice** — rebuild `index.html`: ¾-iso diorama, lock-on + quickstep,
   posture/HP/rally model, duelist 4-attack state machine with animated tells,
   visceral kill. Reskin to the chosen sprite once picked.

## Out of scope (YAGNI for the slice)
Multiple enemies, level traversal, inventory/weapons-swap, save system, audio polish
beyond basic hit cues, iOS packaging.
