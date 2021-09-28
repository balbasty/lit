# Classification losses

## Optimal Bayes classifier

It is easier to understand classification by defining the joint probability 
across data _**x**_ &isin; **R**<sup>_N_</sup> and labels _**z**_ &isin; [1.._K_]<sup>_M_</sup>, _p_(_**x**_, _**z**_), 
for the entire (infinite) collection of pairs.
Note that this collection is larger than just the training or testing set. Using the 
product rule of probability, this joint distribution can be factorised as either 
_p_(_**x**_ | _**z**_) _p_(_**z**_) or _p_(_**z**_ | _**x**_) _p_(_**x**_).

Application of Bayes rule (which simply stems from the two factors above) allows the 
posterior probability of the labels conditioned on the data to be written: 
_p_(_**z**_ | _**x**_) = _p_(_**x**_ | _**z**_) _p_(_**z**_) &#8725; _p_(_**x**_). 
However, the denominator _p_(_**x**_) = &int; _p_(_**x**_ | _**z**_) _p_(_**z**_) _d**z**_
is usually intractable. We will assume, however that this posterior is known.
For simplicity (and to be coherent with the literature), we write the _marginal_
posterior as _&eta;<sub>m</sub>_(_**x**_, _k_) = _p_(_z<sub>m</sub>_ = _k_ | _**x**_) 
= &int; _p_(_z<sub>m</sub>_ = _k_, _**z**<sub>l &ne; m</sub>_ | _**x**_) _d**z**<sub>l &ne; m</sub>_.

Now, we define the classifier _b:_ **R**<sup>_N_</sup> 	&rarr; [1.._K_]<sup>_M_</sup> that assigns the 
classes with maximum marginal probability to a data point: _b<sub>m</sub>_(_**x**_) = argmax<sub>_k_</sub> _&eta;<sub>m,k</sub>_(_**x**_).
Let us prove that this classifier minimizes the expected 0/1 risk (or equivalently maximizes the _accuracy_). For any classifier _h_:
> _L<sub>0/1</sub>_ = **E**<sub>_**x**,**z**_</sub>[ &sum;<sub>_m_</sub> _h<sub>m</sub>_(_**x**_) &ne; _z<sub>m</sub>_ ]
> = &sum;<sub>_m_</sub> **E**<sub>_**x**_</sub>[ **E**<sub>_**z**_|_**x**_</sub>[ _h<sub>m</sub>_(_**x**_) &ne; _z<sub>m</sub>_ ] ]
> = &sum;<sub>_m_</sub> **E**<sub>_**x**_</sub>[ &sum;<sub>k</sub> _&eta;<sub>m</sub>_(_**x**_, _k_){_h<sub>m</sub>_(_**x**_) &ne; _k_} ]

This risk is minimized when _h<sub>m</sub>_ assigns the most probable _posterior_ class under _&eta;<sub>m</sub>_. 
The minimum possible risk is called the Bayes error rate and is 
_L<sup>*</sup><sub>0/1</sub>_ = &sum;<sub>_m_</sub> **E**<sub>_**x**_</sub>[ min<sub>_k_</sub> _&eta;<sub>m</sub>_(_**x**_, _k_) ].
Note finally that correlations between labels to not matter. Only their marginal posterior probabilities are needed 
in order to make the optimal decision.

## Learning optimal classifiers

Of course, posteriors are not known in general. Unsupervised and semi-supervised methods generally start 
by defining a (family of) joint distribution _p_(_**x**_, _**z**_) in the form of a _generative model_, which 
caracterizes the factorized form _p_(_**x**_ | _**z**_) _p_(_**z**_). The posterior distribution _p_(_**z**_ | _**x**_)
is then calculated, or approximated (using _.e.g._ variational Bayes), and used to take the optimal decision.

On the other hand, fully supervised method start with a very large collection of paired samples {(_**x&#770;**_<sub>_i_</sub>, _**z&#770;**_<sub>_i_</sub>)}<sub>_i_</sub>, 
such that summing a function across its samples approximates taking its expected value: 
(1 &#8725; _N<sub>i</sub>_) &sum;<sub>_i_</sub> _f_(_**x&#770;**_<sub>_i_</sub>, _**z&#770;**_<sub>_i_</sub>) &approx; **E**<sub>_**x**_,_**z**_</sub> _f_(_**x**_, _**z**_).
The objective is then to find a classifier _h_(_**x**_) that minimizes the _L<sub>0/1</sub>_ risk.