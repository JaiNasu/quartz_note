---
Title: "Lagrange Formalism"
author: "Jai Nasu"
date: "2025-08-19"
tags: [Analytical Mechanics, Lagrangian Mechanics]
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

and the relations between these quantities, in presence of external forces $\vec{F}_{\text{ext}}^{(i)}$ acting on the particle, are given by **Newton's second law**:

$$
\begin{aligned}
  \frac{d\vec{p}}{dt} = m \frac{d^2\vec{r}}{dt^2} = \sum_i \vec{F}_{\text{ext}}^{(i)}
\end{aligned}
$$

The work done by such forces is given by the inner product of the motion and the force:
$$
\begin{aligned}
  W_{\text{total}} & = \sum_i \int_l d{\vec{x}} \cdot \vec{F}_{\text{ext}}^{(i)}
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

> [!Definition] Definition: Kinetic Energy
> $$
> \begin{aligned}
>   T = \frac{m}{2} \vec{v}^{\, 2}
> \end{aligned}
> $$

Now, often, an external force acting on the particle is due to a potential $V$:
$$
\begin{aligned}
  \vec{F}_{\text{ext}} & = -\nabla V
\end{aligned}
$$

For example, for a 1D spring, the potential $V$ is given by
> [!example] Example: 1D Spring/ Harmonic Potential
> $$
>   \begin{aligned}
>     V & = \frac{1}{2} k x^2 \implies F_{\text{ext}} = -k x
>   \end{aligned}
> $$
or the electrostatic potential:
> [!example] Electrostatic potential
> $$
> \begin{aligned}
>  V & = \frac{1}{4 \pi \varepsilon_0} \frac{q_1 q_2}{r} \implies F_{\text{ext}} = -\nabla V = -\frac{q_1 q_2}{4 \pi \varepsilon_0 r^2} \hat{r}
> \end{aligned}
> $$

## D'Alembert's Principle

Now, for a particle whose the external forces are given by a potential:
$$
\begin{aligned}
  m \frac{d^2\vec{r}}{dt^2} & = - \nabla V \iff - m \frac{d^2\vec{r}}{dt^2} - \nabla V = 0
\end{aligned}
$$
This looks as if the forces $-\nabla V$ and $m \ddot{\vec{r}}$ are in equilibrium.
So, if we move a particle by an infinitisimal distance $\delta \vec{r}$, the total work done by these forces must be zero:
$$
\begin{aligned}
  \left( - m \frac{d^2\vec{r}}{dt^2} - \nabla V \right) \cdot \delta \vec{r} & = 0
\end{aligned}
$$
at any time $t$. We want to apply this for entire path of the motion of the particle, from $t_i$ to $t_f$.
This is called **D'Alembert's Principle**.

## Action and Lagrangian

Then, the integral of this equation over the time interval $[t_i, t_f]$ gives
$$
\begin{aligned}
  \delta I = \int_{t_i}^{t_f} dt \, \left(- m \frac{d^2\vec{r}}{dt^2} - \nabla V \right) \cdot \delta \vec{r} = 0
\end{aligned}
$$
now, we can apply integration by parts:
$$
\begin{aligned}
  \frac{d}{dt} \left[\dot{\vec{r}} \cdot \delta \vec{r}\right]
   & = \ddot{\vec{r}} \cdot \delta \vec{r} + \dot{\vec{r}} \cdot \frac{d\delta \vec{r}}{dt}                           \\
   & = \ddot{\vec{r}} \cdot \delta \vec{r} + \dot{\vec{r}} \cdot \delta \dot{\vec{r}}                              \\
  \iff \quad - m \ddot{\vec{r}}
   & = - \frac{d}{dt} \left(\dot{\vec{r}} \cdot \delta \vec{r} \right) + \dot{\vec{r}} \cdot \delta \dot{\vec{r}}             \\
   & = - \frac{d}{dt} \left(m \dot{\vec{r}} \cdot \delta \vec{r}\right) + \delta \left(\frac{m}{2} \dot{\vec{r}}^2\right),
\end{aligned}
$$
where we used the commutitivity of $\frac{d(\cdot)}{dt}$ and $\delta {(\cdot)}$.
Then the integral becomes
$$
\begin{aligned}
  \delta I            & = \int_{t_i}^{t_f} dt \, \left(
    \delta \left[\frac{m}{2} \left(\frac{d\vec{r}}{dt}\right)^2\right]
    - \delta V
  \right)                                                                                                   \\
                      & = \int_{t_i}^{t_f} dt \, \left(
    \delta T - \delta V
  \right) = 0                                                                                               \\
  \iff \quad \delta I & = \delta \int_{t_i}^{t_f} dt \, (T - V) = 0
\end{aligned}
$$
\cite{maeno-leastAction}

