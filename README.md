# FIFA 20 Player Clustering & Analysis

Exploratory data analysis and unsupervised clustering of FIFA 20 players based on their skill attributes.

## About

FIFA 20 contains data on 18,278 players across 104 features. This project clusters players by skill profile using K-Means, DBSCAN, and Hierarchical Clustering, and answers three specific analysis questions on nationality, age-performance trends, and offensive player wages.

## Dataset

- Source: `players_20.csv` — FIFA 20 Career Mode player data
- 18,278 players · 104 features · 0 duplicates
- 86 features profiled in SweetViz report
- Download: [PRCP-1004-Fifa20 dataset](https://d3ilbtxij3aepc.cloudfront.net/projects/CDS-Capstone-Projects/PRCP-1004-Fifa20.zip)

## Notebooks

| Notebook | Description |
|---|---|
| `Task_1_and_3.ipynb` | EDA (Task 1), SweetViz report, Task 3 analysis questions |
| `Fifa_20_using_clustering.ipynb` | Data preprocessing, clustering (Task 2) |

## Task 3 — Analysis Questions

### Top 10 countries producing the most players

| Rank | Country |
|---|---|
| 1 | England (1,667) |
| 2 | Germany (1,216) |
| 3 | Spain (1,035) |
| 4 | France (984) |
| 5 | Argentina (886) |
| 6 | Brazil (824) |
| 7 | Italy (732) |
| 8 | Colombia |
| 9 | Japan |
| 10 | Netherlands |

### At what age do players stop improving?

Based on the scatter plot of overall rating vs age, players rated above 85 (top tier) stop improving after **age 34**. The mathematical peak (mean overall by age) is age 41, but this is skewed by a handful of elite veterans. For most players, the peak window is between ages 25–30.

### Which offensive position earns the most?

| Position | Average Weekly Wage |
|---|---|
| Right Winger (RW) | €15,848 |
| Left Winger (LW) | €14,037 |
| Striker (ST) | €10,153 |

Right Wingers are paid ~56% more than Strikers on average, reflecting the premium placed on pace and dribbling skill profiles.

## Clustering (Task 2)

### Features used (11)

`age`, `value_eur`, `overall`, `international_reputation`, `skill_moves`, `pace`, `shooting`, `passing`, `dribbling`, `defending`, `physic`

Goalkeepers were separated from outfield players before clustering. Players with overall < 50 were excluded.

### Pipeline

1. MinMaxScaler — normalise all 11 features
2. PCA — reduce to 2 components for visualisation
3. Fit three clustering models and compare

### Models compared

| Model | Params | Notes |
|---|---|---|
| K-Means | k=5, random_state=42 | Primary model, clear visual separation |
| DBSCAN | eps=0.5, min_samples=5 | Density-based, auto noise detection |
| Hierarchical | Ward linkage, cut=2 | Dendrogram for cluster tree view |

## Key EDA Findings

- Real Madrid has the highest squad value (€897.9M) and highest weekly wage bill (€5.35M/week)
- Players aged 20–35 possess the top overall and potential ratings
- Heavier players (>90kg) show lower pace and dribbling but higher physic ratings
- Taller players (>190cm) show decline in pace, passing, and dribbling
- Right foot is dominant — roughly 75% of all players prefer right foot

## Tech Stack

- Python, pandas, NumPy, Matplotlib, seaborn
- scikit-learn (KMeans, DBSCAN, PCA, MinMaxScaler, LabelEncoder)
- scipy (linkage, dendrogram, fcluster)
- sweetviz (automated EDA report)

## Setup

```bash
git clone https://github.com/<your-username>/fifa20-player-clustering.git
cd fifa20-player-clustering
pip install pandas numpy matplotlib seaborn scikit-learn scipy sweetviz
```

## Run

Place `players_20.csv` in the project folder, then open either notebook and run all cells.

**Task 1 + 3:**
```
jupyter notebook Task_1_and_3.ipynb
```

**Clustering:**
```
jupyter notebook Fifa_20_using_clustering.ipynb
```

## Project Structure

```
fifa20-player-clustering/
├── Task_1_and_3.ipynb
├── Fifa_20_using_clustering.ipynb
├── players_20.csv
├── SWEETVIZ_REPORT.html      # Auto-generated EDA report
└── README.md
```

## Author

K Manoj
