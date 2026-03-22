# Premier League Analytics Dashboard 🏴󠁧󠁢󠁥󠁮󠁧󠁿⚽

An interactive Power BI dashboard built using live Premier League 2025/26 season data, featuring standings, match results, and upcoming fixture win probabilities.

---

## 📊 Dashboard Overview

This project demonstrates end-to-end data analytics skills — from data collection and modeling to interactive visualization and DAX measure development.

**The dashboard includes four main visuals:**
- **Points Bar Chart** — Current standings for all 20 Premier League teams sorted by points
- **Win/Draw/Loss Stacked Bar** — 100% stacked breakdown showing how each team earned their points
- **Recent Results Table** — Latest match results with conditional formatting by outcome
- **Upcoming Fixtures Probability Chart** — Win probability breakdown for upcoming matches with a favourite slicer
<img width="1440" height="750" alt="PL" src="https://github.com/user-attachments/assets/17718268-64b6-4caa-b2ab-2e5053830426" />

---

## 🛠️ Tools & Technologies

| Tool | Usage |
|---|---|
| Power BI Desktop | Dashboard design and visualization |
| DAX | KPI measures and calculated fields |
| Power Query | Data transformation and custom columns |
| Excel (.xlsx) | Data source with three structured tables |
| Python (openpyxl) | Data collection and Excel file generation |

---


## 🔢 DAX Measures

Three custom DAX measures were created for the KPI cards at the top of the dashboard:

**League Leader** — Returns the name of the team with the most points
```
League Leader = 
VAR TopTeam = TOPN(1, Standings, Standings[Points], DESC)
RETURN MAXX(TopTeam, Standings[Team])
```

**Points Gap** — Calculates the points difference between 1st and 2nd place
```
Points Gap = 
VAR First = MAXX(Standings, Standings[Points])
VAR Second = MAXX(FILTER(Standings, Standings[Points] < First), Standings[Points])
RETURN First - Second
```

**Top Win Rate** — Returns the highest win percentage across all teams
```
Top Win Rate = 
VAR TopWins = MAXX(Standings, Standings[Wins])
VAR TopGames = MAXX(FILTER(Standings, Standings[Wins] = TopWins), Standings[Games Played])
RETURN DIVIDE(TopWins, TopGames)
```

---

## 📐 Data Model

The Excel workbook contains three sheets loaded into Power BI as separate tables:

- **Standings** — Rank, Team, Wins, Losses, Draws, Points, Games Played, Win %
- **Recent Results** — Date, Home Team, Away Team, Home Score, Away Score, Result, Total Goals
- **Upcoming Fixtures** — Date, Home Team, Away Team, Home Win %, Draw %, Away Win %, Favourite

---


## 💡 Key Skills Demonstrated

- Data ingestion and transformation using Power Query
- DAX measure development for dynamic KPI cards
- Conditional formatting on table visuals
- Multi-visual dashboard layout and design
- Predictive data visualization using win probability models
