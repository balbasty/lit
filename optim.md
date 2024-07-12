# Stochastic optimization

## References

- **Variational free energy and the Laplace approximation** <br />
  Karl Friston, Jérémie Mattout, Nelson Trujillo-Barreto, John Ashburner, Will Penny <br />
  _NeuroImage_ (2007) <br />
  https://www.fil.ion.ucl.ac.uk/~karl/Variational%20free%20energy%20and%20the%20Laplace%20approximation.pdf

- **Adaptive subgradient methods for online learning and stochastic optimization** <br />
  John Duchi, Elad Hazan, Yoram Singer <br />
  _JMLR_ (2011) <br />
  https://jmlr.org/papers/volume12/duchi11a/duchi11a.pdf

- **On the importance of initialization and momentum in deep learning** <br />
  Ilya Sutskever, James Martens, George Dahl, Geoffrey Hinton <br />
  _ICML_ (2013) <br />
  https://proceedings.mlr.press/v28/sutskever13.html
  
- **Advances in Optimizing Recurrent Networks** <br />
  Yoshua Bengio, Nicolas Boulanger-Lewandowski, Razvan Pascanu <br />
  _ICASSP_ (2013) <br />
  https://arxiv.org/abs/1212.0901
  
- **Performance of first-order methods for smooth convex minimization: a novel approach** <br />
  Yoel Drori, Marc Teboulle <br />
  _Math. Program_ (2014) <br />
  https://arxiv.org/abs/1206.3209
  
- **Adam: A Method for Stochastic Optimization** <br />
  Diederik P. Kingma, Jimmy Ba <br />
  _ICLR_ (2015) <br />
  https://arxiv.org/abs/1412.6980

- **Optimized first-order methods for smooth convex minimization** <br />
  Donghwan Kim, Jeffrey A. Fessler <br />
  _Math. Program_ (2016) <br />
  https://arxiv.org/abs/1406.5468
  
- **Incorporating Nesterov Momentum into Adam** (NAdam) <br />
  Timothy Dozat <br />
  _ICLR_ (2016) <br />
  https://openreview.net/forum?id=OM0jvwB8jIp57ZJjtNEZ

- **On the Convergence Analysis of the Optimized Gradient Method** <br />
  Donghwan Kim, Jeffrey A. Fessler <br />
  _Optim Theory Appl_ (2017) <br />
  https://arxiv.org/abs/1510.08573

- **On the Convergence of Adam and Beyond** (AMSgrad) <br />
  Sashank J. Reddi, Satyen Kale, Sanjiv Kumar <br />
  _ICLR_ (2018) <br />
  https://arxiv.org/abs/1904.09237

- **Generalizing the optimized gradient method for smooth convex minimization** <br />
  Donghwan Kim, Jeffrey A. Fessler <br />
  _SIAM J Optim_ (2018) <br />
  https://arxiv.org/abs/1607.06764

- **Decoupled Weight Decay Regularization** (AdamW) <br />
  Ilya Loshchilov, Frank Hutter <br />
  _ICLR_ (2019) <br />
  https://arxiv.org/abs/1711.05101

- **On the variance of the adaptive learning rate and beyond** (RAdam) <br />
  Liyuan Liu, Haoming Jiang, Pengcheng He, Weizhu Chen, Xiaodong Liu, Jianfeng Gao, Jiawei Han <br />
  _ICLR_ (2020) <br />
  https://arxiv.org/abs/1908.03265

- **Optimizing the Efficiency of First-Order Methods for Decreasing the Gradient of Smooth Convex Functions** <br />
  Donghwan Kim, Jeffrey A. Fessler <br />
  _J Optim Theory Appl_ (2021) <br />
  https://arxiv.org/abs/1803.06600
  
---

## Notes

Let us consider a function $f:\mathbb{R}^N \rightarrow \mathbb{R}$ to minimise.

All iterative optimisation methods conpute a vector $\boldsymbol{\Delta}_{k}$, 
which defines the step taken from the previous value of the function parameter $\mathbf{x}$:
> ##### Iteration
> ```math
> \mathbf{x}_{k+1} = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k} ~.
> ```

### Line Search

