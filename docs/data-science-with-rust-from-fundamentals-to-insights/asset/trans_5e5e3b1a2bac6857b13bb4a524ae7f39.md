

```
let var1 = sample1.var(1.0);
let var2 = sample2.var(1.0);
let n1 = sample1.len() as f64;
let n2 = sample2.len() as f64;

(mean1 - mean2) / ((var1 / n1) + (var2 / n2)).sqrt()
}
```

**说明**：
- `independent_t_test` 函数计算两个独立样本的 T 统计量。
- T 统计量使用样本的均值和方差计算得出。

## 2. 卡方检验

**目的**：卡方检验用于分类数据，以检验两个变量的独立性或拟合优度。

**类型**：- 卡方独立性检验：检验两个分类变量是否独立。- 卡方拟合优度检验：检验样本是否与总体匹配。

**示例**：让我们检验两个分类变量之间是否存在关联，例如鱼类类型及其在温哥华周围海域的偏好深度。

## 在 Rust 中实现：

### 1. 设置 Rust 环境：

```
sh
cargo new chi_square_test
cd chi_square_test
```

### 1. 添加依赖：

更新 Cargo.toml 以包含必要的 crate：

```
toml
[dependencies]
ndarray = "0.15"
```

## 1. 实现卡方独立性检验：

```
rust
use ndarray::{Array2, Axis};

fn main() {
    let observed = Array2::from_shape_vec((2, 2), vec![10.0, 10.0, 20.0, 20.0]).unwrap();
    let chi2_stat = chi_square_test(&observed);
    println!("Chi-Square Statistic: {}", chi2_stat);
}

fn chi_square_test(observed: &Array2<f64>) -> f64 {
    let row_sums = observed.sum_axis(Axis(1));
    let col_sums = observed.sum_axis(Axis(0));
    let total = observed.sum();

    let mut chi2 = 0.0;
    for i in 0..observed.shape()[0] {
        for j in 0..observed.shape()[1] {
            let expected = (row_sums[i] * col_sums[j]) / total;
            chi2 += (observed[(i, j)] - expected).powi(2) / expected;
        }
    }
    chi2
}
```

**说明**：
- `chi_square_test` 函数计算卡方统计量。
- 它比较观察频数和期望频数以确定独立性。

## 3. 方差分析（ANOVA）

**目的**：方差分析检验三个或多个组的均值之间是否存在显著差异。

**类型**：- **单因素方差分析**：比较一个因素下的均值。- **双因素方差分析**：比较两个因素下的均值。

示例：让我们分析三种不同肥料对温哥华城市花园中植物生长是否有显著不同的效果。

## 在 Rust 中实现：

### 1. 设置 Rust 环境：

```
sh
cargo new anova_test
cd anova_test
```

### 1. 添加依赖：

更新 Cargo.toml 以包含必要的 crate：

```
toml
[dependencies]
ndarray = "0.15"
```

### 1. 实现单因素方差分析：

```
rust
use ndarray::Array2;

fn main() {
    let data = Array2::from_shape_vec((3, 5), vec![
        10.0, 20.0, 30.0, 40.0, 50.0, // Group 1
        15.0, 25.0, 35.0, 45.0, 55.0, // Group 2
        20.0, 30.0, 40.0, 50.0, 60.0 // Group 3
    ]).unwrap();

    let f_stat = one_way_anova(&data);
    println!("F-Statistic: {}", f_stat);
}

fn one_way_anova(data: &Array2<f64>) -> f64 {
    let grand_mean = data.mean().unwrap();
    let ss_between = data.axis_iter(ndarray::Axis(0))
        .map(|group| group.len() as f64 * (group.mean().unwrap() - grand_mean).powi(2))
        .sum::<f64>();
    let ss_within = data.axis_iter(ndarray::Axis(0))
        .map(|group| group.mapv(|val| (val - group.mean().unwrap().powi(2))).sum())
        .sum::<f64>();
    let df_between = data.len_of(ndarray::Axis(0)) as f64 - 1.0;
    let df_within = data.len_of(ndarray::Axis(1)) as f64 *
        data.len_of(ndarray::Axis(0)) as f64 - data.len_of(ndarray::Axis(0)) as f64;
    (ss_between / df_between) / (ss_within / df_within)
}
...
```

**说明**：
- `one_way_anova` 函数计算单因素方差分析的 F 统计量。
- 它比较组间方差和组内方差以确定显著性。

## 4. Mann-Whitney U 检验

**目的**：Mann-Whitney U 检验是一种非参数检验，用于在数据不服从正态分布时比较两个独立组之间的差异。

**示例**：比较两种不同机器学习模型在非正态分布数据集上的性能。

