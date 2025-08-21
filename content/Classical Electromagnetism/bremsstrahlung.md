---
title: Bremsstrahlung
author: Jai Nasu
date: 2025-08-19
tags: [Classical Electromagnetism]
---

## 概要
相対論的速度$v \approx c$をもった粒子が衝撃波の上流と下流を往復しながら加速される現象を**bremsstrahlung**と呼ぶ。

上流にある波面の慣性系から見た速度$\vec{v}$とエネルギー$E$をもつ粒子が衝撃波に衝突したとき、衝撃波の速度を$u_1$、下流の慣性系の速度を$u_2$とすると、
エネルギーと運動量の関係は
\begin{align}
  E^2 & = p^2 c^2 + m^2 c^4
\end{align}
ここで$v \approx c$より$p \approx m c$と書けるので
\begin{align}
  E & \approx p c \iff p = \frac{E}{c}
\end{align}
と書ける。
また、粒子の速度が大きいとき$(v \approx c)$、密度の比は
\begin{align}
  \frac{\rho_1}{\rho_2} & = \frac{\gamma - 1}{\gamma + 1}
\end{align}
となる。\cite{spitzer-phys-process}
また、下流から$x$方向に飛んでいく(往復する\&しない)粒子のfluxは時間平均的に
\begin{align}
  n_2 u_2
\end{align}
と書け、下流から波面を通過する速度$v \approx c$粒子のfluxは
\begin{align}
  \frac{1}{4} n_2 c
\end{align}
なので、粒子が放出される(下流から上流に戻らない粒子)の割合$1 - P$は
\begin{align}
  1 - P = \frac{\text{往復しない粒子}}{\text{往復する粒子}} = \frac{n_2 u_2}{\frac{1}{4} n_2 c} = \frac{4 u_2}{c}
\end{align}

また、流体の連続の式から
\begin{align}
  \pdv{\rho}{t} + \nabla \cdot (\rho \vec{u}) & = 0
\end{align}
定常状態$\pdif{t} = 0$と考えて
\begin{align}
  \nabla \cdot (\rho \vec{u}) & = 0
\end{align}
ここで$\rho$と$\vec{u}$が$x$軸方向にのみ依存するとすると
\begin{align}
  \pdv{(\rho \vec{u})}{x} & = 0
\end{align}
つまりどんな二点においても
\begin{align}
  \rho_1 u_1 & = \rho_2 u_2 \quad \text{(mass conservation)}
\end{align}
が成り立つ。

下流の慣性系$u_2$では上流の粒子は$-V=-(u_1 - u_2)$の速度で移動しているので、
粒子と$x$軸のなす角を$\theta_1$とすると、
下流の慣性系から見た粒子のエネルギーは
\begin{align}
  E_{\text{down}}                             & = \gamma_2 \pab{E - (-\vec{V}) \cdot \vec{p}} \\
                                              & = \gamma_2 \pab{E + V p \cos \theta_1}        \\
  \implies \quad E_{\text{down}} - \gamma_2 E & = \gamma_2 V p \cos \theta_1
\end{align}
$u_2 \ll c$のとき、$\gamma_2 \approx 1$なので
\begin{align}
  E_{\text{down}} - E \approx V p \cos \theta_1 \approx \frac{V \cos \theta_1}{c} E
\end{align}
この粒子が弾性散乱で衝撃波の上流に戻ると考えると,
粒子が下流から上流に戻るときのエネルギーは
\begin{align}
  E_{\text{up}} & = \gamma_1 \pab{E_{\text{down}} - \vec{V} \cdot (-\vec{p})} \\
                & = \gamma_1 \pab{E_{\text{down}} + V p \cos \theta_2}
\end{align}
ここで、$\theta_2$は衝撃波の上流に戻るときの粒子と$x$軸のなす角である。
\begin{align}
  \implies \quad E_{\text{up}} -  E_{\text{down}} & \approx  V p \cos \theta_2 = \frac{V \cos \theta_2}{c} E_{\text{down}}
\end{align}
なので
\begin{align}
  E_{\text{up}} - E
   & \approx  \frac{V \cos \theta_1}{c} E + \frac{V \cos \theta_2}{c} E_{\text{down}}                 \\
   & = - \frac{V \cos \theta_1}{c} E + \frac{V \cos \theta_2}{c} \pab{1 + \frac{V \cos \theta_1}{c}}E \\
   & = \frac{V}{c} \pab{\cos \theta_1 + \cos \theta_2 + \frac{V \cos \theta_1 \cos \theta_2}{c}} E
\end{align}
$V \ll c$なので$V/c$の二次の項は無視して、
\begin{align}
  E_{\text{up}} - E & \approx \frac{V}{c} \pab{\cos \theta_1 + \cos \theta_2} E
  \implies \frac{\Delta E(\theta_1, \theta_2)}{E} \approx \frac{V}{c} \pab{\cos \theta_1 + \cos \theta_2}
