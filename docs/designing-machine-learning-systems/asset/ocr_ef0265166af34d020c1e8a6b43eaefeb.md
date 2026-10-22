Ofqual failed to take into account the fact that schools with more resources tend to outperform schools with fewer resources. By prioritizing schools’ historical performance over students’ current performance, this auto-grader punished students from low resource schools, which tend to have more students from underprivileged backgrounds.

# Failure 2: Insufficient fine-grained model evaluation to discover biases.

Bias against students from historically low-performing schools is only one of the many biases discovered about this model after the results were brought to the public. The automated grading system took into account teachers’ assessments as inputs but failed to address teachers’ inconsistency in evaluation across demographic groups. It also “does not take into consideration the impact of multiple disadvantages for some protected groups [under the] 2010 Equalities Act, who will be double/triple disadvantaged by low teacher expectations, [and] racial discrimination that is endemic in some schools.”13

Because the model took into account each school’s historical performance, Ofqual acknowledged that their model didn’t have enough data for small schools. For these schools, instead of using this algorithm to assign final grades, they only used teacher-assessed grades. In practice, this led to “better grades for private school students who tend to have smaller classes.”14

It might have been possible to discover these biases through the public release of the model’s predicted grades with fine-grained evaluation to understand their model’s performance for different slices of data—e.g., evaluating the model’s accuracy for schools of different sizes and for students from different backgrounds.

# Failure 3: Lack of transparency.

Transparency is the first step in building trust in systems, yet Ofqual failed to make important aspects of their auto-grader public before it was too late. For example, they didn’t let the public know that the objective of their system was to maintain fairness between schools until the day the grades were published. The public, therefore, couldn’t express their concern over this objective as the model was being developed.

Further, Ofqual didn’t let teachers know how their assessments would be used by the auto-grader until after the assessments and student ranking had been submitted. Ofqual’s rationale was to avoid teachers attempting to alter their assessments to influence the model’s predictions. Ofqual chose not to release the exact model being used until results day to ensure that everyone would find out their results at the same time.

13 Ofqual, “Awarding GCSE, AS & A Levels.”

14 Jones and Safak, “Can Algorithms Ever Make the Grade?”