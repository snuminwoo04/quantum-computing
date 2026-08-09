# Ion-Trap Quantum Computing Study Notes

## 1. Study Goal

이 문서는 trapped-ion(ion-trap) 기반 양자컴퓨터 하드웨어를 공부하기 위한 입문 노트다. 전기정보공학부 학부 2학년 수료 수준을 기준으로, 전자기학과 기초 양자역학에서 출발해 ion-trap qubit과 quantum gate까지 연결하는 것을 목표로 한다.

---

## 2. 가장 중요한 출발 논문

### Cirac & Zoller (1995)

**J. I. Cirac and P. Zoller, “Quantum Computations with Cold Trapped Ions,” Physical Review Letters 74, 4091 (1995).**

이 논문은 trapped-ion quantum computing의 대표적인 출발점이다.

핵심 아이디어는 다음과 같다.

- ion의 내부 전자 상태를 qubit으로 사용한다.
- 여러 ion이 공유하는 진동 모드(collective motional mode)를 이용한다.
- 레이저를 이용해 internal state와 motional state를 결합한다.
- 이 진동 모드를 quantum bus처럼 사용해 서로 다른 ion 사이에 entanglement와 two-qubit gate를 구현한다.

다만 PRL 논문이라 매우 압축되어 있기 때문에, 입문자가 처음부터 모든 수식을 이해하기에는 어렵다.

---

## 3. 먼저 읽기 좋은 Review Paper

### Leibfried, Blatt, Monroe & Wineland (2003)

**D. Leibfried, R. Blatt, C. Monroe, and D. Wineland, “Quantum dynamics of single trapped ions,” Reviews of Modern Physics 75, 281 (2003).**

이 논문은 ion trap을 공부할 때 교과서처럼 참고하기 좋은 review paper다.

주요 내용:

- Paul trap의 기본 원리
- trapped ion의 고전적 운동
- quantized harmonic motion
- laser-ion interaction
- Doppler cooling
- resolved-sideband cooling
- internal state와 motional state의 결합

처음부터 끝까지 읽기보다 필요한 부분을 선택적으로 읽는 방식이 좋다.

### Wineland et al. (1998)

**“Experimental Issues in Coherent Quantum-State Manipulation of Trapped Atomic Ions”**

실험적인 관점에서 trapped-ion quantum logic, coherent control, decoherence 등의 문제를 이해하는 데 중요한 review다.

---

## 4. 추천 공부 순서

### Step 1. Paul Trap의 고전역학

먼저 ion을 실제 공간에 어떻게 가두는지 이해해야 한다.

공부할 개념:

- Earnshaw's theorem
- quadrupole potential
- RF electric field
- Mathieu equation
- secular motion
- micromotion

중요한 질문:

> 왜 정전기장만으로는 charged particle을 3차원 공간에 안정적으로 가둘 수 없는가?

Paul trap에서는 시간에 따라 변하는 RF 전기장을 사용하여 이 문제를 해결한다.

대표적인 potential은

\[
\Phi(x,y,t)
=
\frac{V_{\mathrm{RF}}\cos(\Omega t)}{2r_0^2}(x^2-y^2)
\]

형태로 나타낼 수 있다.

이 potential에서 전기장을 구하고 Newton equation

\[
m\ddot{x}=qE_x
\]

을 세우면 Mathieu equation 형태의 운동방정식이 나타난다.

---

### Step 2. Trapped Ion의 양자화된 운동

ion이 trap 안에서 작은 진동을 한다고 보면 harmonic oscillator로 근사할 수 있다.

Hamiltonian:

\[
H=\frac{p^2}{2m}+\frac12m\omega^2x^2
\]

양자역학적으로는

\[
H=\hbar\omega\left(a^\dagger a+\frac12\right)
\]

로 표현된다.

공부할 개념:

- quantum harmonic oscillator
- creation operator \(a^\dagger\)
- annihilation operator \(a\)
- number state \(|n\rangle\)
- zero-point motion
- phonon
- collective vibrational mode

여기서 ion의 진동 상태는 나중에 여러 ion 사이의 quantum information을 전달하는 역할을 한다.

---

### Step 3. Ion의 Internal State를 Qubit으로 사용

ion의 두 내부 에너지 준위를

\[
|g\rangle,\quad |e\rangle
\]

으로 두고 qubit을 정의할 수 있다.

예를 들어

\[
|0\rangle \equiv |g\rangle
\]

\[
|1\rangle \equiv |e\rangle
\]

처럼 사용할 수 있다.

실제 trapped-ion qubit에는 다음과 같은 형태가 있다.

- optical qubit
- hyperfine qubit
- Zeeman qubit

공부할 개념:

- two-level atom
- energy level
- spontaneous emission
- hyperfine splitting
- Zeeman splitting

---

## 5. Laser-Ion Interaction

레이저는 ion의 internal state를 조작하는 핵심 수단이다.

가장 먼저 이해해야 하는 현상은 Rabi oscillation이다.

레이저가 두 에너지 준위를 resonant하게 구동하면

\[
|g\rangle \leftrightarrow |e\rangle
\]

전이가 주기적으로 일어난다.

공부할 개념:

- Rabi frequency
- detuning
- rotating-wave approximation (RWA)
- laser phase
- pulse area
- \(\pi\)-pulse
- \(\pi/2\)-pulse

---

## 6. Carrier와 Sideband Transition

