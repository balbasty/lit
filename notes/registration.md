# Optimisation-based registration

Most classical registration software cast the problem as optimising a functionl of the form

$$
\mathcal{L} = \mathcal{S}\left(\mathbf{f}, g\circ\boldsymbol\phi ~\mid~ \boldsymbol\theta\right) + \mathcal{R}(\boldsymbol\theta) ~.
$$

A few notes on my notations:
- $\mathcal{S}$ is the similarity metric, which measures how well the fixed and moved images match each other.
- $\mathcal{R}$ is the regularizer, which measures the regularity of the transformation.
- $\mathbf{f} \in \mathbb{R}^N$ is the fixed image, disceretized into $N$ voxels.
- $g \in \mathcal{C}\left(\mathbb{R}^3 \rightarrow \mathbb{R}\right)$ is the moving image, defined as a continuous function of space. Think B-spline encoding.
- $\boldsymbol\phi \in \mathbb{R}^{N \times 3}$ is the transformation field evaluated at the fixed image voxels.
  - More formally, I could have defined $\varphi \in \mathcal{C}\left(\mathbb{R}^3 \rightarrow \mathbb{R}^3\right)$, the continuous spatial transformation, 
    and $\boldsymbol\phi = \left\\{ \varphi\left( \mathbf{x}\_{n} \right) \right\\}_{1 \leqslant n \leqslant N}$ the discretized transfomation.
  - Abusing notations, we have $\left(g\circ\boldsymbol\phi\right) \in \mathbb{R}^N$.
- $\boldsymbol\theta \in \mathbb{R}^K$ is the parameterization of $\boldsymbol\phi$ &mdash; that's what we optimize.

---

To simplify things, let us keep only references to $\boldsymbol\theta$, since that's what we optimize for:

$$
\mathcal{L}\left(\boldsymbol\theta\right) = \mathcal{S}\left(\boldsymbol\theta\right) + \mathcal{R}(\boldsymbol\theta) ~.
$$

In 99% of the cases, the regularizer is actually quadratic in the parameters, so we have 

$$
 \mathcal{R}(\boldsymbol\theta) = \frac{1}{2}\boldsymbol\theta^{\mathrm{T}}\mathbf{R}\boldsymbol\theta ~~~~\text{with}~~~~ \mathbf{R} \in \mathbb{R}^{K \times K} ~.
$$

Classically finite-difference-based regularization is used, in which case (assuming circulant boundary conditions), the matrix $\mathbf{R}$ is Toeplitz-circulant, and its inverse $\mathbf{R}^{-1}$ can be computed using Fourier transforms. Let us further note that the gradient and Hessian of the regularization term are
- $\boldsymbol\nabla\mathcal{R}(\boldsymbol\theta) = \mathbf{R}\boldsymbol\theta$,
- $\mathcal{H}\mathcal{R}(\boldsymbol\theta) = \mathbf{R}$.

When it comes to the similarity term, let us also write its gradient and Hessian as
- $\boldsymbol\nabla\mathcal{S}(\boldsymbol\theta) = \mathbf{g}_{\boldsymbol\theta}$,
- $\mathcal{H}\mathcal{S}(\boldsymbol\theta) = \mathbf{H}_{\boldsymbol\theta}$.

Note that in general the similarity is not quadratic in $\boldsymbol\theta$, so the gradient and Hessian both depend on the point at which they are evaluated in some unknown way.

Let's optimize! The simplest optimization scheme is gradient descent:

$$
\boldsymbol\theta^{\text{new}} = \boldsymbol\theta - \left(\mathbf{g}_{\boldsymbol\theta} + \mathbf{R}\boldsymbol\theta\right) ~.
$$

On the other end of the spectrum, if the Hessian of the similarity term is known, we can use [Newton-Raphson](https://en.wikipedia.org/wiki/Newton%27s_method_in_optimization) (also known simply as _Newton's optimisation method_):

$$
\boldsymbol\theta^{\text{new}} = \boldsymbol\theta - \left(\mathbf{H}\_{\boldsymbol\theta} + \mathbf{R}\right)^{-1}\left(\mathbf{g}_{\boldsymbol\theta} + \mathbf{R}\boldsymbol\theta\right) ~.
$$

However, they both belong to the broader family of [preconditioned gradient descent methods](https://en.wikipedia.org/wiki/Preconditioner#Preconditioning_in_optimization), of the form

$$
\boldsymbol\theta^{\text{new}} = \boldsymbol\theta - \mathbf{P}\_{\boldsymbol\theta}^{-1}\left(\mathbf{g}_{\boldsymbol\theta} + \mathbf{R}\boldsymbol\theta\right) ~,
$$

where $\mathbf{P}\_{\boldsymbol\theta}$ is known as the preconditioner. In Newton's case, the preconditioner changes at each step, with $\mathbf{P}\_{\boldsymbol\theta} = \mathbf{H}\_{\boldsymbol\theta} + \mathbf{R}$, whereas in gradient descent, the preconditioner is fixed and $\mathbf{P} = \mathbf{I}_K$. [This chapter ](https://web.eecs.umich.edu/~fessler/book/c-opt.pdf) in Jeff Fessler's unpublished textbook made me realize that most optimization techniques are variants of preconditioned GD. Now, in general we don't know $\mathbf{H}\_{\boldsymbol\theta}$ (and even when we know it, it may not be the best choice). Designing a good optimizer therefore reduces to finding a good preconditioner, that is both efficient to compute (and invert!)&mdash;so that each step is computationaly efficient&mdash; and close enough to the true Hessian&mdash;so that each step is close to optimal in some sense. 
