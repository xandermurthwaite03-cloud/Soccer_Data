# Football Match Statistics Research Proposal

## 1. The Question

**Has the relationship between ball possession and successful goal attempts evolved differently across European leagues?**

## 2. The Dataset

- **Source:** Kaggle – Football Match Statistics
- **URL:** https://www.kaggle.com/datasets/gokhanergul/football-match-statistics/data
- **License:** MIT
- **Date Retrieved:** Thursday, September 10, 2026
- **File Size:** 33 MB

## 3. The Grain

One row represents **one soccer match between a home team and an away team in a particular country, league, and season on a specific date and time**.

- **Total rows:** 95,384
- **Unique match keys:** 95,345

There is a difference of 39 rows between the total row count and the unique match-key count. I plan to investigate and clean these potential duplicates before conducting the analysis.

## 4. The Comparison

I will split the data by **league** and **season/year** to compare how the relationship changes across European leagues and over time.

The main variables I will measure are:

- **Ball possession**
- **Attacking efficiency**, defined as **goals scored / goal attempts**

This will allow me to examine whether greater possession is associated with more efficient attacking and whether that relationship differs by league and season.

## 5. Why Either Answer Is Interesting

I am a very passionate soccer fan, and when I watch teams from different leagues compete in European competitions, I notice differences in their styles of play. Possession alone does not tell the whole story, but it is an important part of understanding how a team controls and builds its attack during a match.

**If I find a similar positive relationship across leagues:** This could suggest that possession-based attacking has become a broader norm in modern European soccer.

**If I find meaningful differences between leagues:** This could suggest that European leagues maintain distinct styles of play, with some relying more heavily on possession-based attacking than others.