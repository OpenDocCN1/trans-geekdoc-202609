

总体参数。常见的估计量包括样本均值、样本方差和样本比例。

## 示例：均值的点估计

在 Rust 中，计算样本均值可以很简单：

```rust
fn sample_mean(data: &[f64]) -> f64 { let sum: f64 = data.iter().sum(); sum / data.len() as f64 }

fn main() {
    let data = vec![4.0, 8.0, 6.0, 5.0, 3.0];
    let mean = sample_mean(&data);
    println!("Sample mean: {}", mean);
}
```

## 区间估计

区间估计提供了一组值的范围，总体参数预期会落在该范围内，置信度为某个特定水平。最常见的区间估计是置信区间。

## 示例：计算置信区间

假设服从正态分布，均值的置信区间可以计算为：

```
[ \text{CI} = \left(\bar{x} - z \frac{\sigma}{\sqrt{n}}\right), \bar{x} + z \frac{\sigma}{\sqrt{n}}\right) ]
```

其中，( \bar{x} ) 是样本均值，( \sigma ) 是标准差，( n ) 是样本量，( z ) 是对应所需置信水平的 z 分数。

```rust
use statrs::distribution::{Normal, Distribution};

fn confidence_interval(data: &[f64], confidence_level: f64) -> (f64, f64) {
    let mean: f64 = data.iter().sum::<f64>() / data.len() as f64;
    let variance: f64 = data.iter().map(|x| (x - mean).powi(2)).sum::<f64>() / data.len() as f64;
    let std_dev = variance.sqrt();
    let z = Normal::new(0.0, 1.0).unwrap().inverse_cdf(1.0 - (1.0 - confidence_level) / 2.0);
    let margin_of_error = z * std_dev / (data.len() as f64).sqrt();
    (mean - margin_of_error, mean + margin_of_error)
}

fn main() {
    let data = vec![5.0, 7.0, 8.0, 6.0, 9.0];
    let (lower, upper) = confidence_interval(&data, 0.95);
    println!("95% Confidence Interval: ({}, {})", lower, upper);
}
```

## 假设检验

假设检验涉及做出一个初始假设（原假设），并使用样本数据来决定是否拒绝该假设而支持备择假设。此过程通常包括以下步骤：

- 1. **制定假设**：定义原假设（H0）和备择假设（H1）。
- 2. **选择显著性水平**：确定 alpha 水平（通常为 0.05），即在 H0 为真时拒绝 H0 的概率。
- 3. **计算检验统计量**：基于样本数据，计算一个衡量样本与 H0 之间一致程度的统计量。
- 4. **确定 p 值**：在假设 H0 为真时，观察到与所观察到的检验统计量一样极端或更极端的检验统计量的概率。
- 5. **做出决策**：如果 p 值小于所选的显著性水平，则拒绝 H0；否则，不拒绝 H0。

## 示例：均值的假设检验

考虑检验样本均值是否与已知总体均值有显著差异。

```rust
use statrs::distribution::{Normal, Univariate};

fn t_test(data: &[f64], population_mean: f64, alpha: f64) -> bool {
    let sample_mean: f64 = data.iter().sum::<f64>() / data.len() as f64;
    let variance: f64 = data.iter().map(|x| (x - sample_mean).powi(2)).sum::<f64>() / (data.len() - 1) as f64;
    let std_dev = variance.sqrt();
    let t_value = (sample_mean - population_mean) / (std_dev / (data.len() as f64).sqrt());
    let degrees_of_freedom = data.len() as f64 - 1.0;

    // Calculate the critical t-value from the Normal distribution
    let normal = Normal::new(0.0, 1.0).unwrap();
    let critical_value = normal.inverse_cdf(1.0 - alpha / 2.0);

    t_value.abs() > critical_value
}

fn main() {
    let data = vec![5.0, 7.0, 8.0, 6.0, 9.0];
    let result = t_test(&data, 6.0, 0.05);
    println!("Reject the null hypothesis: {}", result);
}
```

## 自助法（Bootstrapping）

自助法是一种强大的非参数统计推断方法。它涉及从数据中重复采样（有放回抽样）以估计统计量的抽样分布。这允许对置信区间和标准误进行稳健估计，尤其是在底层分布未知时。

## 示例：自助法置信区间

