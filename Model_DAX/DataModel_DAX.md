[VALORANT_DAX_README.md](https://github.com/user-attachments/files/29455774/VALORANT_DAX_README.md)
# 🎮 Valorant Scouting Analytics – Data Model & DAX Logic

## 🎯 Model Objective

This model is designed to:
- ensure objective player evaluation
- enable multi-dimensional performance analysis
- provide consistent and reproducible rankings
- support data-driven scouting decisions

👉 Priority: analytical clarity and decision-making over complexity

---

## 🏗️ Model Architecture

Star schema design:

```
Fact_PlayerStats
- Player
- Match
- Rounds
- Kills
- Deaths
- Assists
- Damage

Dim_Player
Dim_Team
Dim_Map
```

---

## 🧠 DAX Principles Applied

- Full reliance on measures (not columns)
- Context-driven calculations
- No hardcoded rankings
- Model-driven evaluation

👉 Focus: context, comparability and consistency

---

## 📊 Core Metrics

```DAX
Impact Score = 
SUM(PlayerStats[Kills]) + SUM(PlayerStats[Assists])

Damage = 
SUM(PlayerStats[Damage])
```

---

## 📈 Efficiency Metrics

```DAX
Kill Efficiency = 
DIVIDE(
    SUM(PlayerStats[Kills]),
    SUM(PlayerStats[Damage])
)

Impact per Round =
DIVIDE(
    [Impact Score],
    SUM(PlayerStats[Rounds])
)
```

---

## 🧠 Reliability (Sample Size)

```DAX
Reliability Score =
SUM(PlayerStats[Rounds])
```

👉 Proxy for statistical confidence

---

## 🧠 Readiness (Benchmark vs Tier 1)

```DAX
Readiness Score =
DIVIDE(
    [Impact Score],
    CALCULATE([Impact Score], ALL(PlayerStats))
)
```

👉 Measures distance from top-level performance

---

## 🧮 Final Scoring Model

```DAX
Final Score =
([Readiness Score] * 0.35) +
([Impact Score] * 0.20) +
([Reliability Score] * 0.15) +
([Kill Efficiency] * 0.10) +
([Impact per Round] * 0.10)
```

---

## ⚠️ Key Modeling Decisions

- No subjective adjustments
- No pre-ranked players
- No qualitative inputs
- Fully model-driven scoring

👉 Ensures objective evaluation

---

## 🚫 Common Mistakes Avoided

- Using raw totals without normalization
- Ranking players without context
- Ignoring sample size
- Mixing performance and perception

---

## ✅ Model Outcome

✔️ Objective ranking system  
✔️ Fully reproducible analysis  
✔️ Comparable player evaluation  
✔️ Decision-ready metrics

---

## 🔚 Conclusion

> This model transforms raw, unranked player statistics into a structured, data-driven scouting decision system.