These methods can be augmented by the use of a line search. In this case, 
an initial search direction $\boldsymbol{\Delta}_{k+1}$ is modulated by a positive
scalar $\alpha\_{k}$ that is optimised until some condition is enforced, giving the effective update step
> ##### Line Search
> ```math
> \mathbf{x}_{k+1} = \mathbf{x}_{k} + \alpha_{k}\boldsymbol{\Delta}_{k}
> ```

### Gradient descent

One of the simplest and most used optimisation scheme is gradient descent, in which case
the step is defined as the gradient of the function modulated by a parameter $\eta$ (called
_learning rate_ in machine learning):
> ##### GD
> ```math
> \begin{align*}
> \mathbf{g}_{k}            & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \boldsymbol{\Delta}_{k}   & = - η~\mathbf{g}_{k} \\
> \mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```

If the optimisation problem is convex (_i.e._, when the Hessian matrix of second derivatives $(\mathbf{H}f)_{ij} = \frac{\partial^2 f}{\partial x_i \partial x_j}$ is positive definite everywhere -- assuming $f$ is twice differentiable), convergence is assured when
```math
\frac{1}{\eta} \geqslant \sup_{\mathbf{x}} \lVert \mathbf{H}f(\mathbf{x}) \rVert_2
```
where $\lVert \mathbf{H} \rVert_2$ returns the largest singular value of $\mathbf{H}$.

### Preconditioning

Gradient descent is a special case of the broader "preconditioned gradient descent" family, which take updates of the form
> ##### PGD
> ```math
> \begin{align*}
> \mathbf{g}_{k}            & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \boldsymbol{\Delta}_{k}   & = - \mathbf{P}_{k} \mathbf{g}_{k} \\
> \mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```
where $\mathbf{P}_k$ is a positive-definite matrix. One recognises that gradient descent reduces to $\mathbf{P}_k = \eta \mathbf{I}$.

Again, assuming convexity, convergence is assured when 
```math
\mathbf{P}_k^{-1} \succcurlyeq \mathbf{H}f(\mathbf{x}) ~~\forall\mathbf{x},
```
where $\succcurlyeq$ denotes the Loewner order ($\mathbf{A} \succcurlyeq \mathbf{B} \Leftrightarrow \mathbf{A} - \mathbf{B} \succcurlyeq \mathbf{0}$).

On the other side of the spectrum, the preconditioner can be the inverse Hessian at the current parameter value (Newton-Raphson) or an approximation of it (in non-convex problems, Gauss-Newton):
> ##### Newton-Raphson
> ```math
> \begin{align*}
> \mathbf{g}_{k}            & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \mathbf{H}_{k}            & = \mathbf{H}f(\mathbf{x}_k) \\
> \mathbf{P}_k              & = \mathbf{H}_{k}^{-1} \\
> \boldsymbol{\Delta}_{k}   & = - \mathbf{P}_k \mathbf{g}_{k} \\
> \mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```

The Levenberg-Marquardt algorithm interpolates between both sides of the spectrum by adding loading factors on the diagonal of the (Newton or Gauss-Newton) Hessian:
> ##### Levenberg-Marquardt
> ```math
> \begin{alignat*}{3}
> \mathbf{g}_{k}            & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \mathbf{H}_{k}            & = \mathbf{H}f(\mathbf{x}_k) \\
> \mathbf{P}_k              & = \left(\mathbf{H}_{k} + \lambda\mathbf{I}\right)^{-1} & ~~~\text{(Levenberg)}\\
> \mathbf{P}_k              & = \left(\mathbf{H}_{k} + \lambda\mathrm{diag}\left(\mathrm{diag}(\mathbf{H}_{k})\right)\right)^{-1} & ~~~\text{(Marquardt)}\\
> \boldsymbol{\Delta}_{k}   & = - \mathbf{P}_k \mathbf{g}_{k} \\
> \mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{alignat*}
> ```

### Temporal regularisation

