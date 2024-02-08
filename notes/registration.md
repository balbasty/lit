# Optimisation-based registration

Most classical registration software cast the problem as optimising a functionl of the form

$$
\mathcal{L} = \mathcal{S}\left(\mathbf{f}, g\circ\boldsymbol\phi ~\mid~ \boldsymbol\theta\right) + \mathcal{R}(\boldsymbol\theta)
$$

A few notes on my notations:
- $\mathbf{f} \in \mathbb{R}^N$ is the fixed image, disceretized into $N$ voxels.
- $g \in \mathcal{C}\left(\mathbb{R}^3 \rightarrow \mathbb{R}\right)$ is the moving image, defined as a continuous function of space. Think B-spline encoding.
- $\boldsymbol\phi \in \mathbb{R}^{N \times 3}$ is the transformation field evaluated at the fixed image voxels.
  - More formally, I could have defined $\varphi \in \mathcal{C}\left(\mathbb{R}^3 \rightarrow \mathbb{R}^3\right)$, the continuous spatial transformation, 
    and $\boldsymbol\phi = \left\\{ \varphi\left( \mathbf{x}\_{n} \right) \right\\}_{1 \leqslant n \leqslant N}$ the discretized transfomation.
  - Abusing notations, we have $\left(g\circ\boldsymbol\phi\right) \in \mathbb{R}^N$.
- $\boldsymbol\theta \in \mathbb{R}^K$ is the parameterization of $\boldsymbol\phi$ &mdash; that's what we optimize.