\subsection{Lagrangian and Variational Principle}
In Lagrangian mechanics, we will use a different approach to describe the motion of a particle than the Newtonian mechanics.
Instead of using the usual 3D Euclidean space, we will use a **configuration space** of a system.
This space is spanned by the so-called **generalized coordinate** $q_i$, and their time derivatives (or generalized velocity) $\dot{q_i}$.
Now, let us define quantities called **Lagrangian** $L$ and **action** $S$:
> [!definition] Lagrangian $L$ and Action $S$
> Lagrangian $L$ is defined as the difference between the kinetic energy $T$ and potential energy $V$ of a particle:
> $$
> \begin{aligned}
>   L & := T - V, \qquad  S[L] := \int_{t_i}^{t_f} dt \, L
> \end{aligned}
> $$

Now, **variation** of the action $\delta {S}$ is given by
$$
\begin{aligned}
  \delta {S} & = \delta \int_{t_i}^{t_f} dt \, (T - V)
\end{aligned}
$$
which is an identical expression to \eqref{eq:newton-variation}.

## Variational Principle

So, we postulate that the motion of the particle is such that the action is stationary:
> [!principle] Variational Principle
> The motion of a particle is such that the action $S$ is stationary, i.e., $\delta {S} = 0$.
> $$
> \begin{aligned}
>   \delta {S} & = \delta \int_{t_i}^{t_f} dt \, L(q_i(t), \dot{q_i}(t), t)= 0
> \end{aligned}
> $$

As to show why this maybe useful, let us compare between \cref{eq:eom-variation}:
$$
\begin{aligned}
  \delta{I} = \delta{S}[L] & = \int_{t_i}^{t_f} dt \, \left(- m \frac{d^2\vec{r}}{dt^2} - \nabla V\right) \cdot \delta{\vec{r}} = 0
\end{aligned}
$$
and \cref{eq:func_deriv_euler_lagrange}:
$$
\begin{aligned}
  \delta{I} = \delta{S}[f] & = \int_B^A dx \, \left(
    \frac{\partial F}{\partial f} - \frac{d}{dx} \frac{\partial F}{\partial \left(\frac{df}{dx}\right)}
    \right) \delta{f} = 0
\end{aligned}
$$
which immidiately gives that the EoM is the Euler-Lagrange equation, if we set $F = L(q_i, \dot{q_i}, t)$:
$$
\begin{aligned}
  \frac{\partial L}{\partial q_i} - \frac{d}{dt} \left(\frac{\partial L}{\partial \dot{q_i}}\right) & = 0 \iff m \frac{d^2\vec{r}}{dt^2} = - \nabla V
\end{aligned}
$$
The generalization to multiple particles is straightforward:
$$
\begin{aligned}
  L & = \sum_{n} \frac{m_n}{2} \dot{\vec{r}}_n^2 - V(\vec{r}_1, \vec{r}_2, \ldots, \vec{r}_N)
\end{aligned}
$$
The Euler-Lagrange equation is given by
$$
\begin{aligned}
  \frac{\partial L}{\partial \vec{r}_i^{\, (N)}} - \frac{d}{dt} \left(\frac{\partial L}{\partial \dot{\vec{r}}_i^{\, (N)}}\right) & = 0
\end{aligned}
$$

## Harmonic Oscillator

Let us consider a particle of mass $m$ in a 1D harmonic potential:
$$
\begin{aligned}
  V & = \frac{1}{2} k x^2 \implies F_{\text{ext}} = - \nabla V = -k x
\end{aligned}
$$
then the Lagrangian is given by
$$
\begin{aligned}
  L & = T - V = \frac{m}{2} \dot{x}^2 - \frac{1}{2} k x^2
\end{aligned}
$$
The Euler-Lagrange equation yields
$$
\begin{aligned}
   &          & \frac{\partial L}{\partial x} - \frac{d}{dt} \left(\frac{\partial L}{\partial \dot{x}}\right) = 0 \implies \frac{\partial L}{\partial x} & = -k x, \quad \frac{\partial L}{\partial \dot{x}} = m \dot{x} \\
   & \implies & \quad -k x - \frac{d}{dt} (m \dot{x})                                    & = 0                                        \\
   & \implies & \quad m \frac{d^2x}{dt^2}                                                 & = -k x
\end{aligned}
$$
which is the equation of motion of a harmonic oscillator in Newtonian mechanics.
Here, notice that
$$
\begin{aligned}
  \frac{\partial L}{\partial x} & = -k x = - \nabla V = F_{\text{ext}}
\end{aligned}
$$
and
$$
\begin{aligned}
  \frac{\partial L}{\partial \dot{x}} & = m \dot{x} = p
\end{aligned}
$$
these derivatives of the Lagrangian are the **generalized force** and **conjugate momentum**, respectively.
$$
\begin{aligned}
  \frac{\partial L}{\partial q} & = F_{\text{g}}, \quad \frac{\partial L}{\partial \dot{q}} = p_{\text{g}}
\end{aligned}
$$
