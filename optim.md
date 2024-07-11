# Stochastic optimization

## References

- **Variational free energy and the Laplace approximation** <br />
  Karl Friston, Jérémie Mattout, Nelson Trujillo-Barreto, John Ashburner, Will Penny <br />
  _NeuroImage_ (2007) <br />
  https://www.fil.ion.ucl.ac.uk/~karl/Variational%20free%20energy%20and%20the%20Laplace%20approximation.pdf

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

- **On the Convergence of Adam and Beyond** <br />
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

All iterative optimisation methods conpute a vector $\boldsymbol{\Delta}_{k+1}$, 
which defines the step taken from the previous value of the function parameter $\mathbf{x}$:
```math
\mathbf{x}_{k+1} = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k+1} ~.
```

### Line Search

These methods can be augmented by the use of a line search. In this case, 
an initial search direction $\boldsymbol{\Delta}_{k+1}$ is modulated by a positive
scalar $\alpha_{k+1}$ that is optimised until some condition is enforced, giving the effective update step
```math
\mathbf{x}_{k+1} = \mathbf{x}_{k} + \alpha_{k+1}\boldsymbol{\Delta}_{k+1}
```

### Gradient descent

One of the simplest and most used optimisation scheme is gradient descent, in which case
the step is defined as the gradient of the function modulated by a parameter $\eta$ (called
_learning rate_ in machine learning):
```math
\begin{align*}
\mathbf{g}_{k}            & = \nabla f(\mathbf{x}_{k}) \\
\boldsymbol{\Delta}_{k+1} & = - η~\mathbf{g}_{k} \\
\mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k+1}
\end{align*}
```

If the optimisation problem is convex (_i.e._, when the Hessian matrix of second derivatives $(\mathbf{H}f)_{ij} = \frac{\partial^2 f}{\partial x_i \partial x_j}$ is positive definite everywhere -- assuming $f$ is twice differentiable), convergence is assured when
```math
\frac{1}{\eta} \geqslant \sup_{\mathbf{x}} \lVert \mathbf{H}f(\mathbf{x}) \rVert_2
```
where $\lVert \mathbf{H} \rVert_2$ returns the largest singular value of $\mathbf{H}$.

### Preconditioning

Gradient descent is a special case of the broader "preconditioned gradient descent" family, which take updates of the form
```math
\begin{align*}
\mathbf{g}_{k}            & = \nabla f(\mathbf{x}_{k}) \\
\boldsymbol{\Delta}_{k+1} & = - \mathbf{P}_{k} \mathbf{g}_{k} \\
\mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k+1}
\end{align*}
```
where $\mathbf{P}_k$ is a positive-definite matrix. One recognises that gradient descent reduces to $\mathbf{P}_k = \eta \mathbf{I}$.

Again, assuming convexity, convergence is assured when 
```math
\mathbf{P}_k^{-1} \succcurlyeq \mathbf{H}f(\mathbf{x}) ~~\forall\mathbf{x},
```
where $\succcurlyeq$ denotes the Loewner order ($\mathbf{A} \succcurlyeq \mathbf{B} \Leftrightarrow \mathbf{A} - \mathbf{B} \succcurlyeq \mathbf{0}$).

On the other side of the spectrum, the preconditioner can be the inverse Hessian at the current parameter value (Newton-Raphson) or an approximation of it (in non-convex problems, Gauss-Newton):
```math
\begin{align*}
\mathbf{g}_{k}            & = \nabla f(\mathbf{x}_{k}) \\
\mathbf{H}_{k}            & = \mathbf{H}f(\mathbf{x}_k) \\
\mathbf{P}_k              & = \mathbf{H}_{k}^{-1} \\
\boldsymbol{\Delta}_{k+1} & = - \mathbf{P}_k \mathbf{g}_{k} \\
\mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k+1}
\end{align*}
```

The Levenberg-Marquardt algorithm interpolates between both sides of the spectrum by adding loading factors on the diagonal of the (Newton or Gauss-Newton) Hessian:
```math
\begin{alignat*}{3}
\mathbf{g}_{k}            & = \nabla f(\mathbf{x}_{k}) \\
\mathbf{H}_{k}            & = \mathbf{H}f(\mathbf{x}_k) \\
\mathbf{P}_k              & = \left(\mathbf{H}_{k} + \lambda\mathbf{I}\right)^{-1} & ~~~\text{(Levenberg)}\\
\mathbf{P}_k              & = \left(\mathbf{H}_{k} + \lambda\mathrm{diag}\left(\mathrm{diag}(\mathbf{H}_{k})\right)\right)^{-1} & ~~~\text{(Marquardt)}\\
\boldsymbol{\Delta}_{k+1} & = - \mathbf{P}_k \mathbf{g}_{k} \\
\mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k+1}
\end{alignat*}
```

### Temporal regularisation

