---
name: roblox-safe-progression
description: Implement exploit-safe, data-loss-safe player progression in Roblox (daily login streaks, rewards, XP, currencies) with Luau --!strict, server authority and DataStore best practice. Use for any Roblox reward, streak, currency or save-data task.
---
# Roblox Safe Progression

## Non-negotiables
1. **Server authority:** the client only *requests*; the server validates and grants. Never trust client-sent amounts, timestamps, or reward IDs.
2. **Time from the server:** use `os.time()` / `DateTime.now()` on the server; compute "day index" as `math.floor((t - offsetSeconds) / 86400)`. Client clocks are ignored.
3. **Idempotent claims:** store `lastClaimDay` and refuse a second claim on the same day index; remotes are rate limited (e.g. 1 call / 2 s per player).
4. **Persistence:** `UpdateAsync` (never `SetAsync` for read-modify-write), retries with exponential backoff (3 tries, 1/2/4 s), budget checks via `GetRequestBudgetForRequestType`, save on `PlayerRemoving` and `game:BindToClose` (with a timeout), and autosave every 120–300 s. Prefer session locking (ProfileStore) for anything with currency.
5. **Schema versioning:** every save has `version`; write a `migrate(data)` that upgrades old shapes and fills defaults.
6. **Typed modules:** `--!strict`, exported types for `PlayerData`, `RewardDef`, `ClaimResult`.

## Streak algorithm
```
today = dayIndex(now)
if data.lastClaimDay == today -> AlreadyClaimed
elseif data.lastClaimDay == today - 1 -> streak += 1
elseif grace and today - lastClaimDay <= 1 + graceDays -> streak += 1
else streak = 1
reward = rewards[((streak - 1) % #rewards) + 1]
grant(reward) ; data.lastClaimDay = today ; save
```

## Structure
- `ServerScriptService/Progression/Service.server.luau` – remotes, validation, grants
- `ServerStorage/Progression/Store.luau` – DataStore/ProfileStore adapter (swappable)
- `ReplicatedStorage/Progression/Config.luau` – reward table, reset offset, grace days
- `ReplicatedStorage/Progression/Types.luau`
- `StarterPlayerScripts/ProgressionUI.client.luau` – UI only, no logic

## Testing
Inject a fake clock and fake store into the service; unit-test: first claim, same-day double claim, consecutive day, missed day, grace window, cycle wrap, corrupted/old-version data, DataStore failure (retry then fail closed without granting).

## Report back
Files, the reward table, how to change reset hour, test results, and any API you could not verify.