An other way of interpolating between a gradient and a (approximate) Newton step, proposed by Friston et al. (2007) and named _temporal regularisation_, takes advantage of the fact that
the step $\mathbf{x}\_{k+1} = \mathbf{x}\_{k} + \mathbf{P}\_k \mathbf{g}\_k$ finds the minimum of the quadratic
```math
\hat{f}(\mathbf{x}) = \mathbf{x}_{k} + (\mathbf{x} - \mathbf{x}_{k})^\mathrm{T} \mathbf{g}_k + \frac{1}{2}(\mathbf{x} - \mathbf{x}_{k})^\mathrm{T}\mathbf{P}_k^{-1}(\mathbf{x} - \mathbf{x}_{k})
```
by integrating its gradient flow (defined by $\dot{\mathbf{x}} = -\frac{\partial f}{\partial \mathbf{x}}$)
from $t=0$ to $t=\infty$, with $\mathbf{x}\_0  = \mathbf{x}\_{k}$. One way to regularize this step, when the preconditioner cannot be completely trusted, is to stop the integration of the flow early, _e.g._, integrate until some finite $t$. This partial gradient flow can again be obtained in closed form, yielding the update step
> ##### Temporal regularisation
> ```math
> \begin{align*}
> \mathbf{g}_{k}            & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \mathbf{H}_{k}            & = \mathbf{H}f(\mathbf{x}_k) \\
> \mathbf{P}_k              & = \left(\mathbf{I} - \mathrm{expm}(t\mathbf{H}_k)\right)\mathbf{H}_k^{-1} \\
> \boldsymbol{\Delta}_{k}   & = - \mathbf{P}_k \mathbf{g}_{k} \\
> \mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```

### Accelerated first-order methods

Rather than computing the analytical Hessian, the family of _accelerated_ gradient methods use gradients from all previous steps to diverge from the gradient flow in an efficient way.

#### Momentum

The simplest acceleration methods adds a _momentum_ term, such that the effective step taken is a weighted average of the previous step and current gradient step:
> ##### Momentum (variant 1)
> ```math
> \begin{align*}
> \mathbf{g}_{k}            & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \boldsymbol{\Delta}_{k}   & = \beta \boldsymbol{\Delta}_{k-1} - \eta~\mathbf{g}_{k} \\
> \mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```
Note that the steps $\boldsymbol{\Delta}$ are recursive averages of all gradients, and the momentum strategy can thefore be rewritten as
> ##### Momentum (variant 2)
> ```math
> \begin{align*}
> \mathbf{g}_{k}            & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \bar{\mathbf{g}}_{k}      & = \beta \bar{\mathbf{g}}_{k-1} + (1-\beta) \mathbf{g}_{k} \\
> \boldsymbol{\Delta}_{k}   & = - \eta~\bar{\mathbf{g}}_{k} \\
> \mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```
where the "old" $\eta$ is equal to the "new" $\eta(1-\beta)$. This reformulation allows gradient descent with momentum to be interpreted as some "moving average" gradient descent. It will also help us connect this method with adaptive moment methods later on.

#### Nesterov's momentum

Nesterov introduced a variant of the momentum method, where the gradient is computed _after_ re-taking a step. The gradient step can thereby be seen as correcting the momentum step. This can be written as
> ##### Nesterov (variant 1)
> ```math
> \begin{align*}
> \boldsymbol{\Delta}_{k}   & = \beta_{k} \boldsymbol{\Delta}_{k-1} - \eta~\boldsymbol{\nabla} f(\mathbf{x}_{k} + \beta_{k} \boldsymbol{\Delta}_{k-1}) \\
> \mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```
We can introduce an auxiliary sequence of points at which the gradient is computed:
> ##### Nesterov (variant 2)
> ```math
> \begin{align*}
> \mathbf{y}_{k}            & = \mathbf{x}_{k} + \beta_{k} \boldsymbol{\Delta}_{k-1} \\
> \mathbf{g}_{k}            & = \boldsymbol{\nabla} f(\mathbf{y}_{k}) \\
> \boldsymbol{\Delta}_{k}   & = \beta_{k} \boldsymbol{\Delta}_{k-1} - \eta~\mathbf{g}_{k} \\
> \mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```
Following Sutskever et al (2013) and Bengio et al (2013), we can switch half iterations and rewrite these steps as 
> ##### Nesterov (variant 3)
> ```math
> \begin{align*}
> \mathbf{g}_{k}            & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \boldsymbol{\Delta}_{k}   & = \beta_{k} \boldsymbol{\Delta}_{k-1} - \eta~\mathbf{g}_{k} \\
> \mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \beta_{k+1}\boldsymbol{\Delta}_{k} - \eta~\mathbf{g}_{k}
> \end{align*}
> ```
where the new $\mathbf{x}$ corresponds to the old $\mathbf{y}$. 

