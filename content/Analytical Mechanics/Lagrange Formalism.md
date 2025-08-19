---
Title: "Lagrange Formalism"
author: "Jai Nasu"
date: "2025-08-19"
---

## Recap of Newtonian Mechanics

In Newtonian mechanics, the motion of a particle is described through a few important quantities:
for a particle of (inertial) mass $m$, position $\vec{r}$, we have

$$
\begin{aligned}
  \text{velocity}: \vec{v}     & = \frac{d\vec{r}}{dt}                       \\
  \text{acceleration}: \vec{a} & = \frac{d\vec{v}}{dt} = \frac{d^2\vec{r}}{dt^2} \\
  \text{momentum}: \vec{p}     & = m\vec{v} = m\frac{d\vec{r}}{dt}
\end{aligned}
$$

and the relations between these quantities, in the presence of external forces $\vec{F}_{\text{ext}}^{(i)}$ acting on the particle, are given by **Newton's second law**:

$$
\begin{aligned}
  \frac{d\vec{p}}{dt} = m \frac{d^2\vec{r}}{dt^2} = \sum_i \vec{F}_{\text{ext}}^{(i)}
\end{aligned}
$$

The work done by such forces is given by
$$
\begin{aligned}
  W_{\text{total}} & = \sum_i \int_l d{\vec{x}} \cdot \vec{F}_{\text{ext}}^{(i)}, \quad \text{where } l \text{ is the path of the particle.}
\end{aligned}
$$

This is the energy change of the particle through the motion:
$$
\begin{aligned}
  W_{\text{total}}
   & = \sum_i \int_l d{\vec{x}} \cdot \vec{F}_{\text{ext}}^{(i)}     \\
   & = \int_{t_i}^{t_f} d{t} \, \vec{v} \cdot m \frac{d\vec{v}}{dt}     \\
   & = \int_{t_i}^{t_f} d{t} \, \frac{m}{2} \frac{d}{dt} \vec{v}^{\, 2} \\
   & = \frac{m}{2} \vec{v}_f^{\, 2} - \frac{m}{2} \vec{v}_i^{\, 2}
\end{aligned}
$$
meaning that $m \vec{v}^{\, 2} / 2$ is the energy due to the motion of the particle: the **kinetic energy** $T$:

> [!Definition]
> $$
> \begin{aligned}
>   T = \frac{m}{2} \vec{v}^{\, 2}
> \end{aligned}
> $$

Now, often, the external force acting on the particle is due to a potential $V$:

$$
\begin{aligned}
  \vec{F}_{\text{ext}} & = -\nabla V
\end{aligned}
$$

For example, for a 1D spring, the potential is given by

[!example] 1D Spring/ Harmonic Potential
1D spring/ Harmonic potential}{
  \vspace*{-2em}
  \begin{aligned}
    V & = \frac{1}{2} k x^2 \implies F_{\text{ext}} = -k x
  \end{aligned}
}
or the electrostatic potential:
\eg{Electrostatic potential}{
  \vspace*{-2em}
  \begin{aligned}
    V & = \frac{1}{4 \pi \varepsilon_0} \frac{q_1 q_2}{r} \implies F_{\text{ext}} = -\nabla V = -\frac{q_1 q_2}{4 \pi \varepsilon_0 r^2} \hat{r}
  \end{aligned}
}

## Motivation for Analytical Mechanics

Now, for a particle whose the external forces are given by a potential:
\begin{aligned}
  m \odv[2]{\vec{r}}{t} & = - \nabla V \iff - m \odv[2]{\vec{r}}{t} - \nabla V = 0
\end{aligned}
This looks as if the forces $-\nabla V$ and $m \ddot{\vec{r}}$ are in equilibrium.
So, if we move a particle by an infinitisimal distance $\fdif{\vec{r}}$, the total work done by these forces must be zero:
\begin{aligned}
  \pab{- m \odv[2]{\vec{r}}{t} - \nabla V} \cdot \fdif{\vec{r}} & = 0
\end{aligned}
at any time $t$. We want to apply this for entire path of the motion of the particle, from $t_i$ to $t_f$.
Then, the integral of this equation over the time interval $[t_i, t_f]$ gives
\begin{aligned}
  \fdif{I} & = \int_{t_i}^{t_f} \odif{t} \, \pab{- m \odv[2]{\vec{r}}{t} - \nabla V} \cdot \fdif{\vec{r}} = 0 \label{eq:eom-variation}
\end{aligned}
now, we can apply integration by parts:
\begin{aligned}
  \odv{}{t} \bab{\dot{\vec{r}} \cdot \fdif{\vec{r}}}
   & = \ddot{\vec{r}} \cdot \fdif{\vec{r}} + \dot{\vec{r}} \cdot \odv{\fdif{\vec{r}}}{t}                           \\
   & = \ddot{\vec{r}} \cdot \fdif{\vec{r}} + \dot{\vec{r}} \cdot \fdif{\dot{\vec{r}}}                              \\
  \iff \quad - m \ddot{\vec{r}}
   & = - \odv{}{t} \pab{\dot{\vec{r}} \cdot \fdif{\vec{r}}} + \dot{\vec{r}} \cdot \fdif{\dot{\vec{r}}}             \\
   & = - \odv{}{t} \pab{m \dot{\vec{r}} \cdot \fdif{\vec{r}}} + \delta \pab{\frac{m}{2} \pab{\odv{\vec{r}}{t}}^2},