An other way of interpolating between a gradient and a (approximate) Newton step, proposed by Friston et al. (2007) and named _temporal regularisation_, takes advantage of the fact that
the step $\mathbf{x}\_{k+1} = \mathbf{x}\_{k} + \mathbf{P}\_k \mathbf{g}\_k$ finds the minimum of the quadratic
```math
\hat{f}(\mathbf{x}) = \mathbf{x}_{k} + (\mathbf{x} - \mathbf{x}_{k})^\mathrm{T} \mathbf{g}_k + \frac{1}{2}(\mathbf{x} - \mathbf{x}_{k})^\mathrm{T}\mathbf{P}_k^{-1}(\mathbf{x} - \mathbf{x}_{k})
```
by integrating its gradient flow (defined by $\dot{\mathbf{x}} = -\frac{\partial f}{\partial \mathbf{x}}$)
from $t=0$ to $t=\infty$, with $\mathbf{x}\_0  = \mathbf{x}\_{k}$. One way to regularize this step, when the preconditioner cannot be completely trusted, is to stop the integration of the flow early, _e.g._, integrate until some finite $t$. This partial gradient flow can again be obtained in closed form, yielding the update step
```math
\begin{align*}
\mathbf{g}_{k}            & = \nabla f(\mathbf{x}_{k}) \\
\mathbf{H}_{k}            & = \mathbf{H}f(\mathbf{x}_k) \\
\mathbf{P}_k              & = \left(\mathrm{expm}(t\mathbf{H}_k) - \mathbf{I}\right)\mathbf{H}_k^{-1} \\
\boldsymbol{\Delta}_{k+1} & = - \mathbf{P}_k \mathbf{g}_{k} \\
\mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k+1}
\end{align*}
```

### Accelerated first-order methods

Rather than computing the analytical Hessian, the family of _accelerated_ gradient methods use gradients from the previous steps to diverge from the gradient flow in an efficient way.

#### Momentum

The simplest acceleration methods adds a _momentum_ term, such that the effective step taken is a weighted average of the previous step and current gradient step:
```math
\begin{align*}
\mathbf{g}_{k}            & = \nabla f(\mathbf{x}_{k}) \\
\boldsymbol{\Delta}_{k+1} & = \beta \boldsymbol{\Delta}_{k} - \eta~\mathbf{g}_{k} \\
\mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k+1}
\end{align*}
```
Note that the steps $\boldsymbol{\Delta}$ are recursive averages of all gradients, and the momentum strategy can thefore be rewritten as
```math
\begin{align*}
\mathbf{g}_{k}            & = \nabla f(\mathbf{x}_{k}) \\
\bar{\mathbf{g}}_{k+1}    & = \beta \bar{\mathbf{g}}_{k} + (1-\beta) \mathbf{g}_{k} \\
\boldsymbol{\Delta}_{k+1} & = - \eta~\bar{\mathbf{g}}_{k+1} \\
\mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k+1}
\end{align*}
```
where the "old" $\eta$ is equal to the "new" $\eta(1-\beta)$. This reformulation allows gradient descent with momentum to be interpreted as some "moving average" gradient descent. It will also help us connect this method with adaptive moment methods later on.

#### Nesterov's momentum

Nesterov introduced a variant of the momentum method, where the gradient is computed _after_ re-taking a step. The gradient step can thereby be seen as correcting the momentum step. This can be written as
```math
\begin{align*}
\boldsymbol{\Delta}_{k+1} & = \beta_{k} \Delta_{k} - \eta~\nabla f(\mathbf{x}_{k} + \beta_{k} \boldsymbol{\Delta}_{k}) \\
\mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k+1}
\end{align*}
```
We can introduce an auxiliary sequence of points at which the gradient is computed:
```math
\begin{align*}
\mathbf{y}_{k}            & = \mathbf{x}_{k} + \beta_{k} \Delta_{k} \\
\mathbf{g}_{k}            & = \nabla f(\mathbf{y}_{k}) \\
\boldsymbol{\Delta}_{k+1} & = \beta_{k} \boldsymbol{\Delta}_{k} - \eta~\mathbf{g}_{k} \\
\mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k+1}
\end{align*}
```
Following Sutskever et al (2013) and Bengio et al (2013), we can switch half iterations and rewrite these steps as 
```math
\begin{align*}
\mathbf{g}_{k}            & = \nabla f(\mathbf{x}_{k}) \\
\boldsymbol{\Delta}_{k+1} & = \beta_{k} \boldsymbol{\Delta}_{k} - \eta~\mathbf{g}_{k} \\
\mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \beta_{k+1}\boldsymbol{\Delta}_{k+1} - \eta~\mathbf{g}_{k}
\end{align*}
```
where the new $\mathbf{x}$ corresponds to the old $\mathbf{y}$. Which (assuming the series of $\beta\_k$ constant) we can again rewrite as an averaged gradient step
```math
\begin{align*}
\mathbf{g}_{k}            & = \nabla f(\mathbf{x}_{k}) \\
\bar{\mathbf{g}}_{k+1}    & = \beta \bar{\mathbf{g}}_{k} + (1-\beta) \mathbf{g}_{k} \\
\boldsymbol{\Delta}_{k+1} & = - \eta~\left(\beta\bar{\mathbf{g}}_{k+1} + (1-\beta) \mathbf{g}_{k}\right) \\
\mathbf{x}_{k+1}          & = \mathbf{x}_{k} + \boldsymbol{\Delta}_{k+1}
\end{align*}
```
(^^^ THIS SHOULD BE CHECKED... MY MATH IS FUZZY)

In practice, the series of $\beta_k$ is set such that
```math
\begin{align*}
\theta_{k+1} & = \frac{1}{2} (1 + \sqrt{1 + 4 \theta^2}) \\
\beta_{k+1} & = \frac{\theta_{k+1} - 1}{\theta_{k}}
\end{align*}
```