\end{align}

ここで、粒子の分布と運動は等方的と考えると、
ある立体角$\odif{\Omega}$から衝撃波面に入射する粒子の数は$\odif{\Omega}$に比例する。
$\odif{\Omega}$を通るfluxは衝撃波に対する角度$\theta$に依存し、
\begin{align}
  p(\theta) & = 2 \cos \theta \sin \theta \odif{\theta}
\end{align}
と書ける。
このとき、$\cos \theta$の平均値は
\begin{align}
  \aab{\cos \theta}
   & = \int_0^{\pi/2} 2 \cos^2 \theta \sin \theta \odif{\theta}    \\
   & = - \bab{\frac{2}{3} \cos^3 \theta}_{0}^{\pi/2} = \frac{2}{3}
\end{align}
となる。
したがって、衝撃波の上流と下流を往復する粒子のエネルギーの変化は平均をとると
\begin{align}
  \aab{\frac{\Delta E}{E}} & \approx 2 \cdot \frac{2}{3} \frac{V}{c} = \frac{4}{3} \frac{V}{c}
\end{align}

散乱はランダムなので、下流と上流に往復しない粒子もある。
粒子が$N$個あるとき、一回の往復で残る粒子の割合は$PN$と書ける。
このとき、粒子一個のエネルギーは$\Delta E$だけ増加するので一往復後の粒子一個あたりのエネルギーは
\begin{align}
  E_{k=1} & = E + \Delta E = \pab{1 + \frac{\Delta E}{E}} E
\end{align}
したがって、$k$回の往復後のエネルギーはおおよそ
\begin{align}
  E_{k} & \approx \pab{1 + \aab{\frac{\Delta E}{E}}}^k E
\end{align}
同様に$k$回の往復後の粒子数は
\begin{align}
  N_{k} & = P^k N
\end{align}
これより$k$は以下のように書けて、
\begin{align}
  k = \frac{1}{\ln P} \ln \frac{N_k}{N} = \frac{1}{\ln \pab{1 + \aab{\frac{\Delta E}{E}}}} \ln \frac{E_k}{E}
\end{align}
粒子数は
\begin{align}
  N_k & = P^k N = P^{\frac{1}{\ln \pab{1 + \aab{\frac{\Delta E}{E}}}} \ln \frac{E_k}{E}} N      \\
      & = N \exp \pab{\frac{1}{\ln \pab{1 + \aab{\frac{\Delta E}{E}}}} \ln \frac{E_k}{E} \ln P} \\
      & = N \pab{\frac{E_k}{E}}^{\frac{1}{\ln \pab{1 + \aab{\frac{\Delta E}{E}}}} \ln P}
\end{align}
ここで$P \approx 1$と仮定すると
\begin{align}
  \ln P = \ln (1 + P - 1) \approx P - 1, \ln \aab{1 + \pab{\frac{\Delta E}{E}}} \approx \aab{\frac{\Delta E}{E}} = \frac{4}{3} \frac{V}{c} \ll 1
\end{align}
これより
\begin{align}
  \Gamma := - \frac{1}{\ln \pab{1 + \aab{\frac{\Delta E}{E}}}} \ln P \approx \frac{1 - P}{\aab{\frac{\Delta E}{E}}}
\end{align}
とおけば
\begin{align}
  N_k & = N \pab{\frac{E_k}{E}}^{-\Gamma}.
\end{align}
また、質量保存と単分子の比熱比$\gamma = 5 / 3$から
\begin{align}
  \frac{u_1}{u_2} & = \frac{\rho_2}{\rho_1} = \frac{\gamma + 1}{\gamma - 1} = 4 \implies V = u_1 - u_2 = 3 u_2
\end{align}
なので
\begin{align}
  \aab{\frac{\Delta E}{E}} & \approx \frac{4}{3} \frac{V}{c} = 4 u_2 / c    \\
  \implies \quad
  \Gamma                   & \approx \frac{1 - P}{\aab{\frac{\Delta E}{E}}}
  = \frac{4 u_2 / c}{4 u_2 / c} = 1
\end{align}
まとめると、最初に粒子数$N_0$、エネルギー$E_0$の粒子があったとき、衝撃波加速を受けた後の全ての粒子数$N_{\text{total}}$はエネルギー$E$の関数として
\begin{align}
  N_{\text{total}} & = N_0 \pab{\frac{E}{E_0}}^{-\Gamma}.
\end{align}
エネルギーあたりの粒子数$N(E)$は
\begin{align}
  N(E) := \odv{N_{\text{total}}}{E} \propto E^{-(\Gamma + 1)} = E^{-2}
\end{align}
これが宇宙線のエネルギースペクトルに対応する。