## 在 Rust 中实现：

### 1. 设置 Rust 环境：

```
sh
cargo new mann_whitney_u_test
cd mann_whitney_u_test
```

### 1. 添加依赖：

更新 Cargo.toml：

```
toml
[dependencies]
ndarray = "0.15"
```

### 1. 实现 Mann-Whitney U 检验：

```
rust
use ndarray::Array1;

fn main() {
    let sample1 = array![23.0, 45.0, 67.0, 89.0, 12.0];
    let sample2 = array![34.0, 56.0, 78.0, 90.0, 23.0];

    let u_stat = mann_whitney_u_test(&sample1, &sample2);
    println!("Mann-Whitney U Statistic: {}", u_stat);
}

fn mann_whitney_u_test(sample1: &Array1<f64>, sample2: &Array1<f64>)
    -> f64 {
    let ranks = rank(&[sample1, sample2]);

    let rank_sum1: f64 = ranks[0].iter().sum();
    let rank_sum2: f64 = ranks[1].iter().sum();

    let n1 = sample1.len() as f64;
    let n2 = sample2.len() as f64;

    rank_sum1 - (n1 * (n1 + 1.0)) / 2.0
}

fn rank(samples: &[&Array1<f64>]) -> Vec<Vec<f64>> {
    let mut combined: Vec<(f64, usize)> = samples.iter().enumerate()
        .flat_map(|(idx, sample)| sample.iter().map(move |&val| (val, idx)))
        .collect();

    combined.sort_by(|a, b| a.0.partial_cmp(&b.0).unwrap());

    let mut ranks = vec![vec![0.0; samples[0].len()], vec![0.0;
    samples[1].len()]];
    let mut rank = 1.0;
    for i in 0..combined.len() {
        ranks[combined[i].1][i % samples[combined[i].1].len()] = rank;
        rank += 1.0;
    }

    ranks
}
...
```

## 说明：

- `mann_whitney_u_test` 函数计算 U 统计量。
- `rank` 函数为合并后的样本分配排名，用于 U 检验计算。

## 5. Wilcoxon 符号秩检验

**目的**：Wilcoxon 符号秩检验是一种非参数检验，用于比较两个相关样本、配对样本或单一样本上的重复测量。

**示例**：比较临床试验中患者的治疗前和治疗后评分。

## 在 Rust 中实现：

### 1. 设置 Rust 环境：

```
sh
cargo new wilcoxon_test
cd wilcoxon_test
```

### 1. 添加依赖：

更新 Cargo.toml：

```
toml
[dependencies]
ndarray = "0.15"
```

### 1. 实现 Wilcoxon 符号秩检验：

```
rust
use ndarray::Array1;

fn main() {
    let pre_treatment = array![85.0, 88.0, 85.0, 90.0, 87.0];
    let post_treatment = array![88.0, 90.0, 89.0, 91.0, 92.0];

    let w_stat = wilcoxon_signed_rank_test(&pre_treatment,
    &post_treatment);
    println!("Wilcoxon Signed-Rank Statistic: {}", w_stat);
}
```

```
fn wilcoxon_signed_rank_test(sample1: &Array1<f64>, sample2:
    &Array1<f64>) -> f64 {
    let differences: Vec<f64> = sample1.iter().zip(sample2.iter())
        .map(|(&pre, &post)| post - pre)
        .collect();

    let abs_differences: Vec<f64> = differences.iter()
        .map(|&diff| diff.abs())
        .collect();

    let ranks = rank(&abs_differences);

    let signed_ranks: f64 = differences.iter()
        .zip(ranks.iter())
        .map(|(&diff, &rank)| if diff > 0.0 { rank } else { -rank })
        .sum();

    signed_ranks.abs()
}
```

```
fn rank(differences: &[f64]) -> Vec<f64> {
    let mut ranked: Vec<(f64, usize)> = differences.iter().enumerate()
        .map(|(idx, &diff)| (diff, idx))
        .collect();

    ranked.sort_by(|a, b| a.0.partial_cmp(&b.0).unwrap());

    let mut ranks = vec![0.0; differences.len()];
    let mut rank = 1.0;
    for i in 0..ranked.len() {
        ranks[ranked[i].1] = rank;
        rank += 1.0;
    }

    ranks
}
...
```

## 说明：

- `wilcoxon_signed_rank_test` 计算 Wilcoxon 符号秩统计量。
- `rank` 函数为绝对差值分配排名，用于符号秩计算。

统计检验是数据科学中的基本工具，为做出数据驱动的决策提供了信心。无论你是使用 T 检验分析均值，使用卡方检验确定关系，还是使用方差分析比较组别，Rust 都为你的统计分析需求提供了强大的解决方案。

