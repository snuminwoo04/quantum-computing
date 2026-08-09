# Quantum computing with trapped ions: a beginner's guide

## Study Note 01 — Generic Unitary and Pauli Rotations

논문의 식 (2):

\[
U=e^{i\alpha}e^{i n_j\sigma_j\theta/2}\equiv e^{i\alpha}R_{\hat n}(\theta),
\qquad \hat n=(n_x,n_y,n_z),\quad \hat n\cdot\hat n=1
\]

### 1. \(\sigma_j\)와 Einstein summation convention

\(\sigma_j\)는 Pauli operator(Pauli matrix)를 의미한다.

\[
\sigma_x=\begin{pmatrix}0&1\\1&0\end{pmatrix},\qquad
\sigma_y=\begin{pmatrix}0&-i\\i&0\end{pmatrix},\qquad
\sigma_z=\begin{pmatrix}1&0\\0&-1\end{pmatrix}.
\]

논문의 \(n_j\sigma_j\)는 반복되는 index \(j\)에 대해 합을 취하는 Einstein summation convention을 사용한 것이다.

\[
n_j\sigma_j=n_x\sigma_x+n_y\sigma_y+n_z\sigma_z.
\]

따라서

\[
U=e^{i\alpha}e^{i\frac{\theta}{2}(n_x\sigma_x+n_y\sigma_y+n_z\sigma_z)}.
\]

### 2. 회전축 \(\hat n\)

\[
\hat n=(n_x,n_y,n_z),\qquad n_x^2+n_y^2+n_z^2=1
\]

은 Bloch sphere에서 회전축의 방향을 나타내는 단위벡터다. 예를 들어 \(\hat n=(1,0,0)\)이면 \(n_j\sigma_j=\sigma_x\)이므로 x축 회전에 해당한다.

### 3. Pauli matrix의 exponential과 회전

Pauli matrix는 \(\sigma_x^2=I\)를 만족한다. 따라서

\[
e^{i\theta\sigma_x/2}=I\cos\frac{\theta}{2}+i\sigma_x\sin\frac{\theta}{2}.
\]

일반적인 축에 대해서도 \((\hat n\cdot\boldsymbol{\sigma})^2=I\)이므로

\[
R_{\hat n}(\theta)=I\cos\frac{\theta}{2}+i(\hat n\cdot\boldsymbol{\sigma})\sin\frac{\theta}{2}.
\]

양자정보 교재에서는 \(R_{\hat n}(\theta)=e^{-i\theta\hat n\cdot\sigma/2}\)처럼 반대 부호 convention을 사용하는 경우도 많다.

### 4. 왜 \(\theta/2\)인가?

Qubit은 spin-1/2 시스템과 같은 수학적 구조를 가지며 Bloch sphere의 일반적인 상태는

\[
|\psi\rangle=\cos\frac{\vartheta}{2}|0\rangle+e^{i\phi}\sin\frac{\vartheta}{2}|1\rangle
\]

처럼 half-angle을 포함한다. 따라서 Bloch vector를 \(\theta\)만큼 회전시키는 unitary에는 \(\theta/2\)가 들어간다.

### 5. Global phase \(e^{i\alpha}\)

\[
|\psi'\rangle=e^{i\alpha}|\psi\rangle
\]

처럼 전체 상태에 동일한 phase가 곱해져도 측정확률은 변하지 않는다. 따라서 \(e^{i\alpha}\)는 global phase이며, 논문의 “modulo a phase factor”는 이 global phase를 제외하면 된다는 의미다.

### 6. 모든 single-qubit unitary와 Bloch sphere rotation

일반적인 single-qubit unitary는 \(U(2)\)의 원소이고, global phase와 \(SU(2)\) 회전으로 나눌 수 있다. 따라서

\[
U=e^{i\alpha}e^{i\frac{\theta}{2}\hat n\cdot\sigma}.
\]

즉 물리적으로 single-qubit gate는 Bloch sphere에서 어떤 축 \(\hat n\)을 중심으로 상태를 얼마나 회전시키는가로 이해할 수 있다.

### 7. Trapped-ion quantum computing과의 연결

Trapped-ion qubit에서는 이온의 두 internal state를 \(|0\rangle\), \(|1\rangle\)로 정하고 laser 또는 microwave field로 두 상태를 coupling한다. 적절한 pulse의 amplitude, duration, phase, detuning을 조절하여 \(R_x(\theta)\), \(R_y(\theta)\) 등의 single-qubit rotation을 구현할 수 있다.

따라서 이후 등장하는 Rabi oscillation과 laser-ion interaction은 결국 이 \(R_{\hat n}(\theta)\)를 실제 trapped-ion hardware에서 구현하는 과정으로 연결해서 이해하면 된다.
