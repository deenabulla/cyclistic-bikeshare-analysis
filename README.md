# Cyclistic Bike-Share — Rider Behavior Analysis

## Business problem
Cyclistic, a Chicago bike-share program, wants to convert casual riders into annual members. The question: **how do annual members and casual riders use the service differently**, and what marketing levers could turn casual riders into members?

## Data source
12 months of Divvy trip data, **January–December 2024**, from `divvy-tripdata.s3.amazonaws.com` — **5,860,568 raw trip records** (ride id, bike type, timestamps, stations, rider type).

## Cleaning steps
1. Parsed `started_at`/`ended_at` into ride durations (minutes).
2. Removed **8,319 trips** with zero/negative duration or duration over 24 hours; 0 null ride IDs, 0 duplicate ride IDs.
3. Processed in 300k-row chunks and aggregated incrementally (no raw data retained).
4. Clean dataset: **5,852,249 rides**.

## Key findings (from the actual data)
1. **Two distinct customer bases.** Annual members took **3,707,005 rides (63.3%)**; casual riders took **2,145,244 (36.7%)**.
2. **Casual riders ride nearly twice as long.** Average ride: **20.9 min casual vs 12.2 min member** (medians ~12.5 vs ~7.5 min) — casual riders savor the ride; members use it as transport.
3. **Weekends belong to casual riders.** **37.9% of casual rides fall on Saturday–Sunday** vs only **24.2%** for members. Peak day: **Saturday for casual, Wednesday for members** — commuting vs leisure.
4. **Geography confirms the split.** Casual hotspots are lakefront/tourist stations — Streeter Dr & Grand Ave, DuSable Lake Shore Dr & Monroe St, Michigan Ave & Oak St — and their top routes are **round-trips** (start = end station), i.e. leisure loops. Member hotspots are commuter corridors (Kingsbury St & Kinzie St, Clinton St & Washington Blvd, Clark St & Elm St) with point-to-point routes.
5. **Shared seasonality, different motives.** Both groups peak in **September 2024** and at **5 PM** — evening lakefront leisure for casual riders, the commute home for members.

## Recommendations
1. **Target weekend lakefront riders for conversion.** Casual riders cluster at a handful of tourist stations on Saturdays — place membership offers (QR codes, station signage) there with the math: "ride all summer for less than the cost of a few weekend rentals."
2. **Sell members' weekday habit to casuals.** Members' Wednesday peak shows the commute use-case; a "try commuting for a week" trial membership could convert leisure riders who also work downtown.
3. **Price the long ride.** Since casual rides average 20.9 min vs 12.2 for members, emphasize that membership removes per-ride time pressure — unlimited longer rides for one flat price.

## Limitations
Station names were missing on some records (excluded from route analysis only). Duration medians are approximated from 5-minute buckets. 2024 only — no year-over-year trend.

---
*Portfolio rebuild of the 2024 Google Data Analytics capstone analysis; original coursework files were lost.*
