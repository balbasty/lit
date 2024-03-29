# Classification losses

## Optimal Bayes classifier

It is easier to understand classification by defining the joint probability $p(\mathbf{x}, \mathbf{z})$ 
across data $\mathbf{x} \in \mathbb{R}^N$ and labels $\mathbf{z} \in \left\[1 \dots K\right\]^M$,
for the entire (infinite) collection of pairs.
Note that this collection is larger than just the training or testing set. Using the 
product rule of probability, this joint distribution can be factorised as either 
$p\left(\mathbf{x} \mid \mathbf{z}\right)~p\left(\mathbf{z}\right)$ or $p\left(\mathbf{z} \mid \mathbf{x}\right)~p\left(\mathbf{x}\right)$.

Application of Bayes rule (which simply stems from the two factors above) allows the 
posterior probability of the labels conditioned on the data to be written: 
$p\left(\mathbf{z} \mid \mathbf{x}\right) = p\left(\mathbf{x} \mid \mathbf{z}\right)~p\left(\mathbf{z}\right)/p\left(\mathbf{x}\right)$. 
However, the denominator $p\left(\mathbf{x}\right) = \int p\left(\mathbf{x}, \mathbf{z}\right) \mathrm{d}\mathbf{z}$
is usually intractable. We will assume, however that this posterior is known.
For simplicity (and to be coherent with the literature), we write the _marginal_
posterior as 
```math
\eta_m\left(\mathbf{x}, k\right) = p\left(z_m = k \mid \mathbf{x}\right) 
= \int p\left(z_m = k, \mathbf{z}_{l \neq m} \mid \mathbf{x}\right) \mathrm{d}\mathbf{z}_{l \neq m}.
```

Now, we define the classifier $b: \mathbb{R}^N 	\rightarrow \left[1 \dots K\right]^M$ that assigns the 
classes with maximum marginal probability to a data point:
```math
b_m\left(\mathbf{x}\right) = \mathrm{argmax}_k~~\eta_{m}\left(\mathbf{x}, k\right).
```
Let us prove that this classifier minimizes the expected 0/1 risk (or equivalently maximizes the _accuracy_). For any classifier $h$:
```math
\mathcal{L}_{0/1} 
= \mathbb{E}_{\mathbf{x}, \mathbf{z}}\left[\sum_m h_m\left(\mathbf{x}\right) \neq z_m\right]
= \sum_m \mathbb{E}_{\mathbf{x}}\left[ \mathbb{E}_{\mathbf{z} | \mathbf{x}}\left[ h_m\left(\mathbf{x}\right) \neq z_m \right] \right]
= \sum_m \mathbb{E}_{\mathbf{x}}\left[ \sum_k \eta_m\left(\mathbf{x}, k\right) \left\{ h_m\left(\mathbf{x}\right) \neq k\right\} \right]
```

This risk is minimized when $h_m$ assigns the most probable _posterior_ class under $\eta_m$. 
The minimum possible risk is called the Bayes error rate and is 
```math 
\mathcal{L}_{0/1}^\star = \sum_m \mathbb{E}_{\mathbf{x}}\left[\min_k \eta_m\left(\mathbf{x}, k\right)\right] .
```
Note finally that correlations between labels to not matter. Only their marginal posterior probabilities are needed 
in order to make the optimal decision.

## Learning optimal classifiers

Of course, posteriors are not known in general. Unsupervised and semi-supervised methods generally start 
by defining a (family of) joint distribution $p(\mathbf{x}, \mathbf{z})$ in the form of a _generative model_, which 
caracterizes the factorized form $p\left(\mathbf{x} \mid \mathbf{z}\right)~p\left(\mathbf{z}\right)$. 
The posterior distribution $p\left(\mathbf{z} \mid \mathbf{x}\right)$ is then calculated, 
or approximated (using _.e.g._ variational Bayes), and used to take the optimal decision.

On the other hand, fully supervised method start with a very large collection of paired samples $\\{(\hat{\mathbf{x}}_i, \hat{\mathbf{z}}_i)\\}_i$,
such that summing a function across its samples approximates taking its expected value: 
```math
\frac{1}{N_i} \sum_i f\left(\hat{\mathbf{x}}_i, \hat{\mathbf{z}}_i\right) \approx \mathbb{E}_{\mathbf{x}, \mathbf{z}} \left[ f\left(\mathbf{x}, \mathbf{z}\right) \right] .
```
The objective is then to find a classifier $h\left(\mathbf{x}\right)$ that minimizes the $\mathcal{L}_{0/1}$ risk.
