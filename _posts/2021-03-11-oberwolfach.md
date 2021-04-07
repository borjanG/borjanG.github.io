---
layout: post
title: "Control and deep learning: some connections"
tags: [math, ML]
---

*This note is an extended abstract for a talk given by my thesis advisor, Enrique Zuazua, during the workshop "Challenges in Optimization with Complex PDE-Systems", at Oberwolfach, in February 2021. I share it on this blog as I believe it can serve a dissemination purpose. The .pdf version may be found <a href="https://cmc.deusto.eus/control-and-deep-learning-some-connections/">here</a>.*

It is superfluous to state the impact that deep learning has had on modern technology, as it powers many tools of modern society, ranging from web search to content filtering on social networks ([1]). A key paradigm of deep learning is that of **supervised learning**, which addresses the problem of predicting from labeled data, consisting in approximating an unknown function $f(\cdot):\mathcal{X}\to\mathcal{Y}$ from $N$ known but possibly noisy data samples {$x_i,y_i$}$_{i=1}^N$ with $x_i\in\mathcal{X}\subset\mathbf{R}^d$ and $y_i\in\mathcal{Y}$. 
We shall focus on *classification tasks*, wherein $\mathcal{Y}=${$1,\ldots,m$}. 

The workhorse behind the recent successes of deep learning are models called *neural networks* for approximating $f_{\text{approx}}$ of the unknown function $f$; these are parametrized computational architectures which propagate each individual sample $x_i$ of the input data across a sequence of linear parametric operators and simple nonlinearities. 
A canonical example of such models is the **perceptron**

\begin{equation}
f_{\text{approx}}(x) = \sum_{j=1}^d w_{1,j}\sigma(w_{2,j} x+b_j)
\end{equation}

where $w_1\in\mathbf{R}^d$, $w_2\in\mathbf{R}^{d\times d}$ and $b\in\mathbf{R}^d$ are unknown parameters, with $\sigma:\mathbf{R}\to\mathbf{R}$ being a globally Lipschitz continuous function, defined element-wise, the so-called *activation function*. 
	
A by-now classical result, Cybenko's *universal approximation theorem* ([1]) ensures that the set of functions which can be represented by formula (1) is a dense subset of $C^0([-1,1]^d)$. This theory has since flourished, and universal approximation results have been shown for more compound models than (1) (see [2]).
	
In practice however, one looks to use models wherein the compositions are iterated over multiple layers, namely *deep neural networks*. A staple of such models are the so-called **residual neural networks** (ResNets, [3]) which may often be cast as schemes of the mould
	
$$
\begin{cases}
\mathbf{x}_i^{k+1} = \mathbf{x}_i^k + w_1^k\sigma(w_2^k \mathbf{x}_i^k + b^k) &\text{ for } k \in \{0, \ldots, N_{\text{layers}}-1\}\\
\mathbf{x}_i^0 = x_i
\end{cases}
$$

for all $i \in [N]$, where $[N]:=${$1, \ldots, N$}, $w_1^k, w_2^k\in\mathbf{R}^{d\times d}$ and $N_{\text{layers}}\geq 1$ designates the number of layers referred to as the *depth*. 
In fact, I recently came accross a tweet stating that the original paper on ResNets ([3]) is the most cited paper (per Google Scholar) in all scientific disciplines of the 2010s. 

<center>
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">2020&#39;s most cited paper across all scientific disciplines was (still) 2015&#39;s ResNet. <br><br>Paper: <a href="https://t.co/mGGX1OpseY">https://t.co/mGGX1OpseY</a> (v/MSFTResearch) <br><br>More: <a href="https://t.co/e3Va7P6Ea8">https://t.co/e3Va7P6Ea8</a> (<a href="https://twitter.com/TDataScience?ref_src=twsrc%5Etfw">@TDataScience</a>)<a href="https://twitter.com/hashtag/DeepLearning?src=hash&amp;ref_src=twsrc%5Etfw">#DeepLearning</a> <a href="https://twitter.com/hashtag/BestOf2020?src=hash&amp;ref_src=twsrc%5Etfw">#BestOf2020</a><a href="https://twitter.com/hashtag/WednesdayWisdom?src=hash&amp;ref_src=twsrc%5Etfw">#WednesdayWisdom</a> <a href="https://t.co/fdAZPXABZV">pic.twitter.com/fdAZPXABZV</a></p>&mdash; MIT CSAIL (@MIT_CSAIL) <a href="https://twitter.com/MIT_CSAIL/status/1334192858635505665?ref_src=twsrc%5Etfw">December 2, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</center>

