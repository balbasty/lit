# Optimisation-based registration

---

## General problem

Most classical registration software cast the problem as optimising (let's say minimizing) a functional of the form

$$
\mathcal{L} = \underbrace{\mathcal{S}\left(\mathbf{f}, g\circ\boldsymbol\phi ~\mid~ \boldsymbol\theta\right)}\_{\text{similarity}} ~~~+ \underbrace{\mathcal{R}(\boldsymbol\theta)}\_{\text{regularity}} ~.
$$

> [!NOTE]
> - $\mathcal{S}$ is the similarity metric, which measures how well the fixed and moved images match each other.
> - $\mathcal{R}$ is the regulariser, which measures the regularity of the transformation.
> - $\mathbf{f} \in \mathbb{R}^N$ is the fixed image, disceretised into $N$ voxels.
> - $g \in \mathcal{C}\left(\mathbb{R}^3 \rightarrow \mathbb{R}\right)$ is the moving image, defined as a continuous function of space. Think B-spline encoding.
> - $\boldsymbol\phi \in \mathbb{R}^{N \times 3}$ is the transformation field evaluated at the fixed image voxels.
>   - More formally, I could have defined $\varphi \in \mathcal{C}\left(\mathbb{R}^3 \rightarrow \mathbb{R}^3\right)$, the continuous spatial transformation, 
>     and $\boldsymbol\phi = \left\\{ \varphi\left( \mathbf{x}\_{n} \right) \right\\}_{1 \leqslant n \leqslant N}$ the discretized transfomation.
>   - Abusing notations, we have $\left(g\circ\boldsymbol\phi\right) \in \mathbb{R}^N$.
> - $\boldsymbol\theta \in \mathbb{R}^K$ is the parameterisation of $\boldsymbol\phi$ &mdash; that's what we optimize.


> [!TIP]
> A nice property of this framework is that when the similarity is well chosen, it can be seen as finding a maximum _a posteriori_ value for $\boldsymbol\theta$, with
> 
> $$
> \mathcal{L} = -\ln\underbrace{p\left(\boldsymbol\theta ~\mid~ \mathbf{f}, g\right)}\_{\text{posterior}} = -\ln\underbrace{p\left(\mathbf{f}  ~\mid~ g, \boldsymbol\theta\right)}\_{\text{likelihood}} ~-~ \ln\underbrace{p(\boldsymbol\theta)}\_{\text{prior}} + \ln p\left(\mathbf{f}  ~\mid~ g\right) ~.
> $$

---

## Flavoured Gradient Descent

To simplify things, let us keep only references to $\boldsymbol\theta$, since that's what we optimise for:

$$
\mathcal{L}\left(\boldsymbol\theta\right) = \mathcal{S}\left(\boldsymbol\theta\right) + \mathcal{R}(\boldsymbol\theta) ~.
$$

In 99% of the cases, the regulariser is actually quadratic in the parameters, so we have 

$$
 \mathcal{R}(\boldsymbol\theta) = \frac{1}{2}\boldsymbol\theta^{\mathrm{T}}\mathbf{R}\boldsymbol\theta ~~~~\text{with}~~~~ \mathbf{R} \in \mathbb{R}^{K \times K} ~.
$$

Classically finite-difference-based regularisation is used, in which case (assuming circulant boundary conditions), the matrix $\mathbf{R}$ is Toeplitz-circulant, and its inverse $\mathbf{R}^{-1}$ can be computed using Fourier transforms. Let us further note that the gradient and Hessian of the regularisation term are
- $\boldsymbol\nabla\mathcal{R}(\boldsymbol\theta) = \mathbf{R}\boldsymbol\theta$,
- $\mathcal{H}\mathcal{R}(\boldsymbol\theta) = \mathbf{R}$.

When it comes to the similarity term, let us also write its gradient and Hessian as
- $\boldsymbol\nabla\mathcal{S}(\boldsymbol\theta) = \mathbf{g}_{\boldsymbol\theta}$,
- $\mathcal{H}\mathcal{S}(\boldsymbol\theta) = \mathbf{H}_{\boldsymbol\theta}$.

> [!NOTE]
> In general the similarity is not quadratic in $\boldsymbol\theta$, so the gradient and Hessian both depend on the point at which they are evaluated in some unknown way.

Let's optimise! The simplest optimisation scheme is gradient descent with step size $\gamma$:

$$
\boldsymbol\theta^{\text{new}} = \boldsymbol\theta - \gamma\left(\mathbf{g}_{\boldsymbol\theta} + \mathbf{R}\boldsymbol\theta\right) ~.
$$

On the other end of the spectrum, if the Hessian of the similarity term is known, we can use [Newton-Raphson](https://en.wikipedia.org/wiki/Newton%27s_method_in_optimization) (also known simply as _Newton's optimisation method_):

$$
\boldsymbol\theta^{\text{new}} = \boldsymbol\theta - \left(\mathbf{H}\_{\boldsymbol\theta} + \mathbf{R}\right)^{-1}\left(\mathbf{g}_{\boldsymbol\theta} + \mathbf{R}\boldsymbol\theta\right) ~.
$$

However, they both belong to the broader family of [preconditioned gradient descent methods](https://en.wikipedia.org/wiki/Preconditioner#Preconditioning_in_optimization), of the form

$$
\boldsymbol\theta^{\text{new}} = \boldsymbol\theta - \mathbf{P}\left(\mathbf{g}_{\boldsymbol\theta} + \mathbf{R}\boldsymbol\theta\right) ~,
$$

where $\mathbf{P}\_{\boldsymbol\theta}$ is known as the preconditioner. In Newton's case, the preconditioner changes at each step, with $\mathbf{P}\_{\boldsymbol\theta} = \left(\mathbf{H}\_{\boldsymbol\theta} + \mathbf{R}\right)^{-1}$, whereas in gradient descent, the preconditioner is fixed and $\mathbf{P} = \gamma\mathbf{I}_K$. [This chapter ](https://web.eecs.umich.edu/~fessler/book/c-opt.pdf) in Jeff Fessler's unpublished textbook made me realise that most optimisation techniques are variants of preconditioned GD. Now, in general we don't know $\mathbf{H}\_{\boldsymbol\theta}$ (and even when we know it, it may not be the best choice). Designing a good optimiser therefore reduces to finding a good preconditioner, that is both efficient to compute&mdash;so that each step is computationaly efficient&mdash;and close enough to the true Hessian&mdash;so that each step is close to optimal in some sense. 

---

## Preconditioners

[Gauss-Newton](https://en.wikipedia.org/wiki/Gauss%E2%80%93Newton_algorithm) is generally presented in the context of nonlinear least-squares optimization. Keeping it general, let's assume that

$$
\mathcal{S}(\boldsymbol\theta) = \frac{1}{2} \mathcal{F}(\boldsymbol\theta)^{\mathbf{T}} \mathbf{W} \mathcal{F}(\boldsymbol\theta)
$$

where $\mathbf{W} \in \mathbb{R}^{M \times M}$ is a positive semi-definite matrix of mixing weights (generally diagonal) and $\mathcal{F} \in \mathcal{C}(\mathbb{R}^K \rightarrow \mathbb{R}^M)$ is some nonlinear function. By application of the chain rule, its gradient and Hessian are
- $\boldsymbol\nabla\mathcal{S}(\boldsymbol\theta) = \boldsymbol\nabla\mathcal{F}(\boldsymbol\theta)^{\mathrm{T}} \mathbf{W} \mathcal{F}(\boldsymbol\theta)$.
- $\mathcal{H}\mathcal{S}(\boldsymbol\theta) = \boldsymbol\nabla\mathcal{F}(\boldsymbol\theta)^{\mathrm{T}} \mathbf{W} \boldsymbol\nabla\mathcal{F}(\boldsymbol\theta) + \sum_{m}\mathcal{H}\mathcal{F}_m(\boldsymbol\theta) \cdot \mathbf{w}_m^{\text{T}} \mathcal{F}(\boldsymbol\theta)$.

Ths idea is that you're essentially discarding the second term of the Hessian, giving us the preconditioner

$$
\mathbf{P}_{\boldsymbol\theta} = \left(\boldsymbol\nabla\mathcal{F}(\boldsymbol\theta)^{\mathrm{T}} \mathbf{W} \boldsymbol\nabla\mathcal{F}(\boldsymbol\theta) + \mathbf{R}\right)^{-1}
$$

Discarding the second term of the Hessian derives from the use of [Fisher's scoring](https://en.wikipedia.org/wiki/Scoring_algorithm), where the assumption $\boldsymbol\nabla\mathcal{S}(\boldsymbol\theta) = \mathbf{0}$ is plugged back into the Hessian. In this case, this yields $\mathcal{F}(\boldsymbol\theta) = \mathbf{0}$ and therefore the nulling of the second term. One of its main advantages is that it is always positive semi-definite, even in cases when the true Hessian $\mathcal{H}\mathcal{S}(\boldsymbol\theta)$ is negative semi-definite (which ca happen!).

> [!NOTE]
> Fisher's scoring can be applied in more general contexts than nonlinear least-squares,
> and is a common way to obtain approximate Hessians to use as preconditioners.
> 
> For example, JA uses it when optimizing bias fields in unified segmentation. As you probably know, he does not
> log transform the data, and enforces bias field positivity by wrapping it in an exponential. The Gaussian log-likelihood in a cluster is
>
> $$
> \ln p(x \mid \beta, \mu, \sigma^2) = -\frac{1}{2\sigma^2} (\exp(\beta) x - \mu)^2 + \beta ~,
> $$
> 
> where the trailing $\beta$ comes from the log-determinant of the variance. The gradient and Hessian of the negative log-likelihhod with respect to $\beta$ are
> - $\nabla\mathcal{L}(\beta) = \frac{\exp(\beta)x}{\sigma_2} (\exp(\beta) x - \mu) - 1$
> - $\mathcal{H}\mathcal{L}(\beta) = 1 + \nabla\mathcal{L}(\beta) + \frac{\left(\exp(\beta)x\right)^2}{\sigma^2}$
>
> Adding the condition $\nabla\mathcal{L}(\beta) = 0$ and plugging it in the Hessian gives us
> - $\mathcal{H}^{\text{Fisher}}\mathcal{L}(\beta) = 1 + \frac{\left(\exp(\beta)x\right)^2}{\sigma^2}$
>
> This si typically a case where the true Hessian can be negative, but Fisher's Hessian is not!
