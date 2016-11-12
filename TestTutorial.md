---  
layout: default  
category: info  
title: This is a Test  
---
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_CHTML">
</script>

{{page.title}}
==============

This demo hopes to include all possible functions necessary for the
documentation of SCIRun. Including but not limited to referencing
[figures](#readfield), [equations](#equation), [sections](#graphics),
and inline $$\theta$$

Graphics
--------

<figure id="readfield">
<img src="BasicTutorial_figures/readfield.png" title="not relavent">
<figcaption>
(2.6)
</figcaption>
</figure>
<a name="equation"></a>

$$\frac{\partial \Phi}{\partial n}\bar\Omega = 0$$

<a name="equation"></a>

$$y(p,t) = \int_{x} \mathbf{A}_{p,x}u(t-\tau(x))\,dx$$

$$\Theta$$

$$\mathbf{A}^T\mathbf{A}+\lambda
\mathbf{L}^T\mathbf{W}_{\beta}(\mathbf{x})\mathbf{L}) \mathbf{x} =
\mathbf{A}^T\mathbf{y}$$

$$\mathbf{W}_{\beta}(u) = \frac{1}{2} \mbox{diag} \left[ 1 / \sqrt{|[\mathbf{L}\mathbf{x}]_i|^2 + \beta^2}\right]$$

$$\begin{split}
                \min_{x(t), t=1\dots T} &\|y(t) - Ax(t)\|_2^2 + \lambda*\|Rx(t)\|_2^2 \\
                &s.t.\\
                &\hspace{2cm}x(1) >= minB\\
        &\hspace{2cm}x(t+1) >= x(t), \hspace{.2cm}t=1\dots T-1\\
        &\hspace{2cm}x(T) <= maxB
\end{split}
$$

$$\nabla \cdot (\mathbf{\sigma} \nabla \Phi) = 0,$$

$$ \bar{\Phi}(x,y,z) = \sum_i \Phi_i
N_i(x,y,z), $$

$$\sum_i \Phi_i \int_{\Omega - \bar{\Omega} -
\bar{\Omega}_k} \mathbf{\sigma} \nabla N_i \nabla N_j \, d\mathbf{V} = 0. $$

$$\mathbf{W}_{\beta}(u) = \frac{1}{2} \mbox{diag} \left[ 1 / \sqrt{|[\mathbf{L}\mathbf{x}]_i|^2 + \beta^2}\right]$$
$$(\mathbf{A}^T\mathbf{A}+\lambda
\mathbf{L}^T\mathbf{W}_{\beta}(\mathbf{x})\mathbf{L}) \mathbf{x} =
\mathbf{A}^T\mathbf{y}
$$

And now I need many lines to see if the anchors actually work
This guy had a citation idea.[1](#1)

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work

And now I need many lines to see if the anchors actually work And now I
need many lines to see if the anchors actually work And now I need many
lines to see if the anchors actually work And now I need many lines to
see if the anchors actually work And now I need many lines to see if the
anchors actually work And now I need many lines to see if the anchors
actually work And now I need many lines to see if the anchors actually
work And now I need many lines to see if the anchors actually work And
now I need many lines to see if the anchors actually work And now I need
many lines to see if the anchors actually work And now I need many lines
to see if the anchors actually work

This demo hopes to include all possible functions necessary for the
documentation of SCIRun. Including but not limited to referencing
[figures](#readfield), [equations](#equation), [sections](#graphics),
and inline

##References <a name="1"></a>
\[1\]: So Chris Krycho, "Not Exactly a Millennium," chriskrycho.com, July 22,
    2015, http://www.chriskrycho.com/2015/not-exactly-a-millennium.html
    (accessed July 25, 2015), ¶6.
    
$$
    % Inverse ---------------------------------------------------------------
%\include{ECGTool_inverse}

\chapter{Inverse Solutions}
\label{ch:inv}

\section{Overview}

The inverse problem of electrocardiography is to find suitable electrical source parameters on the heart that adequately describe the observed body surface potentials. Regularization is typically employed in solution methods to reduce the sensitivity of the problem to relatively small errors in the observed body surface potentials, thereby stabilizing it. As a result, solution methods may be supplied body surface potentials, a forward model, and method-specific regularization parameters as input. Specific use of each method is described below. As output, modules primarily produce the resulting solution with extra outputs, depending on the specific method.

\section{Module Descriptions for Inverse Solution Methods}

%%%%%%%%%%%%%%%%%%%%%%%
\subsection{Tikhonov Regularization}

\begin{figure}[H]
\begin{center}
\includegraphics[width=0.7\textwidth]{ECGToolkitGuide_figures/tik1.png}
\caption{Revised Tikhonov module: {\tt SolveInverseProblemWithTikhonov}.  }
\label{tik_module}
\end{center}
\end{figure}
The module that solves the inverse problem by means of Tikhonov regularization is\\
\href{http://scirundocwiki.sci.utah.edu/SCIRunDocs/index.php/CIBC:Documentation:SCIRun:Reference:BioPSE:SolveInverseProblemWithTikhonov}{{\tt SolveInverseProblemWithTikhonov}}.
This module requires the Forward matrix and a vector of measured potentials (see figure \ref{tik_module}-1,3 ). In this case the module will calculate the standard Tikhonov regularization with $l2$ regularization:
\begin{center}
 \begin{eqnarray}
  x = argmin_x \|Ax -y\|_2 + \lambda \|x\|_2
 \end{eqnarray}
\end{center}

Optionally, the algorithm allows to use other constraints in both the solution and the measurements. In the module, this matrices are respectively called solution constraint
matrix (R) and residual constraint matrix (L) (see figure \ref{tik_module}-2,4). In the general case the formula would result:
\begin{center}
 \begin{eqnarray}
  x = argmin_x \|Ax -Ly\|_2 + \lambda \|Rx\|_2
 \end{eqnarray}
\end{center}

The module is also prepared to compute the solution more efficiently depending in whether the problem is underdetermined or overdetermined. In both cases the underlying
algorithm will be the Gaussian elimination, but the equations to solve will differ. This will give for the underdetermined case:
$$
