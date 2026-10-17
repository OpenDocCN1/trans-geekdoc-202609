
```cs
double std = Sigma_f_d * Math.Sqrt(time_step);

double sum_vals = 0.0;

for (int i = 0; i < NumberScenarios; ++i)
{
    // 生成资产路径
    double ST1 = 0;
    not_out = true;
    int k = 0;
    while (not_out && k < TimeSteps)
    {
        z = PricingUtils.RandNorm(mean, std);
        STN = STN * Math.Exp(z);
        if (STN < Barrier_level) not_out = false;
        ST1 = STN;
        path[k] = STN;
        k++;
    }
    if (is_out)
    {
        opt_val = Math.Max(Strike_b, 0.0);
    }
    else
    {
        opt_val = Math.Max(STN - Strike_b, 0.0);
    }
    if (not_out)
    {
        // 如果上方在障碍水平之上
        // 计算资产保持在障碍以上的概率
        if (UseBrownianBridge)
        {
            double total_probability = 1.0;
            double sigma = Sigma_f_d * Sigma_f_d;
            double log_barrier = Math.Log(Barrier_level);
            double fac;
            for (int j = 0; j < TimeSteps; j++)
            {
                double log_s1 = Math.Log(path[j]);
                double log_s2 = Math.Log(path[j + 1]);
                fac = (log_barrier - log_s1) / (log_s2 - log_s1) / (sigma / 2 * time_step);
                // 保持在障碍以上的概率
                total_probability *= Math.Exp(-fac * fac);
            }
            total_probability_above = total_probability;
            sum_vals += opt_val * disc;
        }
        else
        {
            // 不使用布朗桥
            sum_vals += opt_val * disc;
        }
    }
}

double temp_price = sum_vals / (double)NumberScenarios;
return temp_price;
}

return temp;
}
```
