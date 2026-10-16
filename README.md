# How Much Does Possession Tell Us About Attacking Performance in European Soccer?

**Adding possession reduced the average error in estimating a team's goal attempts by 11.73%, but improved estimates of finishing efficiency by only 0.63%.**

**Recommendation:** Professional clubs should include possession when benchmarking **team-level attacking opportunity**, but should not treat it as a substitute for finishing quality or individual player ability. This is one useful piece of a broader performance and recruitment analysis—not a complete scouting model.

## The question: why should a club care?

Soccer teams play in very different environments. Some dominate the ball; others create chances with less possession. When clubs compare attacking output across teams and leagues, they need to know how much of that output is associated with the team's playing environment.

This matters directly to **performance analysts**, who explain match outcomes to coaches. It can also inform **recruitment analysts**, who need team context before comparing individual attackers—but player-level decisions require additional data.

**Question:** How much useful information does possession add when evaluating attacking output across Europe's major leagues, and does that value change by league?

## The evidence

### 1. Possession relates much more strongly to shot volume than finishing efficiency

![Possession correlations with goal attempts, goals, and attacking efficiency](chart1.png)

Across **33,884 team-match observations**, possession correlated with goal attempts at **+0.483**, with goals at **+0.153**, and with finishing efficiency at **−0.079**. Finishing efficiency here means **goals divided by goal attempts**: two goals from ten attempts is 20%.

**What this means:** More possession tends to accompany more attempts, but not necessarily a higher percentage of attempts becoming goals. These are associations, not evidence that increasing possession causes more shots.

### 2. Adding possession reduces goal-attempt estimation error by 11.73%

![Comparison of goal-attempt model errors](chart2.png)

| Model | Mean absolute error (attempts per team-match) |
|---|---:|
| League and season only | 4.193 |
| League, season, and possession | **3.701** |
| League-specific possession relationships | 3.696 |

**Mean absolute error** is how far a model's estimate is from the actual number of attempts, on average; lower is better. Adding possession reduced this error by **0.492 attempts**, or **11.73%**. Allowing the possession relationship to differ by league delivered very little additional improvement overall.

By contrast, adding possession reduced the error for **finishing efficiency** by just **0.63%**. Possession contributes much more to explaining shot volume than conversion rate.

### 3. Possession improves goal-attempt estimates in all five leagues

![Percentage reduction in prediction error by league](chart3.png)

| League | Reduction in error after adding possession |
|---|---:|
| Premier League | **17.33%** |
| Bundesliga | 12.62% |
| Serie A | 9.39% |
| Ligue 1 | 8.56% |
| La Liga | 4.90% |

The size of the improvement varies, but the direction is consistent across all five leagues. The league-level differences are worth investigating, although they do not by themselves establish that clubs need separate models for each league.

## The check: could the finding have failed on new seasons?

I built the models using earlier seasons and evaluated them on **three later seasons not used for training**. If possession had made estimates worse in those seasons, the case for using it as a benchmarking variable would be weaker.

| Held-out season | Reduction in goal-attempt estimation error |
|---|---:|
| 2021/22 | 13.72% |
| 2022/23 | 10.80% |
| 2023/24 | 10.63% |

The improvement was positive in all three held-out seasons, as well as in each league. This supports the consistency of the result within the dataset, **not** its ability to forecast shots before a match.

## How a club could use this finding

**For performance analysts:** Include possession in a team-level benchmark for expected *shot volume in a completed match*. When a team's actual attempts differ from the benchmark, analysts have a reason to investigate its chance creation, tactics, opposition, and match circumstances. The model is a starting point for questions—not a diagnosis.

**For recruitment analysts:** Use the team-level finding as a reminder to establish the attacking environment around a prospective player. A player on a low-possession team may receive a different volume of opportunities than one on a high-possession team. But **this project does not measure individual players or quantify a scouting adjustment**. Any player comparison would need player-level shots, minutes, roles, and chance-quality measures.

**Practical recommendation:** Start with a simple team-level benchmark using league, season, and possession. It captures almost all the accuracy improvement observed here without the extra complexity of league-specific possession slopes. Use its output as context alongside finishing and player-level metrics—not as a standalone recruitment score.

## What I did

I cleaned publicly available match statistics from the **Premier League, Bundesliga, Serie A, Ligue 1, and La Liga** covering **2013/14–2023/24**, then reorganized roughly 16,942 matches into **33,884 team-match observations**. I calculated goals per attempt as finishing efficiency and examined how possession related to attempts, goals, and efficiency. Finally, I compared regression models with and without possession, measuring their errors on later seasons that were held out from training.

## Limitations—and why they matter

- **Same-match information:** Possession and attempts are measured during the same game. The models support *post-match benchmarking*, not a pre-match forecast.
- **Correlation is not causation:** More possession is associated with more attempts, but the analysis cannot show that instructing a team to keep the ball longer would create more shots.
- **No shot-quality data:** Attempts do not distinguish easy chances from difficult ones. Expected goals (xG) could change how we interpret attacking effectiveness.
- **No player-level data:** The results cannot identify undervalued attackers or tell a recruitment team whom to sign.
- **Coverage is limited:** Findings from these five leagues and seasons may not transfer unchanged to other competitions or future years.
- **Zero-attempt matches:** Eleven team-match records have zero attempts, making goals-per-attempt efficiency undefined for those records.

## Reproduce the analysis

| Item | Details |
|---|---|
| **Source** | [Football Match Statistics — Kaggle](https://www.kaggle.com/datasets/gokhanergul/football-match-statistics/data) |
| **License** | MIT (as listed for the dataset) |
| **Retrieved** | September 10, 2026 |
| **Dataset** | `Football.csv` |
| **Notebook** | `Code.ipynb` |
| **Libraries** | pandas, statsmodels, scikit-learn, matplotlib (and other imports shown in the notebook) |

**Run order:** Download or clone the repository, install the libraries imported in `Code.ipynb`, open the notebook in Jupyter, and use **Restart Kernel → Run All Cells**. The notebook contains the data preparation, analyses, validation, and chart-generation steps. The three charts are also included as PNG files for quick viewing.

```text
Soccer_Data/
├── Code.ipynb
├── Football.csv
├── chart1.png
├── chart2.png
├── chart3.png
└── README.md
```

---

*Analytics Institute — Fall 2026*