We can again (assuming the series of $\beta\_k$ constant) rewrite this as an averaged gradient step, that looks very much like classical momentum:
> ##### Nesterov (variant 4)
> ```math
> \begin{align*}
> \mathbf{g}_{k}                  & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \boldsymbol{\delta}{k}          & = \mathbf{g}_{k} - \mathbf{g}_{k-1} \\
> \bar{\mathbf{g}}_{k}            & = \beta \bar{\mathbf{g}}_{k-1} + (1-\beta) \mathbf{g}_{k} \\
> \bar{\boldsymbol{\delta}}_{k}   & = \beta \bar{\boldsymbol{\delta}}_{k-1} + (1-\beta) \boldsymbol{\delta}_{k} \\
> \tilde{\mathbf{g}}_{k}          & = \bar{\mathbf{g}}_{k} + \beta \bar{\boldsymbol{\delta}}_{k} \\
> \boldsymbol{\Delta}_{k}         & = - \eta~\tilde{\mathbf{g}}_{k} \\
> \mathbf{x}_{k+1}                & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```
where again the "old" $\eta$ is equal to the "new" $\eta(1-\beta)$. We see that the effective gradient $\tilde{\mathbf{g}}$ is the moving average gradient $\bar{\mathbf{g}}$ 
plus a second-order momentum term $\bar{\boldsymbol{\delta}}$. Note that this term is a difference of successive gradients, and therefore a local estimate of curvature:
- if $\delta < 0$, the new slope is steeper than the old slope, and curvature is negative -- the second order term leads to an even more negative gradient and an accelerated descent;
- if $\delta = 0$, there is no change in slope (null curvature) -- we keep our simple moving average descent;
- if $\delta > 0$, the new slope is less steep than the old slope (or even with opposite sign!), and curvature is positive -- the second order term leads to a descelerated descent.

In practice, a nonstationary series of $\beta_k$ is often used:
> ##### Nesterov's $\beta$ series
> ```math
> \begin{align*}
> \theta_0     & = 1 \\
> \theta_{k}   & = \frac{1}{2} (1 + \sqrt{1 + 4 \theta_{k-1}^2}) \\
> \beta_{k}    & = \frac{\theta_{k} - 1}{\theta_{k-1}}
> \end{align*}
> ```

#### Optimised Gradient Method