```rust
use rand::seq::SliceRandom;

fn bootstrap_confidence_interval(data: &[f64], num_samples: usize, alpha: f64) -> (f64, f64) {
    let mut rng = rand::thread_rng();
    let mut means = Vec::with_capacity(num_samples);

    for _ in 0..num_samples {
        let sample: Vec<f64> = data.choose_multiple(&mut rng, data.len()).cloned().collect();
        let mean: f64 = sample.iter().sum::<f64>() / sample.len() as f64;
        means.push(mean);
    }

    means.sort_by(|a, b| a.partial_cmp(b).unwrap());
    let lower_index = (alpha / 2.0 * num_samples as f64) as usize;
    let upper_index = ((1.0 - alpha / 2.0) * num_samples as f64) as usize;

    (means[lower_index], means[upper_index])
}

fn main() {
    let data = vec![5.0, 7.0, 8.0, 6.0, 9.0];
    let (lower, upper) = bootstrap_confidence_interval(&data, 1000, 0.05);
    println!("Bootstrap 95% Confidence Interval: ({}, {})", lower, upper);
}
```

## 贝叶斯推断

贝叶斯推断是一种统计推断方法，在该方法中，随着更多证据或信息的出现，使用贝叶斯定理来更新假设的概率。它涉及三个主要组件：

- 1. **先验分布**：表示在观察任何数据之前对参数的初始信念。
- 2. **似然函数**：表示给定参数时观察到数据的概率。
- 3. **后验分布**：表示在观察数据后对参数的更新信念。

## 示例：贝叶斯更新

```rust
use statrs::distribution::{Beta, Distribution};

fn bayesian_update(prior: Beta, likelihood: f64, num_successes: u32, num_trials: u32) -> Beta {
    let a_post = prior.a() + num_successes as f64 * likelihood;
    let b_post = prior.b() + num_trials as f64 - num_successes as f64 * likelihood;
    Beta::new(a_post, b_post).unwrap()
}

fn main() {
    let prior = Beta::new(1.0, 1.0).unwrap(); // Uniform prior
    let likelihood = 0.5; // Assume a fair coin
    let num_successes = 7;
    let num_trials = 10;

    let posterior = bayesian_update(prior, likelihood, num_successes, num_trials);
    println!("Posterior distribution: Beta({}, {})", posterior.a(), posterior.b());
}
```

统计推断是数据科学的基石，提供了从数据中得出有意义结论所需的工具。Rust 的高效性和强大的库使其成为实现这些方法的绝佳选择，为大规模数据分析提供所需的性能。随着我们向前发展，这些推断技术将在开发高级分析模型和从数据中挖掘更深层洞察方面发挥关键作用。

## 假设检验

### 假设检验的基础

假设检验的核心在于将观察到的数据与在给定假设（称为原假设 H0）下我们期望的数据进行比较。该过程通常包括以下步骤：

- 1. **制定假设**：定义原假设（H0）和备择假设（H1）。原假设通常假设没有效应或没有差异，而备择假设则暗示存在效应或差异。
- 2. **选择显著性水平**：确定 alpha 水平（通常为 0.05），它表示在原假设为真时拒绝原假设的概率（I 类错误）。
- 3. **选择检验统计量**：计算一个量化样本数据偏离 H0 下预期程度的统计量。
- 4. **确定 p 值**：在假设 H0 为真时，计算获得与观察值一样极端或更极端的检验统计量的概率。
- 5. **做出决策**：将 p 值与显著性水平进行比较，以决定是否拒绝 H0。

### 示例：单样本 t 检验

单样本 t 检验用于确定样本均值是否与已知或假设的总体均值有显著差异。让我们考虑一个示例，其中我们检验一组植物样本的平均高度是否与已知的总体均值 15 厘米不同。

```rust
use statrs::distribution::{StudentsT, Univariate};

fn one_sample_t_test(data: &[f64], population_mean: f64, alpha: f64) -> bool {
    let sample_mean: f64 = data.iter().sum::<f64>() / data.len() as f64;
    let variance: f64 = data.iter().map(|x| (x - sample_mean).powi(2)).sum::<f64>() / (data.len() - 1) as f64;
    let std_dev = variance.sqrt();
    let t_value = (sample_mean - population_mean) / (std_dev / (data.len() as f64).sqrt());
    let degrees_of_freedom = data.len() as f64 - 1.0;

    // Calculate the critical t-value from the StudentsT distribution
    let students_t = StudentsT::new(0.0, 1.0, degrees_of_freedom).unwrap();
    let critical_value = students_t.inverse_cdf(1.0 - alpha / 2.0);

    t_value.abs() > critical_value
}

fn main() {
    let data = vec![14.8, 15.1, 15.5, 14.9, 15.2];
    let result = one_sample_t_test(&data, 15.0, 0.05);
    println!("Reject the null hypothesis: {}", result);
}
```

