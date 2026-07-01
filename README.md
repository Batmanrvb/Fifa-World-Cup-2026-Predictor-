# ⚽ FIFA World Cup 2026 — Predictive Analytics Website

A fully interactive, real-data predictive model for the 2026 FIFA World Cup. Built as a single HTML file — no build tools, no dependencies.

---

## 📊 Features

| Feature | Description |
|---|---|
| **Power Rankings** | All 32 remaining teams ranked by tournament win probability |
| **Group Stage Standings** | Complete final standings for all 12 groups with qualification status |
| **Knockout Bracket** | Full Round of 32 results + predicted R16, QF, SF, Final |
| **Team Analyzer** | Per-team dashboard with radar chart, advancement probabilities, and H2H odds |
| **Match Results** | All completed and upcoming R32 matches with model predictions |
| **Predictive Model** | Elo ratings + group stage form + historical data + fixture difficulty |

---

## 🚀 Deploy to GitHub Pages (3 steps)

1. **Create a new GitHub repository** (e.g. `wc2026-predictor`)
2. **Upload `index.html`** to the repo root
3. Go to **Settings → Pages → Source: Deploy from branch → main / root**

Your site goes live in ~60 seconds.

---

## 🔢 How the Predictive Model Works

The model combines four data sources:

### 1. Elo Rating (55% weight)
Modified FIFA Elo system. Higher-rated teams have a higher base win probability against any opponent.
- Formula: `P(A beats B) = 1 / (1 + 10^((Elo_B - Elo_A) / 400))`
- Ratings range: ~1300 (Curaçao) to ~2100 (Argentina)

### 2. Group Stage Form (30% weight)
- Points (0–9), goal difference, goals scored/conceded
- Teams with 9 points (perfect) receive maximum form bonus
- Group stage GD reflects defensive and attacking efficiency

### 3. Historical Strength (15% weight)
- World Cup appearances (tournament experience)
- Titles won (pedigree)
- Normalized to 0–1 scale

### 4. Advancement Probability Monte Carlo
Tournament paths are simulated through the bracket, accounting for:
- Knockout round Elo matchups at each stage
- Bracket difficulty (which teams are in which pathway)
- The FIFA 2026 rule that top 4 Elo teams can't meet until semifinals

---

## 📋 Data Sources

- Group stage results: Real match data (June 11–27, 2026)
- Round of 32 schedule: Confirmed FIFA fixtures
- Elo ratings: Calibrated from club.elo and FIFA rankings
- FIFA rankings: March 2026 release

---

## 🗓️ Tournament Timeline

| Round | Dates |
|---|---|
| Group Stage | June 11–27, 2026 |
| Round of 32 | June 28 – July 3, 2026 |
| Round of 16 | July 4–7, 2026 |
| Quarterfinals | July 9–11, 2026 |
| Semifinals | July 14–15, 2026 |
| **Final** | **July 19, 2026 · MetLife Stadium, NJ** |

---

## 🏆 Model's Top 5 Predictions to Win

| Team | Win % | Key Factor |
|---|---|---|
| 🇦🇷 Argentina | 24.3% | Highest Elo (2100), perfect group stage |
| 🇫🇷 France | 20.1% | Best GD in group stage (+8), Elo 2090 |
| 🇧🇷 Brazil | 18.5% | 5 titles, Elo 2050, 7-goal GD |
| 🇪🇸 Spain | 14.2% | World #1, Elo 2020, solid defense |
| 🇩🇪 Germany | 13.4% | 4 titles, Elo 2010, attacking firepower |

---

## 🛠️ Updating the Data

To update results as the tournament progresses, edit the `R32_MATCHES` array in `index.html`:

```javascript
{ id:"r32-1", date:"Jun 28", venue:"SoFi Stadium, LA",
  home:"ZAF", away:"CAN",
  score_h: 1, score_a: 3,   // ← update these
  winner: "CAN"              // ← and this
},
```

Set `score_h: null, score_a: null, winner: null` for upcoming matches.

---

## 📁 File Structure

```
/
└── index.html      # Everything is in this one file
└── README.md       # This file
```

No npm, no Node, no build step. Pure HTML/CSS/JS.

---

*Not affiliated with FIFA. Predictions are statistical estimates only.*