trapped ion에서는 internal state와 motional state를 함께 나타내야 한다.

상태를

\[
|g,n\rangle
\]

처럼 나타낸다.

여기서

- \(g\): internal state
- \(n\): vibrational quantum number

이다.

### Carrier transition

운동 상태를 바꾸지 않고 internal state만 변화한다.

\[
|g,n\rangle
\leftrightarrow
|e,n\rangle
\]

### Red sideband

internal excitation과 함께 phonon 하나를 제거한다.

\[
|g,n\rangle
\leftrightarrow
|e,n-1\rangle
\]

### Blue sideband

internal excitation과 함께 phonon 하나를 추가한다.

\[
|g,n\rangle
\leftrightarrow
|e,n+1\rangle
\]

이 sideband transition은 trapped-ion quantum computing에서 매우 중요하다.

---

## 7. Lamb-Dicke Regime

레이저와 ion의 상호작용에서 자주 등장하는 중요한 조건이다.

Lamb-Dicke parameter를 보통

\[
\eta = kx_0
\]

형태로 정의한다.

여기서

- \(k\): laser wave vector
- \(x_0\): ion의 ground-state wavepacket 크기

이다.

\(\eta \ll 1\)이면 ion의 운동 범위가 레이저 파장보다 충분히 작다는 뜻이다.

이 조건에서는

\[
e^{i\eta(a+a^\dagger)}
\]

를 Taylor expansion하여

\[
e^{i\eta(a+a^\dagger)}
\approx
1+i\eta(a+a^\dagger)
\]

처럼 근사할 수 있다.

이 근사로 carrier, red sideband, blue sideband를 명확하게 분리해서 이해할 수 있다.

---

## 8. Laser Cooling

quantum gate를 정확하게 수행하려면 ion의 운동을 매우 낮은 에너지 상태까지 냉각해야 한다.

### Doppler Cooling

laser detuning과 Doppler shift를 이용해 ion의 평균 운동 에너지를 낮춘다.

### Resolved-Sideband Cooling

red sideband transition을 반복적으로 이용해

\[
n \rightarrow n-1
\]

과정을 수행한다.

궁극적으로

\[
|n=0\rangle
\]

motional ground state에 가까운 상태를 만든다.

---

## 9. Cirac-Zoller Gate의 핵심 아이디어

여러 ion이 같은 trap 안에 존재하면 collective vibrational mode를 공유한다.

이를 이용하면

\[
\text{Ion 1 internal state}
\]

↓

\[
\text{collective motional state}
\]

↓

\[
\text{Ion 2 internal state}
\]

형태로 quantum information을 전달할 수 있다.

즉,

> ion의 진동 모드가 서로 떨어진 qubit 사이의 quantum bus 역할을 한다.

이것이 Cirac-Zoller trapped-ion gate의 가장 중요한 아이디어 중 하나다.

---

## 10. 전체 학습 로드맵

```text
Electromagnetics
       ↓
Quadrupole electric potential
       ↓
Paul trap
       ↓
Mathieu equation
       ↓
Secular motion / Micromotion
       ↓
Quantum harmonic oscillator
       ↓
Quantized ion motion
       ↓
Two-level atom
       ↓
Laser-ion interaction
       ↓
Rabi oscillation
       ↓
Lamb-Dicke regime
       ↓
Carrier / Red sideband / Blue sideband
       ↓
Sideband cooling
       ↓
Internal state + Motional state coupling
       ↓
Cirac-Zoller gate
       ↓
Trapped-ion quantum computer
```

---

## 11. 현재 첫 번째 공부 목표

가장 먼저 다음 질문에 답할 수 있도록 공부한다.

> **Paul trap은 어떻게 시간에 따라 변하는 전기장을 사용해 ion을 안정적으로 가두는가?**

이를 이해하기 위해 다음 순서로 공부한다.

1. Earnshaw's theorem
2. quadrupole potential
3. RF potential
4. ion의 Newton equation
5. Mathieu equation
6. Mathieu equation의 stable solution
7. secular motion
8. micromotion
9. pseudopotential approximation

이 부분은 전자기학과 미분방정식 수준에서 접근할 수 있으며, 이후 trapped ion을 양자 harmonic oscillator로 취급하는 단계로 연결된다.

---

## Important Papers

1. J. I. Cirac and P. Zoller, **Quantum Computations with Cold Trapped Ions**, Phys. Rev. Lett. 74, 4091 (1995).
2. D. Leibfried, R. Blatt, C. Monroe, and D. Wineland, **Quantum dynamics of single trapped ions**, Rev. Mod. Phys. 75, 281 (2003).
3. D. J. Wineland et al., **Experimental Issues in Coherent Quantum-State Manipulation of Trapped Atomic Ions** (1998).
4. C. Monroe et al., **Demonstration of a Fundamental Quantum Logic Gate**, Phys. Rev. Lett. 75, 4714 (1995).

---

## Study Method

앞으로 논문을 읽으면서 이해되지 않는 문장이나 수식을 기록한다.

예:

- "Lamb-Dicke regime이 정확히 무엇인가?"
- "왜 \(e^{i\eta(a+a^\dagger)}\)가 등장하는가?"
- "Mathieu equation은 어떻게 유도되는가?"
- "왜 red sideband를 사용하면 cooling이 되는가?"
- "collective motional mode가 어떻게 두 qubit을 연결하는가?"

각 질문은 필요한 배경 개념까지 내려가서 다시 정리한다.
