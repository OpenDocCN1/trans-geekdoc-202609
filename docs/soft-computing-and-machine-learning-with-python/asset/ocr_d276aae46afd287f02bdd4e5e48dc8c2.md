(Ascher et al., 2001) for high-performance matrix operations and custom extensions written in ANSI C for portability and speed.

PEBL's use of Python makes it suitable for both programmers and domain experts. Python provides interactive shells and notebook interfaces and includes an extensive standard library and many third-party packages. It has a strong presence in the scientific computing community (Olifant, 2007). Figure 1 shows a script and configuration file example that showcase the ease of using PEBL.

# Table 1: Comparing the features of popular Bayesian network structure learning software

| BANJO | BNT | Causal Explorer | Deal | LibB | PEBL |
|---|---|---|---|---|---||
| Latest Version | 2.0.1 | | 1.4 | 1.2-25 | 2.1 | 0.9.10 |
| License | Academic | GPL | Academic | GPL | MIT |
| Scripting Language | Matlab | Matlab | Matlab | R | N/A | Python |
| Application | Yes | No | No | No | Yes | Yes |
| Interventional Data | No | Yes | No | No | Yes | Yes |
| DBN | No | Yes | Yes | No | No | No |
| Structural Priors | Yes | No | No | No | No | Yes |
| Missing Data | No | Yes | Yes | No | No | Yes |
| Parallel Execution | No | No | No | No | No | Yes |

> 1 Custom academic, non-commercial license; not OSI approved.
2 Via a Matlab-Java bridge.
3 Constraints onhard-priors supported.

While many tasks related to Bayesian learning are embarrassing parallel in theory, few software packages take advantage of it. PEBL can execute tasks in parallel over multiple processors or CPU cores, an Apple Xgrid,1 an IPython cluster2 or the Amazon EC2 platform is particularly attractive for scientists because it allows one to rent processing power on an-demand and execute PEBL tasks on them.

With appropriate configuration settings and the use of parallel execution, PEBL can be used for large learning tasks. Although PEBL has been tested successfully with data sets with 10000 variables and samples, BN structure learning is a known NP-Hard problem (Chickering et al., 1994) and analysis using data sets with more than a few hundred variables is likely to result in poor results due to poor coverage of the search space.