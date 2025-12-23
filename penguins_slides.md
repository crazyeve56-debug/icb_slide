---
title: "Penguins Dataset Presentation"
author: "Auto-generated"
date: "2025-12-23"
---

# Penguins Dataset Overview

This presentation summarizes exploratory analysis and visualizations of the Palmer Penguins dataset. Images and tables are included.

::: notes
Speak briefly about dataset origin and goals: familiarize audience with penguins dataset and analysis scope.
:::

# Data Sample (Top 10 rows)

The following table shows the first 10 rows of the dataset.

```{=markdown}
<!-- table will be included as-is from markdown; see penguins_analysis.md for full table -->
```

::: notes
Mention missing values and column meanings (bill_length_mm, bill_depth_mm, flipper_length_mm, body_mass_g, species, island, sex).
:::

# Summary Statistics

Refer to computed descriptive statistics (mean, std, quartiles) for numeric features.

::: notes
Highlight key moments: mean body mass ~4200g, typical flipper length ~200mm.
:::

# Missing Data Summary

Summary of missing values by column (bill_length_mm:2, bill_depth_mm:2, flipper_length_mm:2, body_mass_g:2, sex:11).

::: notes
Explain how missing data was handled (dropped in some plots via dropna()). Mention impact on counts.
:::

# Bill length vs Bill depth by Species

![](output/scatter_bill.png)

**인사이트:**

부리 길이와 부리 깊이의 산점도는 각 종(species)별로 뚜렷한 분포 차이를 보여준다. 특히 Adélie, Chinstrap, Gentoo 간의 클러스터가 관찰된다. 추가적인 군집분석이 권장된다.

::: notes
Point out visible clusters and suggest follow-up analyses (regression, clustering, environmental covariates).
:::

# Pairplot (numeric)

![](output/pairplot.png)

**인사이트:**

쌍분석 플롯은 변수 간 관계를 보여주며, flipper_length_mm와 body_mass_g 사이의 강한 양의 상관관계를 확인할 수 있다.

::: notes
Explain pairplot interpretation and its usefulness for feature selection.
:::

# Histogram of body_mass_g

![](output/hist_body_mass.png)

**인사이트:**

체중 분포는 종별로 중심값 차이를 가지며, Gentoo의 체중대가 높은 경향을 보인다.

::: notes
Comment on potential skewness/outliers and options (log-transform, species separation).
:::

# KDE of body_mass_g by Species

![](output/kde_body_mass.png)

**인사이트:**

KDE로 종별 체중 분포의 중첩과 분리를 확인할 수 있으며, 일부 종은 분포가 명확히 구분된다.

::: notes
Note on bandwidth selection and what distribution overlap implies for classification.
:::

# Body mass by Species (boxplot)

![](output/boxplot_body_mass_species.png)

**인사이트:**

상자그림은 중앙값과 사분위수 차이를 보여주며, 이상치 존재를 확인할 수 있다.

::: notes
Recommend statistical tests to confirm significance (ANOVA, Kruskal-Wallis).
:::

# Flipper length by Species (violin)

![](output/violin_flipper_species.png)

**인사이트:**

바이올린 플롯을 통해 분포의 형태(다봉성 등)를 파악할 수 있으며, 종내 이형성이 존재할 수 있다.

::: notes
Suggest stratifying by sex/island to find subgroups.
:::

# Bill length by Species (stripplot)

![](output/strip_bill_length.png)

**인사이트:**

스트립플롯은 개별 관측치 분포를 보여주며 이상치 식별에 유용하다.

::: notes
Point out density and overlap; mention jitter.
:::

# Bill depth by Species (swarmplot)

![](output/swarm_bill_depth.png)

**인사이트:**

스웜플롯으로 각 종의 분포 밀도를 명확히 파악할 수 있다.

::: notes
Explain swarmplot benefit for small-to-moderate sample sizes.
:::

# Correlation heatmap (numeric features)

![](output/heatmap_corr.png)

**인사이트:**

숫자형 변수 간 상관관계를 확인하여 변수 selection 시 다중공선성 여부를 검토한다.

::: notes
Recommend PCA or removing collinear features before regression modeling.
:::

# Counts per Species

![](output/bar_species_counts.png)

**인사이트:**

종별 샘플 수 차이는 분석 시 가중치나 표본 균형을 고려해야 함을 시사한다.

::: notes
Mention sample sizes: Adelie ~152, Gentoo ~124, Chinstrap ~68.
:::

# Counts per Island

![](output/bar_island_counts.png)

**인사이트:**

섬별 분포는 지리적 분산과 서식지 관련 요인을 반영할 수 있다.

::: notes
Suggest mapping or spatial analysis if coordinates available.
:::

# Counts per Sex

![](output/bar_sex_counts.png)

**인사이트:**

성비 편향은 분석 결과의 해석에 영향을 줄 수 있으므로 통제 필요.

::: notes
Recommend including sex as covariate in models.
:::

# Stacked (percent) species by island

![](output/stacked_species_island.png)

**인사이트:**

섬별 종 구성 비율은 서식지 차이를 드러내며 보전 우선순위 설정에 참고될 수 있다.

::: notes
Highlight islands with single-species dominance (e.g., Gentoo on Biscoe).
:::

# Species vs Island Cross-tab

| species   | Biscoe | Dream | Torgersen |
|:----------|-------:|------:|----------:|
| Adelie    | 44     | 56    | 52        |
| Chinstrap | 0      | 68    | 0         |
| Gentoo    | 124    | 0     | 0         |

::: notes
Explain this cross-tab: Chinstrap observed only on Dream; Gentoo on Biscoe mostly.
:::

# Pivot: Mean body_mass_g by species and island

| species   | Biscoe | Dream | Torgersen |
|:----------|-------:|------:|----------:|
| Adelie    | 3709.66 | 3688.39 | 3706.37 |
| Chinstrap | nan    | 3733.09 | nan     |
| Gentoo    | 5076.02 | nan    | nan     |

::: notes
Discuss differences in mean body mass across species/islands and possible ecological reasons.
:::

# Conclusions & Recommendations

- Species show clear morphological separations in several measurements; consider using these for classification models.
- Address missing sex values and sample size imbalances before inferential analyses.
- For publication-quality figures, install appropriate Korean fonts if needed and fine-tune styles.

::: notes
Summarize findings and propose next steps (modeling, environmental covariates, conservation implications).
:::