\end{aligned}
where we used the commutitivity of $\odv{(\cdot)}{t}$ and $\fdif{(\cdot)}$.
Then the integral becomes
\begin{aligned}
  \fdif{I}            & = \int_{t_i}^{t_f} \odif{t} \, \pab{
    \delta \bab{\frac{m}{2} \pab{\odv{\vec{r}}{t}}^2}
    - \fdif{V}
  }                                                                                                   \\
                      & = \int_{t_i}^{t_f} \odif{t} \, \pab{
    \fdif{T} - \fdif{V}
  } = 0                                                                                               \\
  \iff \quad \fdif{I} & = \delta \int_{t_i}^{t_f} \odif{t} \, (T - V) = 0 \label{eq:newton-variation}
\end{aligned}
\cite{maeno-leastAction}

\subsection{Lagrangian and Variational Principle}
In Lagrangian mechanics, we will use a different approach to describe the motion of a particle than the Newtonian mechanics.
Instead of using the usual Euclidean space, we will use a \textit{configuration space} $\mathcal{C}$, which is the space of all possible positions of the particle.
This space is spanned by the so-called \emph{generalized coordinates} $q_i$, and their time derivatives (or generalized velocity) $\dot{q_i} := \odv{q_i}{t}$.
Now, let us define quantities called the \emph{Lagrangian} $L$ and \emph{action} $S$:
\dfn{Lagrangian $L$ and Action $S$}{
  The Lagrangian $L$ is defined as the difference between the kinetic energy $T$ and potential energy $V$ of a particle:
  \begin{aligned}
    L & := T - V, \qquad  S[L] := \int_{t_i}^{t_f} \odif{t} \, L
  \end{aligned}
}

Now, \emph{variation} of the action $\fdif{S}$ is given by
\begin{aligned}
  \fdif{S} & = \delta \int_{t_i}^{t_f} \odif{t} \, (T - V)
\end{aligned}
which is an identical expression to \eqref{eq:newton-variation}.
So, we postulate that the motion of the particle is such that the action is stationary:
\prcp{Variational Principle}{
  The motion of a particle is such that the action $S$ is stationary, i.e., $\fdif{S} = 0$.
  \begin{aligned}
    \fdif{S} & = \delta \int_{t_i}^{t_f} \odif{t} \, L(q_i(t), \dot{q_i}(t), t)= 0
  \end{aligned}
}

As to show why this maybe useful, let us compare between \cref{eq:eom-variation}:
\begin{aligned}
  \fdif{I} = \fdif{S}[L] & = \int_{t_i}^{t_f} \odif{t} \, \pab{- m \odv[2]{\vec{r}}{t} - \nabla V} \cdot \fdif{\vec{r}} = 0
\end{aligned}
and \cref{eq:func_deriv_euler_lagrange}:
\begin{aligned}
  \fdif{I} = \fdif{S}[f] & = \int_B^A \odif{x} \, \pab{\pdv{F}{f} - \odv{}{x} \pdv{F}{\odv{f}{x}}} \fdif{f} = 0
\end{aligned}
which immidiately gives that the EoM is the Euler-Lagrange equation, if we set $F = L(q_i, \dot{q_i}, t)$:
\begin{aligned}
  \pdv{L}{q_i} - \odv{}{t} \pab{\pdv{L}{\dot{q_i}}} & = 0 \iff m \odv[2]{\vec{r}}{t} = - \nabla V
\end{aligned}

The generalization to multiple particles is straightforward:
\begin{aligned}
  L & = \sum_{n} \frac{m_n}{2} \dot{\vec{r}}_n^2 - V(\vec{r}_1, \vec{r}_2, \ldots, \vec{r}_N)
\end{aligned}
The Euler-Lagrange equation is given by
\begin{aligned}
  \pdv{L}{\vec{r}_i^{\, (N)}} - \odv{}{t} \pab{\pdv{L}{\dot{\vec{r}}_i^{\, (N)}}} & = 0
\end{aligned}

\subsection{Harmonic Oscillator}
\label{sec:lagrange-harmonic-oscillator}
Let us consider a particle of mass $m$ in a 1D harmonic potential:
\begin{aligned}
  V & = \frac{1}{2} k x^2 \implies F_{\text{ext}} = - \nabla V = -k x
\end{aligned}
then the Lagrangian is given by
\begin{aligned}
  L & = T - V = \frac{m}{2} \dot{x}^2 - \frac{1}{2} k x^2
\end{aligned}
The Euler-Lagrange equation yields
\begin{alignat}{2}
   &          & \pdv{L}{x} - \odv{}{t} \pab{\pdv{L}{\dot{x}}} = 0 \implies \pdv{L}{x} & = -k x, \quad \pdv{L}{\dot{x}} = m \dot{x} \\
   & \implies & \quad -k x - \odv{}{t} (m \dot{x})                                    & = 0                                        \\
   & \implies & \quad m \odv[2]{x}{t}                                                 & = -k x
\end{alignat}
which is the equation of motion of a harmonic oscillator in Newtonian mechanics.
Here, notice that
\begin{aligned}
  \pdv{L}{x} & = -k x = - \nabla V = F_{\text{ext}}
\end{aligned}
and
\begin{aligned}
  \pdv{L}{\dot{x}} & = m \dot{x} = p
\end{aligned}
these derivatives of the Lagrangian are the \emph{generalized force} and \emph{conjugate momentum}, respectively.
\begin{aligned}
  \pdv{L}{q} & = F_{\text{g}}, \quad \pdv{L}{\dot{q}} = p_{\text{g}}
\end{aligned}