Due to the inherent dynamical nature of ResNets, several recent works have considered an associated continuous-time formulation, a trend started with the work [4]. 
This is motivated by the simple observation that for $T>0$, (2) is  the forward Euler approximation of the neural ordinary differential equation (neural ODE)
	
$$
\begin{cases}
\dot{\mathbf{x}}_i(t) = w_1(t)\sigma(w_2(t)\mathbf{x}_i(t)+b(t)) & \text{ for } t \in (0, T) \\
\mathbf{x}_i(0) = x_i.
\end{cases}
$$

It should be noted that the origins of continuous-time supervised learning go back to the 1980s -- in [5] back-propagation algorithms are connected to the adjoint method arising in optimal control (see also [6,7]).
	
One readily sees that the parameters $w_2, w_1, b$ in the neural ODE play the role of *controls*, and thus, the supervised learning problem may be seen as a compound and high-dimensional simultaneous control problem.
	
This is the viewpoint adopted by our group. And here we present some of our main findings.
	
We first analyze neural ODEs from a control theoretical perspective to obtain a fundamental understanding of the working mechanisms behind the processes of classification (more precisely, how the neural ODE flow manages separation of the different classes of data according to their labels). 
	
These objectives are tackled and achieved from the perspective of the simultaneous control of systems of neural ODEs. Namely, in [8] we prove that both separation and universal approximation (to arbitrary $L^\infty_{\text{loc}}$ or $L^2_{\text{loc}}$ functions) are valid properties for the controlled neural ODE flow by means of genuinely nonlinear and constructive proofs, allowing us to also estimate the complexity of the developed control strategies. 

Indeed, the nonlinear nature of the activation function allows deforming half of the phase space while the other half remains invariant, a property that classical models in mechanics do not fulfill. This very property allows to build elementary controls inducing specific dynamics and transformations whose concatenation, along with properly chosen hyperplanes, allows achieving our goals in finitely many steps. We also present the counterparts in the context of the control of neural transport equations, establishing a link between optimal transport and deep neural networks.


In practical applications however, the time-dependent parameters/controls are found by minimizing some cost functional rather than explicitly, via a process commonly referred to as **training**.
Due to the ODE reformulation of ResNets, the training process is nothing else than an optimal control problem which consists in finding optimal parameters steering all of the network outputs $P\mathbf{x}_i(T)$ as close as possible to the corresponding labels $y_i$, where $P:\mathbf{R}^d\to\mathbf{R}^m$ is a given affine and surjective map (e.g., a random matrix) which serves to match dimensions. 
	
In [10], [11], we propose the training problem consisting in minimizing 
	
$$
\frac{1}{N} \sum_{i=1}^N \text{loss}\left(P\mathbf{x}_i(T), y_i\right) + \int_0^T \|\mathbf{x}_i(t)-\overline{\mathbf{x}}_i\|^2 dt +  \|u\|_{L^2(0,T; \mathbf{R}^{d_u})}^2,
$$

where $\text{loss}(\cdot,\cdot)$ is a given continuous and nonnegative function which, in classification tasks (for simplicity, $y_i\in\{0,1\}$), is usually $\text{loss}(x,y) := \|\frac{1}{1+e^{-x}}-y\|^2$ or $\text{loss}(x,y) = \log(1+\exp(-yx))$, and $\overline{\mathbf{x}}_i\in P^{-1}(\{y_i\})$. 

<center>
<img src="../assets/posts/2/trajectory.mp4" width="400" height="300">
</center> 
	
As each time-step of a discretization to (3) may be seen to represent a different layer of the ResNet (2), the time horizon $T>0$ in (3) may serve as an indicator of the number of layers $N_{\text{layers}}$ in the discrete-time context (2). 
A good understanding of the dynamics of the learning problem over longer time horizons would lead to potential rules for choosing the number of layers, and enlighten the possible generalization properties when the number of layers is large. 
	
In [10], [12] (see [13] for the $L^1$--case), under controllability assumptions on the neural ODE (which are addressed in [9]), but without any smallness assumptions on the data, targets, or smoothness assumptions on the dynamics (we only assume $\sigma\in\text{Lip}(\mathbf{R})$), we conclude that the optimal controls $u_T=[w_{1,T}, w_{2,T}, b_T]$ and associated optimal trajectories $\mathbf{x}_T$ satisfy

