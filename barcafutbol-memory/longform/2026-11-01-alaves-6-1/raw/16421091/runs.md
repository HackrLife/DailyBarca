# Apify runs for Sofascore event 16421091 (run at 2026-11-02 ~13:58 UTC)

STATUS: INCOMPLETE. Runs succeeded on Apify, but raw datasets are NOT yet saved to disk (see scrape-log.md, blocker).

| Purpose | Actor | Input | Run ID | Dataset ID | Items |
|---|---|---|---|---|---|
| matchDetails | crawlstone/sofascore-football-scraper | mode=matchDetails, matchId=16421091 | CABmbc3to9pzNJdVj | 6Z7lGbqNyZ9gOhPi6 | 1 |
| spatial (shotmap, heatmaps, lineups) | abotapi/sofascore-scraper | mode=url, url=.../rgbsKhb#id:16421091, includeShotmap/PlayerHeatmaps/Lineups=true | HamyWnBMvNFRm5XMU | Qn4YoUpw0E6fDld2G (KV store 1vFowhqUpagZ1wxJp, key OUTPUT) | 1 (~271 KB) |
| team-2817 (Barca) | crawlstone | mode=teamDetails, teamId=2817, comp 8, season 97268 | vkDJPVTSB1jsUD0bm | 4vRgLmgyUqblRfsnk | 1 (~118 KB est.) |
| team-2885 (Alaves) | crawlstone | mode=teamDetails, teamId=2885, comp 8, season 97268 | J2JuUKwXeRFg9GBia | 6L5zFUhhLdFd1Je8N | 1 (~118 KB) |
| playerDetails x N | crawlstone | not run | - | - | - |