Kim & Fessler (2016, 2017, 2018, 2021), building on Drori & Teboulle (2014) generalised Nesterov's momentum with the formulation
> ##### OGM (variant 1)
> ```math
> \begin{align*}
> \mathbf{y}_{k+1}          & = \mathbf{x}_{k} - \eta \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \mathbf{x}_{k+1}          & = \mathbf{y}_{k+1} + \beta_k (\mathbf{y}_{k+1} - \mathbf{y}_{k}) + \gamma_k (\mathbf{y}_{k+1} - \mathbf{x}_{k})
> \end{align*}
> ```
which reduces to Nesterov's method when $\gamma\_k = 0$, and to gradient descent when $\beta_k = \gamma\_k = 0$.
We can again switch half-iterations and rewrite this algorithm in terms of $\Delta_k$:
> ##### OGM (variant 2)
> ```math
> \begin{align*}
> \mathbf{g}_{k}            & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \boldsymbol{\Delta}_{k}   & = \beta_{k} \boldsymbol{\Delta}_{k-1} - \eta~\mathbf{g}_{k} + \gamma_{k}\eta~\mathbf{g}_{k-1} \\
> \mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \beta_{k+1}\boldsymbol{\Delta}_{k} - \eta~\mathbf{g}_{k}
> \end{align*}
> ```
which we can relate to [Nesterov's third variant](#nesterov-variant-3). Let us now rephrase this iteration in terms of averaged moments:
> ##### OGM (variant 3)
> ```math
> \begin{align*}
> \mathbf{g}_{k}                  & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \boldsymbol{\delta}_{k}          & = \mathbf{g}_{k} - \mathbf{g}_{k-1} \\
> \bar{\mathbf{g}}_{k}            & = \beta \bar{\mathbf{g}}_{k-1} + (1-\beta) \mathbf{g}_{k} \\
> \bar{\boldsymbol{\delta}}_{k}   & = \beta \bar{\boldsymbol{\delta}}_{k-1} + (1-\beta) \boldsymbol{\delta}_{k} \\
> \tilde{\mathbf{g}}_{k}          & = (1-\beta\gamma)\bar{\mathbf{g}}_{k} + \beta(1+\gamma) \bar{\boldsymbol{\delta}}_{k} \\
> \boldsymbol{\Delta}_{k}         & = - \eta~\tilde{\mathbf{g}}_{k} \\
> \mathbf{x}_{k+1}                & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```
which we can relate to [Nesterov's fourth variant](#nesterov-variant-4), where the "old" $\eta$ is (as always) equal to the "new" $\eta(1-\beta)$.
It becomes clear the OGM simply allows the strength of the second-order term to be decorrelated from the averaging parameter $\beta$, through the introduction of $\gamma$.

Note that, in accelerated frameworks, the value of the learning rate is quite arbitrary; we can therefore reparameterize the learnign rate $\eta$ to capture the magnitude of the effective weighting factors (in $\tilde{\mathbf{g}}$ ), and also reparameterize $\gamma$ to find the more visually pleasing update
> ```math
> \begin{align*}
> \tilde{\mathbf{g}}_{k}          & = \bar{\mathbf{g}}_{k} + \gamma \bar{\boldsymbol{\delta}}_{k} \\
> \end{align*}
> ```

### Conjugate gradient descent

CGD is quite related to accelerated first order methods, in that they also consider that a better decision can be made if it is based on the history of previous gradients, rather than just the current gradient. I need to come back to this section later after I re-read some background, but in the meantime, I'll introduce the most common variants of CGD.

All CGD algorithms have the following structure
> ##### CGD
> ```math
> \begin{align*}
> \mathbf{g}_{k}                  & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \boldsymbol{\delta}_{k}          & = \mathbf{g}_{k} - \mathbf{g}_{k-1} \\
> \mathbf{s}_{k}                  & = \beta_k \mathbf{s}_{k-1} + \mathbf{g}_{k} \\
> \boldsymbol{\Delta}_{k}         & = - \eta~\mathbf{s}_{k} \\
> \mathbf{x}_{k+1}                & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```

With four different variants depending on the calculation of the series of $\beta\_k$:
```math
\begin{alignat*}{4}
& \mathrm{Fletcher-Reeves:}  ~~& \beta_{k} & = \frac{\mathbf{g}_{k}^\mathrm{T}\mathbf{g}_{k}}{\mathbf{g}_{k-1}^\mathrm{T}\mathbf{g}_{k-1}} \\
& \mathrm{Polak-Ribière:}   ~~& \beta_{k} & = \frac{\mathbf{g}_{k}^\mathrm{T}\boldsymbol{\delta}_{k}}{\mathbf{g}_{k-1}^\mathrm{T}\mathbf{g}_{k-1}}\\
& \mathrm{Hestenes-Stiefel:} ~~& \beta_{k} & = \frac{\mathbf{g}_{k}^\mathrm{T}\boldsymbol{\delta}_{k}}{\mathbf{s}_{k-1}^\mathrm{T}\boldsymbol{\delta}_{k}}\\
& \mathrm{Dai-Yuan:}         ~~& \beta_{k} & = \frac{\mathbf{g}_{k}^\mathrm{T}\mathbf{g}_{k}}{\mathbf{s}_{k-1}^\mathrm{T}\boldsymbol{\delta}_{k}}
\end{alignat*}
```

### Adaptive learning rate methods

While first order methods can rely on the full history of gradients, they do not use a data-drive learning rate (the sequence of $\beta\_k$ can be non-constant, but typically follows some analytical formula -- note that we do not include CGD methods here), which means that the effective step is a linear combination of all previous gradients. In the last 10 years, there's been a focus in the machine learning community on methods that use a data-driven _adaptive_ step size to accelerate convergence. Reddi et a (2018) proposed a generic formulation that captures most of these adaptive solutions:
> ```math
> \begin{align*}
> \mathbf{g}_{k}            & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \bar{\mathbf{g}}_{k}      & = \phi_k\left(\left\{\mathbf{g}_{i}\right\}_{i=1}^k\right) \\
> \mathbf{v}_{k}            & = \psi_k\left(\left\{\mathbf{g}_{i}\right\}_{i=1}^k\right) \\
> \tilde{\mathbf{g}}_k      & = \bar{\mathbf{g}}_{k} \div \left(\sqrt{\mathbf{v}_{k}} + \varepsilon\right) \\
> \boldsymbol{\Delta}_{k}   & = - \eta_k~\tilde{\mathbf{g}}_k \\
> \mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```
where $\phi_k$ and $\psi_k$ are arbitrary functions. Note that we do not include their "projector onto feasible set" $\Pi$ here.

**Stochastic gradient descent (SGD)** falls in this framework and uses
```math
\begin{align*}
\phi_k\left(\left\{\mathbf{g}_{i}\right\}_{i=1}^k\right) & = g_k \\
\psi_k\left(\left\{\mathbf{g}_{i}\right\}_{i=1}^k\right) & = \mathbf{1}
\end{align*}
```

**Adagrad** (Duchi et al 2011) uses
```math
\begin{align*}
\phi_k\left(\left\{\mathbf{g}_{i}\right\}_{i=1}^k\right) & = g_k \\
\psi_k\left(\left\{\mathbf{g}_{i}\right\}_{i=1}^k\right) & = \frac{1}{K} \sum_{i=1}^K \mathbf{g}_{i} \odot \mathbf{g}_{i}
\end{align*}
```
> ##### Adagrad
> ```math
> \begin{align*}
> \mathbf{g}_{k}           & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \beta_k                  & = \frac{k-1}{k} \\
> \mathbf{v}_{k}           & = \beta_k \mathbf{v}_{k-1} + (1-\beta_k) \mathbf{g}_{k} \odot \mathbf{g}_{k} \\
> \tilde{\mathbf{g}}_k     & = \mathbf{g}_{k} \div \left(\sqrt{\mathbf{v}_{k}} + \varepsilon\right) \\
> \boldsymbol{\Delta}_{k}  & = - \eta_k \tilde{\mathbf{g}}_k \\
> \mathbf{x}_{k+1}         & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```

**RMSProp** (Tieleman & Hinton, unpublished) uses
```math
\begin{align*}
\phi_k\left(\left\{\mathbf{g}_{i}\right\}_{i=1}^k\right) & = g_k \\
\psi_k\left(\left\{\mathbf{g}_{i}\right\}_{i=1}^k\right) & = (1-\beta) \sum_{i=1}^k \beta^{k-1} \mathbf{g}_i \odot \mathbf{g}_i
\end{align*}
```
which yields the following algorithm
> ##### RMSProp
> ```math
> \begin{align*}
> \mathbf{g}_{k}           & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \mathbf{v}_{k}           & = \beta \mathbf{v}_{k-1} + (1-\beta) \mathbf{g}_{k} \odot \mathbf{g}_{k} \\
> \tilde{\mathbf{g}}_k     & = \mathbf{g}_{k} \div \left(\sqrt{\mathbf{v}_{k}} + \varepsilon\right) \\
> \boldsymbol{\Delta}_{k}  & = - \eta_k \tilde{\mathbf{g}}_k \\
> \mathbf{x}_{k+1}         & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```

**Adam** (Kingma & Ba, 2015) uses
```math
\begin{align*}
\phi_k\left(\left\{\mathbf{g}_{i}\right\}_{i=1}^k\right) & = (1-\beta_1) \sum_{i=1}^k \beta_1^{k-1} \mathbf{g}_i \\
\psi_k\left(\left\{\mathbf{g}_{i}\right\}_{i=1}^k\right) & = (1-\beta_2) \sum_{i=1}^k \beta_2^{k-1} \mathbf{g}_i \odot \mathbf{g}_i
\end{align*}
```
which yields the following algorithm
> ##### Adam
> ```math
> \begin{align*}
> \mathbf{g}_{k}           & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \bar{\mathbf{g}}_{k}     & = \beta_1 \bar{\mathbf{g}}_{k-1} + (1-\beta_1) \mathbf{g}_{k} \\
> \mathbf{v}_{k}           & = \beta_2 \mathbf{v}_{k-1} + (1-\beta_2) \mathbf{g}_{k} \odot \mathbf{g}_{k} \\
> \tilde{\mathbf{g}}_k     & = \bar{\mathbf{g}}_{k} \div \left(\sqrt{\mathbf{v}_{k}} + \varepsilon\right) \\
> \tilde{\eta}_k           & = \eta_k~\frac{\sqrt{1-\beta_2^k}}{1-\beta_1^k} \\
> \boldsymbol{\Delta}_{k}  & = - \eta_k \tilde{\mathbf{g}}_k \\
> \mathbf{x}_{k+1}         & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```

Reddi et al. (2018) showed that Adam may not converge and propose two possible solution: AMSGrad uses an upper bound across all second-moment averages, and AdamNC uses a linear average of second moments instead of an exponential average. Both solutions use a decreasing $\beta_1$ for their proof of convergence but in practice can use a constant $\beta_1$ for most applications.

> ##### AMSGrad
> ```math
> \begin{align*}
> \mathbf{g}_{k}           & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \bar{\mathbf{g}}_{k}     & = \beta_{1k} \mathbf{g}_{k-1} + (1-\beta_{1k}) \mathbf{g}_{k} \\
> \mathbf{v}_{k}           & = \beta_2 \mathbf{v}_{k-1} + (1-\beta_2) \mathbf{g}_{k} \odot \mathbf{g}_{k} \\
> \hat{\mathbf{v}}_{k}     & = \max\left(\hat{\mathbf{v}}_{k-1}, \bar{\mathbf{v}}_{k}\right) \\
> \tilde{\mathbf{g}}_k     & = \bar{\mathbf{g}}_{k} \div \left(\sqrt{\hat{\mathbf{v}}_{k}} + \varepsilon\right) \\
> \boldsymbol{\Delta}_{k}  & = - \eta_k \tilde{\mathbf{g}}_k \\
> \mathbf{x}_{k+1}         & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```

> ##### AdamNC
> ```math
> \begin{align*}
> \mathbf{g}_{k}           & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \beta_{1k}               & = \beta_1 \lambda^{k-1} \\
> \beta_{2k}               & = \frac{k-1}{k} \\
> \bar{\mathbf{g}}_{k}     & = \beta_{1k} \mathbf{g}_{k-1} + (1-\beta_{1k}) \mathbf{g}_{k} \\
> \mathbf{v}_{k}           & = \beta_{2k} \mathbf{v}_{k-1} + (1-\beta_{2k}) \mathbf{g}_{k} \odot \mathbf{g}_{k} \\
> \tilde{\mathbf{g}}_k     & = \bar{\mathbf{g}}_{k} \div \left(\sqrt{\mathbf{v}_{k}} + \varepsilon\right) \\
> \boldsymbol{\Delta}_{k}  & = - \eta_k \tilde{\mathbf{g}}_k \\
> \mathbf{x}_{k+1}         & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```

Liu et al. (2020) proposed a rectified version of Adam that reduces the learning rate when the variance of the second-order moments is high, 
and can even fallback to SGD in cases of extreme variance. This is proposed as an alternative to learning rate warmup.

> ##### RAdam
> ```math
> \begin{align*}
> \rho_\infty              & = \frac{2}{1-\beta_2}-1 \\
> \mathbf{g}_{k}           & = \boldsymbol{\nabla} f(\mathbf{x}_{k}) \\
> \bar{\mathbf{g}}_{k}     & = \beta_1 \bar{\mathbf{g}}_{k-1} + (1-\beta_1) \mathbf{g}_{k} \\
> \mathbf{v}_{k}           & = \beta_2 \mathbf{v}_{k-1} + (1-\beta_2) \mathbf{g}_{k} \odot \mathbf{g}_{k} \\
> \rho_k                   & = \rho_\infty - 2k\frac{\beta_2^k}{1-\beta_2^k} \\
> \text{If}~\rho_k > 4 & \\
> \tilde{\mathbf{g}}_k     & = \bar{\mathbf{g}}_{k} \div \left(\sqrt{\mathbf{v}_{k}} + \varepsilon\right) \\
> \tilde{\eta}_k           & = \eta_k~\sqrt{\frac{(\rho_k-4)(\rho_k-2)\rho_\infty}{(\rho_\infty-4)(\rho_\infty-2)\rho_k}}~\frac{\sqrt{1-\beta_2^k}}{1-\beta_1^k}\\
> \text{Else} & \\
> \tilde{\mathbf{g}}_k     & = \bar{\mathbf{g}}_{k} \\
> \tilde{\eta}_k           & = \eta_k \\
> \text{Finally} & \\
> \boldsymbol{\Delta}_{k}  & = - \tilde{\eta}_k \tilde{\mathbf{g}}_k \\
> \mathbf{x}_{k+1}         & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k}
> \end{align*}
> ```
