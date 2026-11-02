# Scrape log, event 16421091

## Identity check (from crawlstone matchDetails, run CABmbc3to9pzNJdVj): PASS
| Field | Expected | Sofascore |
|---|---|---|
| event id | 16421091 | 16421091 |
| start | 2026-10-31 20:00 UTC | 2026-10-31T20:00:00Z (ts 1793476800) |
| home / away | FC Barcelona (2817) / Deportivo Alaves (2885) | homeTeamId 2817 FC Barcelona / awayTeamId 2885 Deportivo Alaves |
| competition | LaLiga (8) | competitionId 8 LaLiga (tournamentId 36) |
| season | 97268 | seasonId 97268, LaLiga 26/27 |
| round | 11 | roundNumber 11 |
| score | 6-1 | 6-1, status finished, winnerSide home |
Venue Spotify Camp Nou; referee Adrian Cordero Vega.
Note: URL slug reads deportivo-alaves-fc-barcelona (reused path) but home/away in data is Barca home. Matched by event id only.
The abotapi spatial run was not yet cross-checked for event id; do that on read.

## BLOCKER
Raw datasets cannot be saved untouched. api.apify.com is denied by the egress proxy (403 on CONNECT, no APIFY_TOKEN in env), so datasets are only readable through the Apify MCP get-dataset-items tool, i.e. through model context. Saving ~270 KB + ~120 KB x 2 + ~30 player datasets would mean the model re-typing JSON, which is a transcription, not an untouched copy, and violates the zero-error rule. Not attempted. data.json not written.
