# Algorithm Complexity
## Big O notation
Video: Michael Sambol [Big-O notation in 5 minutes - YouTube](https://www.youtube.com/watch?v=__vX2sjlpXU)
 
 Describes the efficiency of an algorithm, 
 Complexity in terms of input size, independent of machine

Worst-case most common, best-case, average-case also possible

### Rules
1. Ignores constants: 5n -> O(n)
2. Certain terms dominate others: O(1) < O(logn) < O(n) < O(nlogn) < O(n^2) < O(2^n) < O(n!). Ignore low-order terms

### In practice
1. Constants matter, a lot of situations have small input sizes so a constant of 2 or 3 could have a large impact.
2. Consider average-case and best-case, for the same reason.

# Applied Statistics
## Importance of Being Uncertain
Krzywinski, Martin, and Naomi Altman. “*[[Importance of Being Uncertain.pdf|Points of Significance: Importance of Being Uncertain]]*". Nature Methods 10, no. 9 (August 2013): 809–10. [https://doi.org/10.1038/nmeth.2613](https://doi.org/10.1038/nmeth.2613).

Difference between sample and population.
Sample parameters such as $\bar X$ have their own distribution, called the sampling distribution, constructed by considering all possible samples of a given size. Not directly measurable, but useful concept.

### CLT 
Central Limit Theorem
The distribution of sample means will become increasingly normally distributed as the sample size increases, regardless of the shape of the population, as long as the frequency of extreme values drops of relatively quickly.
The measured spread of sample means is also known as Standard Error of the Mean, $SE_{\bar X}$ and is used to estimate $\sigma_{\bar X}$.

$\mu_{\bar X} = \mu$ 
$\sigma_{\bar X} = \sigma / \sqrt{N}$

Since $\sqrt{N}$, the precision increase is much slower than the rate of data collection.

*Always keep in mind that your measurements are estimates, which you should not endow with “an aura of exactitude and finality”. The omnipresence of variability will ensure that each sample will be different.*

## Clustering
Altman, Naomi, and Martin Krzywinski. “[[Clustering.pdf|Points of Significance: Clustering]]” Nature Methods 14, no. 6 (May 2017): 545–46. [https://doi.org/10.1038/nmeth.4299](https://doi.org/10.1038/nmeth.4299).

Clustering output is only useful if the clusters correspond to relevant features that were not used to define the grouping. 

To judge clusters' validity, we need external information, clusters are not known in advance.

Clustering methods always find clusters, even if there are no  
natural clusters in the data.

We should always ask whether the objects in a cluster have traits in common that were not used to inform the clustering.

## Principal Component Analysis
Lever, Jake, Martin Krzywinski, and Naomi Altman. “[[PCA.pdf|Points of Significance: Principal Component Analysis.]]” Nature Methods 14, no. 7 (June 2017): 641–42. [https://doi.org/10.1038/nmeth.4346](https://doi.org/10.1038/nmeth.4346).

*PCA helps you interpret your data, but it will not always find the important patterns.*

The variance need to be approximately the same across variables, if one or two of them dominate, they will be heavily weighted along those variables, see fig 3c in comparison to 3b. 

They variables also need to use the same scale, for example not expression and phenotype data. If they do not use the same scale, it may be needed to standardize them so that each variable has unit variance, but if the variables already are on the same scale, this may distort the data.

### Limitations of PCA
- The underlying structure of the data must be linear (4a)
- Patterns that are highly correlated may be unresolved (4b)
- The goal is to maximize the variance, not necessarily to find clusters. (4c)

## K-means Clustering
Video: StatQuest [StatQuest: K-means clustering - YouTube](https://www.youtube.com/watch?v=4b5d3muPQmA)

The k-means clustering cannot guarantee to find the best clusters, but can keep track of their total variance. It can then repeat the method with new starting points and see if the total variance is the lowest (best) one so far. It cannot know if it is the best *overall*, so it will do as many as you tell it to.

### How to choose k
Video: clear that we choose k=3, but other times not as clear.

One way is to try different values for k. When you add more clusters you will get a lower variance, until you have as many clusters as you have points, and the clusters have a variance of zero. If you plot the reduction in variance per value for k, you can see where the greatest reduction in variation is, in the example for k=3. "elbow plot"

## Hierarchical Clustering
Video: StatQuest [StatQuest: Hierarchical Clustering - YouTube](https://www.youtube.com/watch?v=7xHsRkOdVwo)

Pairwise comparisons between clusters.
### Distance metric
- Euclidean distance most common (same as k-means clustering distance)
- Manhattan distance (sum(abs(difference in sample i)))
- etc
There is no biological or physical reason to choose one over the other, choose the one which give you more insight into your data.

### Linkage Criterion
- Complete linkage (distance to furthest point)
- Single linkage (distance to closest point)
- Centroid (distance to average of each cluster)
- etc

## PCA main ideas
Video: StatQuest [StatQuest: PCA main ideas in only 5 minutes!!! - YouTube](https://www.youtube.com/watch?v=HMOI_lkzW08)

Differences along PC1 is more important than differences along PC2.