$$
\frac{1}{N} \sum_{i=1}^N\text{loss}\left(P\mathbf{x}_{T,i}(t), y_i\right) + \|\mathbf{x}_{T,i}(t)-\overline{\mathbf{x}}_i\|\leq C\,e^{-\mu t}
$$

and, moreover, 

$$
\|u_T(t)\| \leq\, Ce^{-\mu t}
$$

for some constant $C,\mu>0$ independent of $T$ and for all $t\in[0,T]$. This is a manifestation of the so-called **turnpike property**, well-known in optimal control and economics ([14]).
	
<center>
<img src="../assets/posts/2/norm_state.pdf" width="280" height="240">
<img src="../assets/posts/2/generalization.pdf" width="320" height="240">
</center> 
    
	
**Outlook.** In the above presented works, we have studied a variety of supervised learning tasks from the continuous-time control theoretical perspective, allowing us to obtain fundamental understanding of the working mechanisms and properties that deep learning. We have, however, focused solely on supervised learning tasks, namely, wherein the dataset is labeled.
	
A major challenge which ought to be formulated and addressed in a more control theoretical framework is the topic of *unsupervised learning*, wherein one only disposes of unlabeled data {$x_i$}. 
	

**Acknowledgments.** This project has received funding from the European Union's Horizon 2020 research and innovation programme under the Marie Sklodowska-Curie grant agreement No.765579-ConFlex, the Alexander von Humboldt-Professorship program, the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement NO. 694126-DyCon), the Transregio 154 Project “Mathematical Modelling, Simulation and Optimization Using the Example of Gas Networks” of the German DFG, grant MTM2017-92996-C2-1-R COSNET of MINECO (Spain) and by the Air Force Office of Scientific Research (AFOSR) under Award NO. FA9550-18-1-0242.


## References.

[1] LeCun, Y., Bengio, Y., and Hinton, G. (2015). Deep learning. Nature,
521(7553):436–444.

[2]
Cybenko, G., Approximation by superpositions of a sigmoidal function., Math. Control Signals Systems (1989), 303--314.

[3]
Pinkus, A., Approximation theory of the mlp model in neural networks.,Acta Numer. 8, 1 (1999), 143--195.

[4] He, K., Zhang, X., Ren, S., and Sun, J. (2016). Deep residual learning for image
recognition. In Proceedings of the IEEE conference on computer vision and pattern recognition, pages
770–778.

[5]
E, W., A proposal on machine learning via dynamical systems. Commun. Math. Stat. 5, 1 (2017), 1--11.

[6]
LeCun, Y., Touresky, D., Hinton, G., and Sejnowski, T. A theoretical framework for back-propagation. In Proceedings of the 1988 connectionist models summer school
  (1988), vol.~1, CMU, Pittsburgh, Pa: Morgan Kaufmann, pp.~21--28.
  
[7]
Sontag, E., and Sussmann, H. Complete controllability of continuous-time recurrent neural
  networks. Systems Control Lett. 30, 4 (1997), 177--183.

[8]
Sontag, E.~D., and Qiao, Y. Further results on controllability of recurrent neural networks.
Systems Control Lett. 36, 2 (1999), 121--129.

[9]
Ruiz-Balet, D., and Zuazua, E. Neural {ODE} control for classification, approximation and transport. In preparation (2021).

[10]
Esteve, C., Geshkovski, B., Pighin, D., and Zuazua, E. Large-time asymptotics in deep learning.
arXiv preprint arXiv:2008.02491 (2020).

[11]
Geshkovski, B. Control in moving interfaces and deep learning. PhD Thesis (2021).

[12]
Esteve, C., Geshkovski, B., Pighin, D., and Zuazua, E. Turnpike in Lipschitz-nonlinear optimal control. arXiv preprint arXiv:2011.11091 (2020).

[13]
Esteve Yag{\"u}e, C., and Geshkovski, B. Sparse approximation in learning via neural ODEs.
arXiv preprint arXiv:2102.13566 (2021).

[14]
Trélat, E., and Zuazua, E. The turnpike property in finite-dimensional nonlinear optimal
  control. J. Differ. Equ. 258, 1 (2015), 81--114.