# Example run
**User:** "Add a 7-day login streak to my obby: coins 50,75,100,150,200,300 and a pet on day 7. Reset at 00:00 UTC, 1 day grace."

**Agent output summary:**
- Created Config (7 rewards, `resetOffset = 0`, `graceDays = 1`), Types, Store (UpdateAsync + 3 retries + BindToClose), Service (rate-limited `ClaimStreak` RemoteFunction returning `ClaimResult`), client UI.
- Tests (fake clock/store): 9/9 pass – incl. double-claim rejected, missed-day reset, grace kept streak, DataStore outage → no grant.
- Note: pet grant calls your existing `PetService.Give(player, "StreakPup")` — stubbed, wire it up.

Reference implementation built with this skill: the StreakRewards module (see preview).
