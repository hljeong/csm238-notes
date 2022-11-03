# 9.22 0th
- first quantum computer working in 2016
- rn = 127 qubits
- google projected to have 1mil qubits by 2029
- largest simulation of a quantum computer by a classical computer: nasa, 70 (perfect) qubits, half a year
  - only need 37 for practical uses
- 1% err rate
  - current err corrections reqs ~1000 qubits to support 1 perfect qubit
- moores law of quantum computing
  - err rate improves linearly per qubit
- quantum volume for the decade: 100 qubits * 1000 ops = 100k ops
  - need to push decoherence time
- good problem: small input, lots of calculation, small output, easily verifiable
- double slit experiment
  - numbers of photons that come thru when either slit is covered are not additive
  - complex $\alpha_1$ and $\alpha_2$ for probability for either, can be negative, amplitude leq 1
  - eg $\alpha_1 = 1 / \sqrt 2$ and $\alpha_2 = -1 / \sqrt 2$
  - probability = $|\alpha|^2$ = $1 / 2$
  - probability when both are uncovered = $|\alpha_1 + \alpha_2|^2$ = 0
- borns rule: when measured, a state with amplitude $\alpha$ is observed with probability $|\alpha|^2$

# 9.27 1t

|                   | classical           | quantum           |
| --:               | :-:                 | :-:               |
| \textbf{software} | boolean algebra     | linear algebra    |
| \textbf{hardware} | classical mechanics | quantum mechanics |

## 4 postulates that define the interface between us and the qubits
1. state space rule
  - $\left \vert 0 \right \rangle = \begin{bmatrix} 1 \\ 0 \end{bmatrix}$
  - $\left \vert 1 \right \rangle = \begin{bmatrix} 0 \\ 1 \end{bmatrix}$
  - $\left ( \frac{1}{\sqrt 2} \left \vert 0 \right \rangle + \frac{1}{\sqrt 2} \left \vert 1 \right \rangle \right )$
2. composition rule
  - tensor product
3. step rule
  - unitary matrix
  - $U \left \vert \psi \right \rangle = \left \vert \varphi \right \rangle$
  - $\left \vert \psi \right \rangle$ and $\left \vert \varphi \right \rangle$ are unit vectors of size $2^n$
  - $U$ is $2^n \times 2^n$ but can be programmed in polynomial amount of code
4. measurement rule
  - bit $\overset{\text{load}}{\longrightarrow}$ quantum $\overset{\text{compute}}{\longrightarrow}$ quantum $\overset{\text{measure}}{\longrightarrow}$ bit

## from classical computing to probabilistic computing to quantum computing
- classical
  - step: $\begin{bmatrix} 0 & 0 & 1 & 0 \\ 1 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 \\ 0 & 1 & 0 & 1 \end{bmatrix}$
    - rows: from $00$, $01$, $10$, $11$
    - cols: to $00$, $01$, $10$, $11$
- probabilistic: model of the world with uncertainties
  - state is a vector, taking a step = multiply by probability matrix
  - step: $\begin{bmatrix} 0 & 0 & 0 & 1 / 4 \\ 1 & 2 / 3 & 1 / 3 & 1 / 4 \\ 0 & 1 / 3 & 1 / 3 & 1 / 4 \\ 0 & 0 & 1 / 3 & 1 / 4 \end{bmatrix}$
  - tensor product: $\begin{bmatrix} p \\ 1 - p \end{bmatrix} \otimes \begin{bmatrix} q \\ 1 - p \end{bmatrix} \rightarrow \begin{bmatrix} p q \\ p (1 - q) \\ (1 - p) q \\ (1 - p) (1 - q) \end{bmatrix}$
  - "not gate": $\begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix} \begin{bmatrix} p \\ q \end{bmatrix} = \begin{bmatrix} q \\ p \end{bmatrix}$
  - fair flip: $\begin{bmatrix} 1 / 2 & 1 / 2 \\ 1 / 2 & 1 / 2 \end{bmatrix} \begin{bmatrix} p \\ q \end{bmatrix} = \begin{bmatrix} \frac{1}{2} (p + q) \\ \frac{1}{2} (p + q) \end{bmatrix} = \begin{bmatrix} 1 / 2 \\ 1 / 2 \end{bmatrix}$
  - $\begin{bmatrix} a \\ b \end{bmatrix} \otimes \begin{bmatrix} c \\ d \end{bmatrix} = \begin{bmatrix} a c \\ a d \\ b c \\ b d \end{bmatrix}$ can never equal $\begin{bmatrix} 1 / 2 \\ 0 \\ 0 \\ 1 / 2 \end{bmatrix}$
    - $\frac{1}{4} = \frac{1}{2} \cdot \frac{1}{2} = (a c) (b d) \neq (a d) (b c) = 0 \cdot 0 = 0$
- comparison between probabilistic and quantum

  |                | probabilistic           | quantum                         |
  | --:            | :-:                     | :-:                             |
  | \textbf{value} | real                    | complex                         |
  | \textbf{state} | vector of probabilities | vector of amplitudes            |
  |                | $\sum p_i = 1$          | $\sum |a|^2 = 1$                |
  | \textbf{step}  | stochastic matrix       | unitary matrix                  |

- quantum
  - fair flip: $H = \begin{bmatrix} \frac{1}{\sqrt 2} & \frac{1}{\sqrt 2} \\ \frac{1}{\sqrt 2} & \frac{-1}{\sqrt 2} \end{bmatrix} = \frac{1}{\sqrt 2} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}$
    - $H \left \vert 0 \right \rangle = \frac{1}{\sqrt 2} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix} \begin{bmatrix} 1 \\ 0 \end{bmatrix} = \frac{1}{\sqrt 2} \begin{bmatrix} 1 \\ 1 \end{bmatrix} = \frac{1}{\sqrt 2} \left \vert 0 \right \rangle + \frac{1}{\sqrt 2} \left \vert 1 \right \rangle$
    - $H \left \vert 1 \right \rangle = \frac{1}{\sqrt 2} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix} \begin{bmatrix} 0 \\ 1 \end{bmatrix} = \frac{1}{\sqrt 2} \begin{bmatrix} 1 \\ 1 \end{bmatrix} = \frac{1}{\sqrt 2} \left \vert 0 \right \rangle + \frac{1}{\sqrt 2} \left \vert 1 \right \rangle$
    - distinguishing $\begin{bmatrix} \frac{1}{\sqrt 2} \\ \frac{1}{\sqrt 2} \end{bmatrix}$ and $\begin{bmatrix} \frac{1}{\sqrt 2} \\ \frac{-1}{\sqrt 2} \end{bmatrix}$: 
      - $H \begin{bmatrix} \frac{1}{\sqrt 2} \\ \frac{1}{\sqrt 2} \end{bmatrix} = \left \vert 0 \right \rangle$
      - $H \begin{bmatrix} \frac{1}{\sqrt 2} \\ \frac{-1}{\sqrt 2} \end{bmatrix} = \left \vert 1 \right \rangle$
  - $f \colon \left \{ 0, 1 \right \} \to \left \{ 0, 1 \right \}$

## encoding a function to be invertible
  - encoding of $f$: $U_f \colon \left \{ 0, 1 \right \}^2 \to \left \{ 0, 1 \right \}^2$
    - $U_f(x, b) = (x, b \oplus f(x))$ invertible
    - $(U_f \circ U_f)(x, b) = U_f(U_f(x, b)) = U_f(x, b \oplus f(x)) = (x, b \oplus f(x) \oplus f(x)) = (x, b)$

# 9.29 1th

## complex numbers
- $a + i b$
- $\overline{a + i b} = a - i b$
- $e^{i \theta} = \cos \theta + i \sin \theta$
- $\overline{e^{i \theta}} = \cos \theta - i \sin \theta = e^{-i \theta}$

## hilbert space
- complex vector space w inner product
- $\left \langle \begin{bmatrix} \alpha_1 \\ \alpha_2 \end{bmatrix}, \begin{bmatrix} \beta_1 \\ \beta_2 \end{bmatrix} \right \rangle = \overline{\alpha_1} \beta_1 + \overline{\alpha_2} \beta_2 = \begin{bmatrix} \alpha_1 \\ \alpha_2 \end{bmatrix}^* \begin{bmatrix} \beta_1 \\ \beta_2 \end{bmatrix} = \begin{bmatrix} \overline{\alpha_1} & \overline{\alpha_2} \end{bmatrix} \begin{bmatrix} \beta_1 \\ \beta_2 \end{bmatrix}$
- write $\left \vert \psi \right \rangle = \begin{bmatrix} \alpha_1 \\ \alpha_2 \end{bmatrix}$ and $\left \langle \varphi \right \vert = \begin{bmatrix} \beta_1 \\ \beta_2 \end{bmatrix}$
- bra-ket notation: $\left \langle \psi \right \vert = \begin{bmatrix} \overline{\alpha_1} & \overline{\alpha_2} \end{bmatrix}$
- inner product: $\mleft \langle \psi \middle \vert \varphi \mright \rangle$
- $\left \vert + \right \rangle = \frac{1}{\sqrt 2} \left ( \left \vert 0 \right \rangle + \left \vert 1 \right \rangle \right )$
- $\left \vert - \right \rangle = \frac{1}{\sqrt 2} \left ( \left \vert 0 \right \rangle - \left \vert 1 \right \rangle \right )$
- $H \left \vert 0 \right \rangle = \left \vert + \right \rangle$
- $H \left \vert 1 \right \rangle = \left \vert - \right \rangle$
- $\mleft \langle 0 \middle \vert 1 \mright \rangle = 1^* \cdot 0 + 0^* \cdot 1 = 0$
- $\mleft \langle + \middle \vert - \mright \rangle = \frac{1}{\sqrt 2} \begin{bmatrix} 1 & 1 \end{bmatrix} \cdot \frac{1}{\sqrt 2} \begin{bmatrix} 1 \\ -1 \end{bmatrix} = \frac{1}{2} (1 \cdot 1 + 1 \cdot (-1)) = 0$
- outer product: $\left \vert \psi \right \rangle \left \langle \varphi \right \vert = \begin{bmatrix} \alpha_1 \\ \alpha_2 \end{bmatrix} \begin{bmatrix} \overline{\beta_1} & \overline{\beta_2} \end{bmatrix} = \begin{bmatrix} \alpha_1 \overline{\beta_1} & \alpha_1 \overline{\beta_2} \\ \alpha_2 \overline{\beta_1} & \alpha_2 \overline{\beta_2} \end{bmatrix}$
- a matrix $U$ is unitary iff $U U^* = I$ (equivalent to $U^* U = I$)

## partial measurement
- start state: $\left \vert \psi \right \rangle = \alpha_{00} \left \vert 00 \right \rangle + \alpha_{01} \left \vert 01 \right \rangle + \alpha_{10} \left \vert 10 \right \rangle + \alpha_{11} \left \vert 11 \right \rangle$
- measure qubit 1 $\longrightarrow 0$
- new sate: $\frac{\alpha_{00} \left \vert 00 \right \rangle + \alpha_{01} \left \vert 01 \right \rangle}{\sqrt{\left | \alpha_00 \right |^2 + \left | \alpha_01 \right |^2}} = \left \vert 0 \right \rangle \otimes \frac{\alpha_{00} \left \vert 0 \right \rangle + \alpha_{01} \left \vert 1 \right \rangle}{\sqrt{\left | \alpha_00 \right |^2 + \left | \alpha_01 \right |^2}}$

## generalization of tensor product
- outer product: $\left \vert \psi \right \rangle \left \langle \varphi \right \vert = \begin{bmatrix} \alpha_1 \\ \alpha_2 \end{bmatrix} \otimes \begin{bmatrix} \overline{\beta_1} & \overline{\beta_2} \end{bmatrix} = \begin{bmatrix} \alpha_1 \overline{\beta_1} & \alpha_1 \overline{\beta_2} \\ \alpha_2 \overline{\beta_1} & \alpha_2 \overline{\beta_2} \end{bmatrix}$
- $\begin{bmatrix} \alpha_{00} & \alpha_{01} \\ \alpha_{10} & \alpha_{01} \end{bmatrix} \otimes B = \begin{bmatrix} \alpha_{00} B & \alpha_{01} B \\ \alpha_{10} B & \alpha_{01} B \end{bmatrix}$
- $\left \vert 00 \right \rangle = \left \vert 0 \right \rangle \otimes \left \vert 0 \right \rangle = \begin{bmatrix} 1 \\ 0 \end{bmatrix} \otimes \begin{bmatrix} 1 \\ 0 \end{bmatrix} = \begin{bmatrix} 1 \\ 0 \\ 0 \\ 0 \end{bmatrix}$
- $\underbrace{\left \vert 101 \right \rangle}_\text{5 in decimal} = \left \vert 1 \right \rangle \otimes \left \vert 0 \right \rangle \otimes \left \vert 1 \right \rangle = \begin{bmatrix} 0 \\ 0 \\ 0 \\ 0 \\0 \\ 1 \\ 0 \\ 0 \end{bmatrix}$
- inner product $\rightsquigarrow$ matrix product
- outer product $\rightsquigarrow$ matrix product + tensor product
- $\otimes$ associative: $A \otimes (B + C) = A \otimes B + A \otimes C$
- $(A \otimes B) (C \otimes D) = (A C) \otimes (B D)$
- "floating scalar rule": $(\alpha A) \otimes B = A \otimes (\alpha B) = \alpha (A \otimes B)$
- $\left \vert \psi \right \rangle \cdot \left \langle \varphi \right \vert \cdot \left \vert \gamma \right \rangle = \left \vert \psi \right \rangle \cdot \mleft \langle \varphi \middle \vert \gamma \mright \rangle = \mleft \langle \varphi \middle \vert \gamma \mright \rangle \cdot \left \vert \psi \right \rangle$

# 10.4 2t

- todo: wire drawing
- $\left \vert 0 \right \rangle \otimes \left \vert 0 \right \rangle \otimes \left \vert 0 \right \rangle = \left \vert 000 \right \rangle$
- $\left ( I \otimes CNOT \right ) \left ( I \otimes X \otimes I \right ) \left ( H \otimes I \otimes I \right ) \underbrace{\left \vert 000 \right \rangle}_\text{vector}$
- it is more error-prone to do $I$ than $X$ or $H$
  - qiskit etc will put single operations that cancel out instead

- todo: drawing - cnot but ctrl qbit on top
- $(I \otimes S) (CNOT \otimes I) (I \otimes S) \left \vert 000 \right \rangle$
  - where $S$ is swap

- bob creates $\frac{1}{\sqrt 2} \left ( \left \vert 00 \right \rangle + \left \vert 11 \right \rangle \right )$ and sends one of the qubits to alice
- alice has 2 bits $a b$
  - if $a = 1$, alice applies $Z$ to $A$
    - $Z = \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}$
  - if $b = 1$, alice applies $X$ to $A$
  - send $A$ to bob
- bob
  - $CNOT(A, B)$
  - apply $H$ to $A$
  - measure $A, B$

| $ab$ | alice 1 | alice 2 | bob 1 | bob 2 | bob measure |
| :-:  | :-:     | :-:     | :-:   | :-:   | :-:         |
| $00$ | $\frac{1}{\sqrt 2} \left ( \left \vert 00 \right \rangle + \left \vert 11 \right \rangle \right )$ | $\frac{1}{\sqrt 2} \left ( \left \vert 00 \right \rangle + \left \vert 11 \right \rangle \right )$ | $\left \vert +0 \right \rangle$ | $\left \vert 00 \right \rangle$ | $00$ |
| $01$ | $\frac{1}{\sqrt 2} \left ( \left \vert 00 \right \rangle + \left \vert 11 \right \rangle \right )$ | $\frac{1}{\sqrt 2} \left ( \left \vert 10 \right \rangle + \left \vert 01 \right \rangle \right )$ | $\left \vert +1 \right \rangle$ | $\left \vert 01 \right \rangle$ | $01$ |
| $10$ | $\frac{1}{\sqrt 2} \left ( \left \vert 00 \right \rangle - \left \vert 11 \right \rangle \right )$ | $\frac{1}{\sqrt 2} \left ( \left \vert 00 \right \rangle - \left \vert 11 \right \rangle \right )$ | $\left \vert -0 \right \rangle$ | $\left \vert 10 \right \rangle$ | $10$ |
| $11$ | $\frac{1}{\sqrt 2} \left ( \left \vert 00 \right \rangle - \left \vert 11 \right \rangle \right )$ | $\frac{1}{\sqrt 2} \left ( \left \vert 10 \right \rangle - \left \vert 01 \right \rangle \right )$ | $-\left \vert -1 \right \rangle$ | -$\left \vert 11 \right \rangle$ | $11$ |

## quantum teleportation
- $\big \vert \underbrace{01}_\text{Alice} \underbrace{0}_\text{Bob} \big \rangle$, last 2 are a bell pair
- alice has $\alpha \left \vert 0 \right \rangle + \beta \left \vert 1 \right \rangle$
- start state: $\left ( \alpha \left \vert 0 \right \rangle + \beta \left \vert 1 \right \rangle \right )_A \otimes \frac{1}{\sqrt 2} \left ( \left \vert 00 \right \rangle + \left \vert 11 \right \rangle \right )_{BC}$
- alice
  - todo: drawing
  - $CNOT(A, B)$
  - $H(A)$
  - measure
  - $\frac{1}{\sqrt 2} \left ( \alpha \left \vert 000 \right \rangle + \alpha \left \vert 011 \right \rangle + \beta \left \vert 100 \right \rangle + \beta \left \vert 111 \right \rangle \right ) \rightarrow \frac{1}{\sqrt 2} \left ( \alpha \left \vert 000 \right \rangle + \alpha \left \vert 011 \right \rangle + \beta \left \vert 110 \right \rangle + \beta \left \vert 101 \right \rangle \right )$
  - $\rightarrow \frac{1}{2} \left ( \alpha \left \vert 001 \right \rangle + \alpha \left \vert 101 \right \rangle + \alpha \left \vert 011 \right \rangle + \alpha \left \vert 111 \right \rangle + \beta \left \vert 010 \right \rangle - \beta \left \vert 110 \right \rangle + \beta \left \vert 000 \right \rangle - \beta \left \vert 100 \right \rangle \right )$
  - $\rightarrow \frac{1}{2} \left ( \left \vert 00 \right \rangle \otimes \left ( \alpha \left \vert 0 \right \rangle + \beta \left \vert 1 \right \rangle \right ) + \left \vert 01 \right \rangle \otimes \left ( \beta \left \vert 0 \right \rangle + \alpha \left \vert 1 \right \rangle \right ) + \left \vert 10 \right \rangle \otimes \left ( \alpha \left \vert 0 \right \rangle - \beta \left \vert 1 \right \rangle \right ) + \left \vert 11 \right \rangle \otimes \left ( -\beta \left \vert 0 \right \rangle + \alpha \left \vert 1 \right \rangle \right ) \right )$
  - $\frac{1}{4}$ probability of sending any of the 4
  - $00 \rightarrow \alpha \left \vert 0 \right \rangle + \beta \left \vert 1 \right \rangle$
  - $01 \rightarrow \beta \left \vert 0 \right \rangle + \alpha \left \vert 1 \right \rangle$
  - $10 \rightarrow \alpha \left \vert 0 \right \rangle - \beta \left \vert 1 \right \rangle$
  - $11 \rightarrow -\beta \left \vert 0 \right \rangle + \alpha \left \vert 1 \right \rangle$
- bob
  - $b = 1 \Rightarrow X(C)$
    - $00 \rightarrow \alpha \left \vert 0 \right \rangle + \beta \left \vert 1 \right \rangle$
    - $01 \rightarrow \alpha \left \vert 0 \right \rangle + \beta \left \vert 1 \right \rangle$
    - $10 \rightarrow \alpha \left \vert 0 \right \rangle - \beta \left \vert 1 \right \rangle$
    - $11 \rightarrow \alpha \left \vert 0 \right \rangle - \beta \left \vert 1 \right \rangle$
  - $a = 1 \Rightarrow Z(C)$
    - $00 \rightarrow \alpha \left \vert 0 \right \rangle + \beta \left \vert 1 \right \rangle$
    - $01 \rightarrow \alpha \left \vert 0 \right \rangle + \beta \left \vert 1 \right \rangle$
    - $10 \rightarrow \alpha \left \vert 0 \right \rangle + \beta \left \vert 1 \right \rangle$
    - $11 \rightarrow \alpha \left \vert 0 \right \rangle + \beta \left \vert 1 \right \rangle$
- alice's qubit destroyed when measured

## no cloning theorem
- no quantum operation maps $\left \vert \psi 0 \right \rangle$ to $\left \vert \psi \psi \right \rangle$
- suppose $U \left \vert \psi \right \rangle \left \vert 0 \right \rangle = \left \vert \psi \right \rangle \left \vert \psi \right \rangle$
- pick $\left \vert \psi_1 \right \rangle, \left \vert \psi_2 \right \rangle$ such that $\mleft \langle \psi_1 \middle \vert \psi_2 \mright \rangle \neq 0$ and $\mleft \langle \psi_1 \middle \vert \psi_2 \mright \rangle \neq 1$
- lemma: $\mleft \langle (v_1 \otimes v_2) \middle \vert (w_1 \otimes w_2) \mright \rangle = \mleft \langle v_1 \middle \vert w_1 \mright \rangle \cdot \mleft \langle v_2 \middle \vert w_2 \mright \rangle$
- $\mleft \langle \psi_1 \middle \vert \psi_2 \mright \rangle = \mleft \langle \psi_1 \middle \vert \psi_2 \mright \rangle \cdot \mleft \langle 0 \middle \vert 0 \mright \rangle = \mleft \langle \psi_1 0 \middle \vert \psi_2 0 \mright \rangle = \left \langle U\left ( \left \vert \psi_1 0 \right \rangle \right ), U\left ( \left \vert \psi_2 0 \right \rangle \right ) \right \rangle = \mleft \langle \psi_1 \psi_1 \middle \vert \psi_2 \psi_2 \mright \rangle = \mleft \langle \psi_1 \middle \vert \psi_2 \mright \rangle \cdot \mleft \langle \psi_1 \middle \vert \psi_2 \mright \rangle$

## universality
- $NAND(x_1, x_2) = CCNOT(x_1, x_2, 1)$
  - $CCNOT$ can simulate all of boolean logic
- $\left \{ CCNOT, H \right \}$ is universal for all real unitaries
- $\left \{ CCNOT, H, S = \begin{bmatrix} 1 & 0 \\ 0 & i \end{bmatrix} \right \}$ is universal for all unitaries
- quantum computers implement $\left \{ CNOT, H, T \right \}$
  - $S = T^2$

# 10.6 2th

## deutsch-jozsa problem
- input: a function $f \colon \left \{ 0, 1 \right \}^n \to \left \{ 0, 1 \right \}$
- assumption: either $f$ is constant or $f$ is balanced
- probabilistically, just guess balanced
- $2^n$ inputs, try one after another, know it's constant after $2^{n - 1} + 1$ tries
- $n = 1$
  - $f \colon \left \{ 0, 1 \right \} \to \left \{ 0, 1 \right \}$
  - $U_f \colon \text{qubit}^{\otimes 2} \to \text{qubit}^{\otimes 2}$
  - make unitary
  - $U_f(\left \vert x \right \rangle \otimes \left \vert b \right \rangle) = \left \vert x \right \rangle \otimes \left \vert b \oplus f(x) \right \rangle$

  | input | $f_0$ | $f_1$ | $f_2$ | $f_3$ |
  | --:   | :-:   | :-:   | :-:   | :-:   |
  | $0$   | $0$   | $0$   | $1$   | $1$   |
  | $1$   | $0$   | $1$   | $0$   | $1$   |

  - $U_{f_0}\left ( \left \vert 0 \right \rangle \otimes \left \vert b \right \rangle \right ) = \left \vert 0 \right \rangle \otimes \left \vert b \oplus f(0) \right \rangle = \left \vert 0b \right \rangle$
  - $U_{f_0}\left ( \left \vert 1 \right \rangle \otimes \left \vert b \right \rangle \right ) = \left \vert 1 \right \rangle \otimes \left \vert b \oplus f(1) \right \rangle = \left \vert 1b \right \rangle$
  - $U_{f_0}$ is the $4 \times 4$ identity matrix
  - $f$ is constant
    - $f(0) = 0 \wedge f(1) = 0 \vee f(0) = 1 \wedge f(1) = 1$
    - $f(0) \oplus f(1) = 0$
  - $f$ is balanced
    - $f(0) \oplus f(1) = 1$
  - idea 1: use superposition of $\left \vert 0 \right \rangle, \left \vert 1 \right \rangle$
  - observation: $U_f$ moves $f(0), f(1)$ to the exponent so we can do addition
  - idea 2: $H$ will move $f(0) \oplus f(1)$ "back down"
  - deutsch algorithm
  - todo: drawing
  - $\operatorname{measure}_0\left ( (H \otimes I) U_f (H \otimes H) \left \vert 01 \right \rangle \right ) = \begin{cases}
    0 & \text{$f$ constant} \\ 
    1 & \text{$f$ balanced}
  \end{cases}$
  - lemma 1: $\forall \, a \in \left \{ 0, 1 \right \}: \left \vert 0 \oplus a \right \rangle - \left \vert 1 \oplus a \right \rangle = (-1)^a (\left \vert 0 \right \rangle - \left \vert 1 \right \rangle)$
  - lemma 2: $\forall \, x \in \left \{ 0, 1 \right \}^n: U_f\left ( \left \vert x- \right \rangle \right ) = (-1)^{f(x)} \left \vert x- \right \rangle$
    - $U_f\left ( \left \vert x- \right \rangle \right ) = \frac{1}{\sqrt 2} \left ( U_f\left ( \left \vert x0 \right \rangle \right ) - U_f\left ( \left \vert x1 \right \rangle \right ) \right ) = \frac{1}{\sqrt 2} \left ( \left \vert x \right \rangle \otimes \left \vert 0 \oplus f(x) \right \rangle - \left \vert x \right \rangle \otimes \left \vert 1 \oplus f(x) \right \rangle \right )$
    - $= \left \vert x \right \rangle \otimes \frac{1}{\sqrt 2} \left ( \left \vert 0 \oplus f(x) - \left \vert 1 \oplus f(x) \right \rangle \right \rangle \right ) = \left \vert x \right \rangle \otimes \frac{1}{\sqrt 2} (-1)^{f(x)} \left ( \left \vert 0 \right \rangle - \left \vert 1 \right \rangle \right ) = (-1)^{f(x)} \left \vert x- \right \rangle$
  - lemma 3: $\forall \, a \in \left \{ 0, 1 \right \}: H\left ( \frac{1}{\sqrt 2} \left \vert 0 \right \rangle + \frac{1}{\sqrt 2} (-1)^a \left \vert 1 \right \rangle \right ) = \left \vert a \right \rangle$
  - $(H \otimes I) U_f (H \otimes H) \left \vert 01 \right \rangle = (H \otimes I) U_f\left ( \left \vert +- \right \rangle \right ) = (H \otimes I) U_f \frac{1}{\sqrt 2} \left ( \left ( \left \vert 0 \right \rangle + \left \vert 1 \right \rangle \right ) \otimes \left \vert - \right \rangle \right )$
  - $= (H \otimes I) \frac{1}{\sqrt 2} U_f\left ( \sum_{x \in \left \{ 0, 1 \right \}} \left \vert x- \right \rangle \right ) = (H \otimes I) \frac{1}{\sqrt 2} \sum_{x \in \left \{ 0, 1 \right \}} (-1)^{f(x)} \left \vert x- \right \rangle$
  - $= (H \otimes I) \frac{1}{\sqrt 2} \left ( (-1)^f(0) \left \vert 0 \right \rangle + (-1)^{f(1)} \left \vert 1 \right \rangle \right ) \otimes \left \vert - \right \rangle = (H \otimes I) \frac{1}{\sqrt 2} (-1)^{f(0)} \left ( \left \vert 0 \right \rangle + (-1)^{f(0) \oplus f(1)} \left \vert 1 \right \rangle \right ) \otimes \left \vert - \right \rangle$
  - $= (-1)^{f(0)} \left \vert f(0) \oplus f(1) \right \rangle \otimes \left \vert - \right \rangle$
  - norm: $\left | (-1)^{f(0)} \right |^2 = 1$

## deutsch-jozsa algorithm
- $n > 1$
- todo: drawing
- $\operatorname{measure}_{0 : n}\left ( (H^{\otimes n} \otimes I) U_f H^{\otimes (n + 1)} \left ( \left \vert 0 \right \rangle^{\otimes n} \otimes \left \vert 1 \right \rangle \right ) \right )$ gives an $n$-bit bitstring
- lemma 4 (todo: 5???): $\forall \, x \in \left \{ 0, 1 \right \}: H\left ( \left \vert x \right \rangle \right ) = \frac{1}{\sqrt 2} \sum_{y \in \left \{ 0, 1 \right \}} (-1)^{x y} \left \vert y \right \rangle$
  - $\text{RHS} = \frac{1}{\sqrt 2} \left ( \left \vert 0 \right \rangle + (-1)^x \left \vert 1 \right \rangle \right )$, then see lemma 3
- lemma 5: $H^{\otimes n}\left ( \left \vert x \right \rangle \right ) = \frac{1}{\sqrt{2^n}} \sum_{y \in \left \{ 0, 1 \right \}^n} (-1)^{x \cdot y} \left \vert y \right \rangle$
  - $H^{\otimes n}\left ( \left \vert 0 \right \rangle \right ) = H\left ( \left \vert x_1 \right \rangle \right ) \otimes \cdots \otimes H\left ( \left \vert x_n \right \rangle \right ) = \frac{1}{\sqrt 2} \sum_{y_1 \in \left \{ 0, 1 \right \}} \left \vert y_1 \right \rangle \otimes \cdots \otimes \frac{1}{\sqrt 2} \sum_{y_n \in \left \{ 0, 1 \right \}} \left \vert y_n \right \rangle$
  - $= \frac{1}{\sqrt{2^n}} \sum_{y_1 \in \left \{ 0, 1 \right \}} \cdots \sum_{y_n \in \left \{ 0, 1 \right \}} (-1)^{x_1 y_1} \cdots (-1)^{x_n y_n} \left \vert y_1 \dots y_n \right \rangle = \frac{1}{\sqrt{2^n}} \sum_{y \in \left \{ 0, 1 \right \}^n} (-1)^{x \cdot y} \left \vert y \right \rangle$
- $(H^{\otimes n} \otimes I) U_f H^{\otimes (n + 1)} \left ( \left \vert 0 \right \rangle^{\otimes n} \otimes \left \vert 1 \right \rangle \right ) = (H^{\otimes n} \otimes I) U_f \left ( \frac{1}{\sqrt{2^n}} \sum_{x \in \left \{ 0, 1 \right \}^n} \left \vert x \right \rangle \right ) \otimes \left \vert - \right \rangle$
- $= \left ( H^{\otimes n} \otimes I \right ) \frac{1}{\sqrt{2^n}} \left ( \sum_{x \in \left \{ 0, 1 \right \}^n} (-1)^{f(x)} \left \vert x \right \rangle \right ) \otimes \left \vert - \right \rangle$
- $= \frac{1}{\sqrt{2^n}} \left ( \sum_{x \in \left \{ 0, 1 \right \}^n} \frac{1}{\sqrt{2^n}} \sum_{y \in \left \{ 0, 1 \right \}^n} (-1)^{x \cdot y} \left \vert y \right \rangle \right ) \otimes \left \vert - \right \rangle$
- $= \frac{1}{2^n} \left ( \sum_x \sum_y (-1)^{f(x) \oplus x \cdot y} \left \vert y \right \rangle \right ) \otimes \left \vert - \right \rangle$
- for $\left \vert y \right \rangle = \left \vert 0 \right \rangle^{\otimes n} \left \vert - \right \rangle$, only final state $= \frac{1}{2^n} \left ( \sum_x (-1)^{f(x)} \left \vert 0 \right \rangle^{\otimes n} \right ) \otimes \left \vert - \right \rangle$

# 10.11 3t

## bernstein-vazirani problem
- input: a function $f \colon \left \{ 0, 1 \right \}^n \to \left \{ 0, 1 \right \}$
- assumption: $f(x) = (a \cdot x) \oplus b$
- outpu: $a, b$
- $f(0 \dots 0) = b$
- $f(0 \dots 0 1) = a_n \oplus b$
- $a = 0 \dots 0 \Rightarrow f(x) = b$: $f$ is constant
- $a \neq 0 \dots 0$: $f$ is balanced
  - every input has a sister input (e.g. flipping the last bit) that flips the output
- ideas
  - superposition
  - $U_f$ will move something to the exponent (of $-1$)
  - $H^{\otimes n}$ will move the exponent back down
- goal: final state $\left \vert a \right \rangle$
- circuit
  - todo: drawing
  - $\operatorname{measure}_{1 : n}((H^{\otimes n} \otimes I) U_f H^{\otimes (n + 1)}(\left \vert 0 \dots 01 \right \rangle))$
- $\frac{1}{2^n} \sum_{x \in \left \{ 0, 1 \right \}^n} \sum_{y \in \left \{ 0, 1 \right \}^n} (-1)^{(x \cdot y) \oplus f(x)} \left \vert y \right \rangle = \frac{1}{2^n} \sum_{x \in \left \{ 0, 1 \right \}^n} \sum_{y \in \left \{ 0, 1 \right \}^n} (-1)^{(x \cdot y) \oplus (a \cdot x) \oplus b} \left \vert y \right \rangle$
  - $= \frac{1}{2^n} \sum_{x \in \left \{ 0, 1 \right \}^n} \sum_{y \in \left \{ 0, 1 \right \}^n} (-1)^{(x \cdot (y \oplus a)) \oplus b} \left \vert y \right \rangle = \frac{(-1)^b}{2^n} \sum_{x \in \left \{ 0, 1 \right \}^n} \sum_{y \in \left \{ 0, 1 \right \}^n} (-1)^{x \cdot (y \oplus a)} \left \vert y \right \rangle$
  - amplitude of $\left \vert a \right \rangle = \frac{1}{2^n} \sum_{x \in \left \{ 0, 1 \right \}^n} (-1)^{x \cdot (a \oplus a)} = (-1)^b$
  - then original expression $= (-1)^b \left \vert a \right \rangle$

## another problem
- input: $f \colon \left \{ 0, 1 \right \}^2 \to \left \{ 0, 1 \right \}$
- assumption: $f$ is $1$ on a single input
- output: the single input
- circuit
  - goal: $\left \vert cd \right \rangle$
  - todo: drawing
  - $\operatorname{measure}_{1 : n}((V \otimes I) U_f H^{\otimes 3} \left \vert 0 \dots 01 \right \rangle)$
  - need to find $V$
  - let 
    - $\varphi_{00} = \frac{1}{2} \left ( -\left \vert 00 \right \rangle + \left \vert 01 \right \rangle + \left \vert 10 \right \rangle + \left \vert 11 \right \rangle \right )$
    - $\varphi_{01} = \frac{1}{2} \left ( \left \vert 00 \right \rangle - \left \vert 01 \right \rangle + \left \vert 10 \right \rangle + \left \vert 11 \right \rangle \right )$
    - $\varphi_{10} = \frac{1}{2} \left ( \left \vert 00 \right \rangle + \left \vert 01 \right \rangle - \left \vert 10 \right \rangle + \left \vert 11 \right \rangle \right )$
    - $\varphi_{11} = \frac{1}{2} \left ( \left \vert 00 \right \rangle + \left \vert 01 \right \rangle + \left \vert 10 \right \rangle - \left \vert 11 \right \rangle \right )$
  - $(V \otimes I) U_f H^{\otimes 3} \left \vert 001 \right \rangle = (V \otimes I) U_f \frac{1}{2} \left ( \left \vert 00- \right \rangle + \left \vert 01- \right \rangle + \left \vert 10- \right \rangle + \left \vert 11- \right \rangle \right )$
    - $= (V \otimes I) \frac{1}{2} \left ( (-1)^{f(00)} \left \vert 00- \right \rangle + (-1)^{f(01)} \left \vert 01- \right \rangle + (-1)^{f(10)} \left \vert 10- \right \rangle + (-1)^{f(11)} \left \vert 11- \right \rangle \right )$
    - $= (V \otimes I) (\varphi_{cd} \otimes \left \vert - \right \rangle)$
  - want $V(\varphi_{cd}) = \left \vert cd \right \rangle$
  - $V = \frac{1}{2} \begin{bmatrix} -1 & 1 & 1 & 1 \\ 1 & -1 & 1 & 1 \\ 1 & 1 & -1 & 1 \\ 1 & 1 & 1 & -1 \end{bmatrix}$
    - $\left (= \begin{bmatrix} \varphi_{00} & \varphi_{01} & \varphi_{10} & \varphi_{11} \end{bmatrix}^{-1}\right )$

# 10.13 3th

## simon's problem
- input: $f \colon \left \{ 0, 1 \right \}^n \to \left \{ 0, 1 \right \}^n$
- assumption: $\exists \, s \in \left \{ 0, 1 \right \}\; \forall \, x, y: f(x) = f(y) \Leftrightarrow (x + y) \in \left \{ 0^n, s \right \}$
- output: $s$
\newpage
- $n = 3, s = 110$

| $x$ | $f(x)$ |
| :-: | :-:    |
| 000 | 101    |
| 001 | 010    |
| 010 | 000    |
| 011 | 110    |
| 100 | 000    |
| 101 | 110    |
| 110 | 101    |
| 111 | 010    |

## simon's alg
- repeat $f \rightarrow \text{quantum generate} \rightarrow \text{equations} \rightarrow \text{classical solve} \rightarrow s$ until the chance of success is high
- $y_1 \cdot s = 0, \dots, y_{n - 1} \cdot s = 0$
- ideally the $y_i$'s are linearly independent
- $P(\text{$y_i$'s are linearly independent}) > \frac{1}{4}$

## events
- $E_1$: $y_1$ is not $0$
- for $k = 2, \dots, n - 1$: 
  - $E_k$: $y_k$ is not in the span of $y_1, \dots, y_{k - 1}$
- $E$: $y_1, \dots, y_{n - 1}$ are linearly independent
- sample from a space of size $2^{n - 1}$
- $P(E_1) = P(E_1 \wedge \cdots \wedge E_n) = P(E_1) \cdot P(E_2 \wedge \cdots \wedge E_{n - 1} \mid E_1) = P(1) \cdot \prod_{k = 2}^n P(E_k \mid E_1 \wedge \cdots \wedge E_{k - 1})$
  - $P(E_1) = 1 - 1 / 2^{n - 1}$
  - $\prod_k = 1 - 2^{k - 1} / 2^{n - 1}$
  - $= (1 - 1 / 2^{n - 1}) \cdots (1 - 1 / 2) > 1 / 4$
  - for all $k = 1, \dots, n - 1$: $(1 - 1 / 2^{n - 1}) \cdots (1 - 1 / 2^{n - (k - 1)}) > (1 - 1 / 2^{n - k})$
  - for $k + 1$
    - lhs: $(1 - 1 / 2^{n - 1}) \cdots (1 - 1 / 2^{n - k}) > (1 - 1 / 2^{n - k})^2 = \left ( \frac{2^{n - k} - 1}{2^{n - k}} \right )^2 = \frac{2^{2 n - 2 k} - 2^{n - (k - 1)} + 1}{2^{2 n - 2 k}}$
    - rhs: $1 - 1 / 2^{n - (k + 1)} = \frac{2^{n - (k + 1)} - 1}{2^{n - (k + 1)}} = \frac{2^{2 n + 2 k} - 2^{n - (k - 1)}}{2^{2 n + 2 k}}$
- run the whole thing $4 m$ times
- $P(\text{failure}) < \left ( 1 - \frac{1}{4} \right )^{4 m} < e^{-m}$

## circuit
- todo: drawing
- $U_f \left \vert x \right \rangle \otimes \left \vert b \right \rangle = \left \vert x \right \rangle \otimes \left \vert b \oplus f(x) \right \rangle$
- $\operatorname{measure}_{1 : n} (H^{\otimes n} \otimes I^{\otimes n}) U_f (H^{\otimes n} \otimes I^{\otimes n}) \left \vert 0^n \right \rangle \otimes \left \vert 0^n \right \rangle$
- $= (H^{\otimes n} \otimes I^{\otimes n}) U_f \left ( \frac{1}{\sqrt{2^n}} \sum_{x \in \left \{ 0, 1 \right \}^n} \left \vert x \right \rangle \right ) \otimes \left \vert 0^n \right \rangle$
- $= (H^{\otimes n} \otimes I^{\otimes n}) \frac{1}{\sqrt{2^n}} \left ( \sum_{x \in \left \{ 0, 1 \right \}^n} \left \vert x \right \rangle \right ) \otimes \left \vert f(x) \right \rangle$
- $= \frac{1}{2^n} \sum_{x \in \left \{ 0, 1 \right \}^n} \sum_{y \in \left \{ 0, 1 \right \}^n} (-1)^{x \cdot y} \left \vert y \right \rangle \otimes \left \vert f(x) \right \rangle$
- $= \sum_{y \in \left \{ 0, 1 \right \}^n} \left \vert y \right \rangle \left ( \frac{1}{2^n} \sum_{x \in \left \{ 0, 1 \right \}^n} (-1)^{x \cdot y} \left \vert f(x) \right \rangle \right )$
- $s = 0$
  - $\left | \frac{1}{2^n} \sum_{x \in \left \{ 0, 1 \right \}^n} (-1)^{x \cdot y} \left \vert f(x) \right \rangle \right |^2$
  - $f$ is injective so $\left \vert f(x) \right \rangle$ is an orthonormal basis $\rightarrow$ use pythagorean theorem 
  - $= \frac{1}{2^{2 n}} \sum_{x \in \left \{ 0, 1 \right \}^n} \left | (-1)^{x \cdot y} \left \vert f(x) \right \rangle \right |^2$
  - $= \frac{1}{2^n}$ uniform distribution
- $s \neq 0$
  - $y$ is drawn from a set $A$ of size $2^{n - 1}$
  - for $z \in A$, we have $x_z, x_z' \in \left \{ 0, 1 \right \}^n$ where $f(x_z) = f(x_z') = z$ and $x_z \oplus x_z' = s$
  - $\left | \frac{1}{2^n} \sum_{x \in \left \{ 0, 1 \right \}^n} (-1)^{x \cdot y} \left \vert f(x) \right \rangle \right |^2 = \left | \frac{1}{2^n} \sum_{z \in A} \left ( (-1)^{x_z \cdot y} + (-1)^{x_z' \cdot y} \right ) \left \vert z \right \rangle \right |^2$
  - $= \left | \frac{1}{2^n} \sum_{z \in A} (-1)^{x_z \cdot y} \left ( 1 + (-1)^{s \cdot y} \right ) \left \vert z \right \rangle \right |^2$
  - todo: $\left \vert z \right \rangle$s are orthogonal???
  - $= \begin{cases} 2^{1 - n} & s \cdot y = 0 \\ 0 & s \cdot y = 1 \end{cases}$ uniform distribution

# 10.18 4t

## grover's problem
- input: $f \colon \left \{ 0, 1 \right \}^n \to \left \{ 0, 1 \right \}$
- output: $\begin{cases}
  1 & \exists \, x \in \left \{ 0, 1 \right \}^n: f(x) = 1 \\ 
  0 & \text{otherwise}
\end{cases}$
- $Z_f\left \vert x \right \rangle = (-1)^{f(x)} \left \vert x \right \rangle$
- $Z_0 \left \vert x \right \rangle = \begin{cases}
  -\left \vert x \right \rangle & x = 0^n \\ 
  \left \vert x \right \rangle & x \neq 0^n
\end{cases}$
  - todo: drawing
  - NAND into 1 qubit, use Z gate, uncompute NAND
- $G = - H^{\otimes n} Z_0 H^{\otimes n} Z_f$

## grover's algorithm
- $x$: $n$ qubits, initially $\left \vert 0^n \right \rangle$
1. apply $H^{\otimes n}$ to $x$
2. repeat (apply $G$ to $x$) $\mathcal O(\sqrt{2^n})$ times
3. measure $x$ and output the result

## example $n = 2$
- $f \colon \left \{ 0, 1 \right \}^2 \to \left \{ 0, 1 \right \}$
- $f(00) = f(01) = f(10) = 0$
- $f(11) = 1$
- $\begin{aligned}[t]
    H^{\otimes 2}\left ( \left \vert 00 \right \rangle + \left \vert 01 \right \rangle + \left \vert 10 \right \rangle - \left \vert 11 \right \rangle \right ) = \frac{1}{2} \big ( &\left ( \left \vert 00 \right \rangle + \left \vert 01 \right \rangle + \left \vert 10 \right \rangle + \left \vert 11 \right \rangle \right ) \\ 
    &+ \left ( \left \vert 00 \right \rangle - \left \vert 01 \right \rangle + \left \vert 10 \right \rangle - \left \vert 11 \right \rangle \right ) \\ 
    &+ \left ( \left \vert 00 \right \rangle + \left \vert 01 \right \rangle - \left \vert 10 \right \rangle - \left \vert 11 \right \rangle \right ) \\ 
    &- \left ( \left \vert 00 \right \rangle - \left \vert 01 \right \rangle - \left \vert 10 \right \rangle + \left \vert 11 \right \rangle \right ) \big ) = \left \vert 00 \right \rangle + \left \vert 01 \right \rangle + \left \vert 10 \right \rangle - \left \vert 11 \right \rangle
  \end{aligned}$
- $\begin{aligned}[t]
    G H^{\otimes 2} \left \vert 00 \right \rangle &= G \frac{1}{2} \left ( \left \vert 00 \right \rangle + \left \vert 01 \right \rangle + \left \vert 10 \right \rangle + \left \vert 11 \right \rangle \right ) \\
    &= -H^{\otimes 2} Z_0 H^{\otimes 2} Z_f \frac{1}{2} \left ( \left \vert 00 \right \rangle + \left \vert 01 \right \rangle + \left \vert 10 \right \rangle + \left \vert 11 \right \rangle \right ) \\ 
    &= -H^{\otimes 2} Z_0 H^{\otimes 2} \frac{1}{2} \left ( \left \vert 00 \right \rangle + \left \vert 01 \right \rangle + \left \vert 10 \right \rangle - \left \vert 11 \right \rangle \right ) \\ 
    &= -H^{\otimes 2} Z_0 \frac{1}{2} \left ( \left \vert 00 \right \rangle + \left \vert 01 \right \rangle + \left \vert 10 \right \rangle - \left \vert 11 \right \rangle \right ) \\ 
    &= -H^{\otimes 2} \frac{1}{2} \left ( -\left \vert 00 \right \rangle + \left \vert 01 \right \rangle + \left \vert 10 \right \rangle - \left \vert 11 \right \rangle \right ) \\ 
    &= -H^{\otimes 2} \frac{1}{2} \left ( -2 \left \vert 00 \right \rangle + \left ( \left \vert 00 \right \rangle + \left \vert 01 \right \rangle + \left \vert 10 \right \rangle - \left \vert 11 \right \rangle \right ) \right ) \\ 
    &= -\frac{1}{2} \left ( -2 \cdot \frac{1}{2} \left ( \left \vert 00 \right \rangle + \left \vert 01 \right \rangle + \left \vert 10 \right \rangle + \left \vert 11 \right \rangle \right ) + \left ( \left \vert 00 \right \rangle + \left \vert 01 \right \rangle + \left \vert 10 \right \rangle - \left \vert 11 \right \rangle \right ) \right ) \\ 
    &= \left \vert 11 \right \rangle
  \end{aligned}$

## example
- notation
  - $A = \left \{ x \in \left \{ 0, 1 \right \}^n : f(x) = 1 \right \}$
  - $B = \left \{ x \in \left \{ 0, 1 \right \}^n : f(x) = 0 \right \}$
  - $N = 2^n, a = \left | A \right |, b = \left | B \right |$
  - $\left \vert A \right \rangle = \frac{1}{\sqrt a} \sum_{x \in A} \left \vert x \right \rangle$
  - $\left \vert B \right \rangle = \frac{1}{\sqrt b} \sum_{x \in B} \left \vert x \right \rangle$
- $\left \vert A \right \rangle$ and $\left \vert B \right \rangle$ are orthogonal
- lemma
  - $G \left \vert A \right \rangle = \left ( 1 - \frac{2 a}{N} \right ) \left \vert A \right \rangle - \frac{2 \sqrt{a b}}{N} \left \vert B \right \rangle$
  - $G \left \vert B \right \rangle = \frac{2 \sqrt{a b}}{N} \left \vert A \right \rangle - \left ( 1 - \frac{2 b}{N} \right ) \left \vert B \right \rangle$
  - that is, $\operatorname{span}\left \{ \left \vert A \right \rangle, \left \vert B \right \rangle \right \}$ is closed under $G$
  - $\left \vert h \right \rangle = H^{\otimes n} \left \vert 0^n \right \rangle = \frac{1}{\sqrt N} \sum_{x \in \left \{ 0, 1 \right \}^n} \left \vert x \right \rangle = \frac{\sqrt a}{\sqrt N} \left \vert A \right \rangle + \frac{\sqrt b}{\sqrt N} \left \vert B \right \rangle$
  - $Z_0 = \begin{bmatrix} -1 & 0 & \cdots & 0 \\ 0 & 1 & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & 1 \end{bmatrix} = I - 2 \left \vert 0^n \right \rangle \left \langle 0^n \right \vert$
  - $\begin{aligned}[t]
      H^{\otimes n} Z_0 H^{\otimes n} &= H^{\otimes n} \left ( I - 2 \left \vert 0^n \right \rangle \left \langle 0^n \right \vert \right ) H^{\otimes n} \\ 
      &= H^{\otimes n} I H^{\otimes n} - 2 H^{\otimes n} \left \vert 0^n \right \rangle \left \langle 0^n \right \vert H^{\otimes n} \\ 
      &= I - 2 \left \vert h \right \rangle \left \langle h \right \vert
    \end{aligned}$
  - $\begin{aligned}[t]
      G \left \vert A \right \rangle &= -H^{\otimes n} Z_0 H^{\otimes n} Z_f \left \vert A \right \rangle \\ 
      &= \left ( I - 2 \left \vert h \right \rangle \left \langle h \right \vert \right ) (-Z_f) \left \vert A \right \rangle \\ 
      &= \left ( I - \left \vert h \right \rangle \left \langle h \right \vert \right ) \left \vert A \right \rangle \\ 
      &= \left \vert A \right \rangle - 2 \left \vert h \right \rangle \left \langle h \right \vert \left \vert A \right \rangle \\ 
      &= \left \vert A \right \rangle - 2 \mleft \langle h \middle \vert A \mright \rangle \left \vert h \right \rangle \in \operatorname{span}\left \{ \left \vert A \right \rangle, \left \vert B \right \rangle \right \} \\ 
      &= \left \vert A \right \rangle - 2 \cdot \frac{\sqrt a}{\sqrt N} \cdot \left ( \frac{\sqrt a}{\sqrt N} \left \vert A \right \rangle + \frac{\sqrt b}{\sqrt N} \left \vert b \right \rangle \right ) \\ 
      &= \left ( 1 - \frac{2 a}{N} \right ) \left \vert A \right \rangle - \frac{2 \sqrt{a b}}{\sqrt B} \left \vert B \right \rangle
    \end{aligned}$
  - $M = G_{\left \{ \left \vert B \right \rangle, \left \vert A \right \rangle \right \}} = \begin{bmatrix} -\left ( 1 - \frac{2 b}{N} \right ) & -\frac{2 \sqrt{a b}}{N} \\ \frac{2 \sqrt{a b}}{N} & 1 - \frac{2 a}{N} \end{bmatrix}$
  - $\left ( \frac{\sqrt a}{\sqrt N} \right )^2 + \left ( \frac{\sqrt{b}}{\sqrt N} \right )^2 = 1$
  - let $\theta$ be such that $\sin \theta = \frac{\sqrt a}{\sqrt N}$ and $\cos \theta = \frac{\sqrt b}{\sqrt N}$
  - $R_\theta = \begin{bmatrix} \cos \theta & -\sin \theta \\ \sin \theta & \cos \theta \end{bmatrix} \Rightarrow R_\theta^2 = M$
  - after $k$ iterations: $\sin((2 k + 1) \theta) \left \vert A \right \rangle + \cos((2 k + 1) \theta) \left \vert B \right \rangle$
  - want $\sin((2 k + 1) \theta) \approx 1$
    - $(2 k + 1) \theta \approx \frac{\pi}{2}$
    - $2 k + 1 \approx \frac{\pi}{2 \theta}$
    - $k \approx \frac{\pi}{4 \theta} - \frac{1}{2}$
    - for $a = 1$, $\theta \approx \sin \theta = \frac{1}{\sqrt N}$
    - $k \approx \frac{\pi \sqrt N}{4} - \frac{1}{2} \approx \sqrt N$
  - previous example: $\sin \theta = \frac{\sqrt 1}{\sqrt 4} = \frac{1}{2} \Rightarrow \theta = \frac{\pi}{6} \Rightarrow (2 + 1) \theta = \frac{\pi}{2}$

# 10.25 5t

## algorithm for integer factorization
- input: `int` $N \geq 2$
- output: $N = p_1^{k_1} \cdots p_m^{k_m}$
- method: 
  - if $N = p^k$ return $p^k$
  - else if $N$ is even return combine(2, factor($N / 2$))
  - else
    - `int` d = shor($N$)
    - return combine(factor($d$), factor($N / d$))

## shor's algorithm
- input: odd composite `int` $N$ not the power of a prime
- output: a nontrivial factor $d$
- method: repeat
  - `int a = random(2, 3, ..., N - 1)`
  - `int d = gcd(a, N)`
  - `if (d > 1) return d`
  - `else`
    - `int r = find_order_candidate(a, N)`
      - $a^r \equiv 1\ (\mathrm{mod}\ N)$
    - `if r is even`
      - `int x = a ** (r / 2) - 1 mod N`
      - `int d = gcd(x, N)`
      - `if (d > 1) return d`
  - until give up
- $\mathbb Z / N = \left \{ 0, \dots, N - 1 \right \}$
- $(\mathbb Z / N)^* = \left \{ a \in \mathbb Z / N : \operatorname{gcd}(a, N) = 1 \right \}$ is a group with multiplication
- need `find_order_candidate` to be polynomial with respect to $\log N$
- $N \mid (a^r - 1) = (a^{r / 2} + 1) (a^{r / 2} - 1)$
- never $N \mid (a^{r / 2} - 1)$ since $r$ is the order, the smallest such that $N \mid (a^r - 1)$

## example
- $N = 21, a = 2$
- $d = \operatorname{gcd}(a, N) = \operatorname{gcd}(2, 21)$
- $r = \verb~find_order_cand~(2, 21) = 6$
- $x = (a^{r / 2} - 1) \% N = 7$
- $d = \operatorname{gcd}(x, N) = 7 > 1$

## find order algorithm
- input: `int` $N$, `int` $a \in (\mathbb Z / N)^*$
- output: the smallest `int` $r > 0$ such that $a^r \equiv 1\ (\mathrm{mod}\ N)$ or some other integer
- method: 
  - `float` $f = \verb~phase_estimation~(M_1, \left \vert 1 \right \rangle)$
  - `fraction` $q = \verb~fraction_with_bounded_denominator~(f, N)$
  - `return` $\verb~denominator~(q)$
- $M_a \left \vert x \right \rangle = \left \vert a \cdot x\ (\mathrm{mod}\ N) \right \rangle$
- $\omega = e^{2 \pi i / r}$
- for $0 \leq k < r$
  - $\left \vert \psi_k \right \rangle = \frac{1}{\sqrt r} (\left \vert 1 \right \rangle + \left \vert \omega \right \rangle^{-k} \left \vert a \right \rangle + \omega^{-2 k} \left \vert a^2 \right \rangle + \cdots + \omega{-(r - 1) k} \left \vert a^{r - 1} \right \rangle)$
- lemma: $M_a \left \vert \psi_k \right \rangle = \omega^k \left \vert \psi_k \right \rangle$
  - $\begin{aligned}[t]
      M_a \left \vert \psi_1 \right \rangle &= M_a \frac{1}{\sqrt r} (\left \vert 1 \right \rangle + \omega^{-1} \left \vert a \right \rangle + \omega^{-2} \left \vert a^2 \right \rangle + \cdots + \omega^{-(r - 1)} \left \vert a^{r - 1} \right \rangle) \\ 
      &= \frac{1}{\sqrt r} (\left \vert a \right \rangle + \omega^{-1} \left \vert a^2 \right \rangle + \omega^2 \left \vert a^3 \right \rangle + \cdots + \omega^{-(r - 1)} \left \vert a^r = 1 \right \rangle ) \\ 
      &= \frac{\omega}{\sqrt r} (\omega^{-1} \left \vert a \right \rangle + \omega^{-2} \left \vert a^2 \right \rangle + \omega^{-3} \left \vert a^3 \right \rangle + \omega^{-(r - 1) - 1} \left \vert 1 \right \rangle ) \\ 
      &= \omega \left \vert \psi_1 \right \rangle
    \end{aligned}$

## phase estimation algorithm
- input: unitary $U$ and unit vector $\left \vert \psi \right \rangle$
  - $\psi$ is a linear combination of eigenvectors of $U$
  - $U \left \vert \psi_k \right \rangle = e^{2 \pi i \theta_k} \left \vert \psi_k \right \rangle$
- output: $\theta_k$, for some $k$
- $f \approx \frac{k}{r}$

# 10.27 5th

## phase estimation algorithm
- input: unitary $U$, eigenvector $\left \vert \psi \right \rangle$ of $U$
  - $U \left \vert \psi \right \rangle = e^{2 \pi i \theta} \left \vert \psi \right \rangle$
- ouput: $\theta$
- $\Lambda_m(U) \left \vert k \right \rangle \left \vert \psi \right \rangle = \left \vert k \right \rangle U^k \left \vert \psi \right \rangle$
  - $\left \vert k \right \rangle$ has $m$ qubits
  - $\left \vert \psi \right \rangle$ has $n$ qubits
- $\begin{aligned}[t]
    \Lambda_m(U) (H^{\otimes m} \otimes I^{\otimes n}) \left \vert 0^m \right \rangle \left \vert \psi \right \rangle &= \frac{1}{2^{m / 2}} \sum_{k = 0}^{2^m - 1} \left \vert k \right \rangle U^k \left \vert \psi \right \rangle \\ 
    &= \left ( \frac{1}{2^{m / 2}} \sum_{k = 0}^{2^m - 1} e^{2 \pi k i \theta} \left \vert k \right \rangle \right ) \left \vert \psi \right \rangle
  \end{aligned}$

## quantum fourier transform
- $\omega = e^{2 \pi i / 2^m}$
- $\operatorname{QFT}{2^m} \left \vert j \right \rangle = \frac{1}{2^{m / 2}} \sum_{k = 0}^{2^m - 1} \omega^{j k} \left \vert k \right \rangle = \frac{1}{2^{m / 2}} \begin{bmatrix} 1 & 1 & 1 & \cdots & 1 \\ 1 & \omega & \omega^2 & \cdots & \omega^{2^m - 1} \\ 1 & \omega^2 & \omega^4 & \cdots & \omega^{2 (2^m - 1)} \\ \vdots & \vdots & \vdots & \ddots & \vdots \\ 1 & \omega^{2^m - 1} & \omega^{2 (2^m - 1)} & \cdots & \omega^{(2^m - 1)^2} \end{bmatrix}$
- $\operatorname{QFT}_{2^m}^\dagger \left \vert k \right \rangle = \frac{1}{2^{m / 2}} \sum_{j = 0}^{2^m - 1} \omega^{-j k} \left \vert j \right \rangle$
- lemma
  - $\sum_{k = 0}^{2^m - 1} \omega^{k (j - l)} = \begin{cases}
    2^m & j = l \\ 
    0 & j \neq l
  \end{cases}$
  - for $j \neq l$, $\sum_{k = 0}^{2^m - 1} \omega^{k (j - l)} = \sum_{k = 0}^{2^m - 1} (\omega^{j - l})^k = \frac{1 - \omega^{2^m (j - l)}}{1 - \omega^{j - l}} = \frac{1 - (\omega^{2^m})^{j - l}}{1 - \omega^{j - l}} = 0$

## phase estimation, cont.
- $\operatorname{PhaseEst}_m U \left \vert \psi \right \rangle = (\operatorname{QFT}_{2^m}^\dagger \otimes I^{\otimes n}) \Lambda_m(U) (H^{\otimes m} \otimes I^{\otimes m}) (\left \vert 0^m \right \rangle \otimes \left \vert \psi \right \rangle)$
- let $\theta = j / 2^m$
  - $\begin{aligned}[t]
      \operatorname{PhaseEst}_m U \left \vert \psi \right \rangle &= (\operatorname{QFT}_{2^m}^\dagger \otimes I^{\otimes n}) \Lambda_m(U) (H^{\otimes m} \otimes I^{\otimes m}) (\left \vert 0^m \right \rangle \otimes \left \vert \psi \right \rangle) \\ 
      &= (\operatorname{QFT}_{2^m}^\dagger \otimes I^{\otimes n}) \frac{1}{2^{m / 2}} \sum_{k = 0}^{2^m - 1} e^{2 \pi k i \theta} \left \vert k \right \rangle \left \vert \psi \right \rangle \\ 
      &= (\operatorname{QFT}_{2^m}^\dagger \otimes I^{\otimes n}) \frac{1}{2^{m / 2}} \sum_{k = 0}^{2^m - 1} e^{2 \pi k i (j / 2^m)} \left \vert k \right \rangle \left \vert \psi \right \rangle \\ 
      &= (\operatorname{QFT}_{2^m}^\dagger \otimes I^{\otimes n}) \frac{1}{2^{m / 2}} \sum_{k = 0}^{2^m - 1} \omega^{j k} \left \vert k \right \rangle \left \vert \psi \right \rangle \\ 
      &= (\operatorname{QFT}_{2^m}^\dagger \otimes I^{\otimes n}) \operatorname{QFT}_{2^m} \left \vert j \right \rangle \left \vert \psi \right \rangle \\ 
      &= \left \vert j \right \rangle \left \vert \psi \right \rangle
    \end{aligned}$
- $\begin{aligned}[t]
    \operatorname{PhaseEst}_m U \left \vert \psi \right \rangle &= (\operatorname{QFT}_{2^m}^\dagger \otimes I^{\otimes n}) \Lambda_m(U) (H^{\otimes m} \otimes I^{\otimes m}) (\left \vert 0^m \right \rangle \otimes \left \vert \psi \right \rangle) \\ 
    &= (\operatorname{QFT}_{2^m}^\dagger \otimes I^{\otimes n}) \frac{1}{2^{m / 2}} \sum_{k = 0}^{2^m - 1} e^{2 \pi k i \theta} \left \vert k \right \rangle \left \vert \psi \right \rangle \\ 
    &= (\operatorname{QFT}_{2^m}^\dagger \otimes I^{\otimes n}) \frac{1}{2^{m / 2}} \sum_{k = 0}^{2^m - 1} e^{2 \pi k i (j / 2^m)} \left \vert k \right \rangle \left \vert \psi \right \rangle \\ 
    &= \frac{1}{2^m} \sum_{k = 0}^{2^m - 1} \sum_{j = 0}^{2^m - 1} \omega^{2^m k \theta} \omega^{-j k} \left \vert j \right \rangle \left \vert \psi \right \rangle \\ 
    &= \sum_{j = 0}^{2^m - 1} \left ( \frac{1}{2^m} \sum_{k = 0}^{2^m - 1} \omega^{k (2^m \theta - j)} \right ) \left \vert j \right \rangle \left \vert \psi \right \rangle
  \end{aligned}$
- we get $\left \vert j \right \rangle$ with probability $p_j = \left | \frac{1}{2^m} \sum_{k = 0}^{2^m - 1} \omega^{k (2^m \theta - j)} \right |^2$
  - with $0 < \left | \varepsilon \right | \leq \frac{1}{2^{m + 1}}$, we have $\theta = \frac{j}{2^m} + \varepsilon$
  - $\begin{aligned}[t]
    p_j &= \frac{1}{2^{2 m}} \left | \frac{1 - \omega^{2^m (2^m \theta - j)}}{1 - \omega^{2^m \theta - j}} \right |^2 = \frac{1}{2^{2 m}} \left | \frac{1 - \omega^{2^{2 m} \varepsilon}}{1 - \omega^{2^m \varepsilon}} \right |^2 \\ 
    &= \frac{1}{2^{2 m}} \left | \frac{1 - e^{2^{m + 1} \varepsilon \pi i}}{1 - e^{2 \varepsilon \pi i}} \right |^2 \\
    &= \frac{1}{2^{2 m}} \left | 1 + \omega^{(2^{2 m} - 1) \varepsilon} \right |^2 = \frac{1}{2^{2 m}} \left | 1 + e^{2^{m + 1} \varepsilon \pi i} \right |^2 \\ 
    &\geq \frac{1}{2^{2 m}} \left | 1 + e^{\pi i} \right |^2 \\ 
    &\geq \frac{4}{\pi^2} \approx 0.4
  \end{aligned}$

## encoding a number
- $\widetilde{\operatorname{QFT}}_2 = H$
- $\widetilde{\operatorname{QFT}}_{2^{m + 1}} = ( H \otimes I^{\otimes m} ) \bigotimes_{i = 1}^m \left ( \operatorname{CZ}[0, i] \right ) (I \otimes \widetilde{\operatorname{QFT}}_{2^m})$
- number of gates: $\mathcal O(n^2)$

# 11.3 6th

## error
- bit flip
  - $0 \to 1$
  - $1 \to 0$
- add redundancy
  - need massive amounts for quantum computing
- error detection: sender sends, receiver requests retransmit
- error correction: sender sends, receiver corrects
- bit copy: $0 \to 000$, $1 \to 111$
  - receive
    - $000$, $100$, $010$, $001$ understood as 0
    - $110$, $101$, $011$, $111$ understood as 1
- codeword
  - code $\to$ error syndrome
  - $000, 111 \to 00$, no error
  - $100, 011 \to 10$, first bit flipped
  - $010, 101 \to 11$, second bit flipped
  - $001, 110 \to 01$, third bit flipped
- $0 \to \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$, $1 \to \begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix}$
- encoding: $B^k \to B^n$, $k < n$
- $[n, k]$-code
- apply a matrix $P$ to find parity
  - $P = \begin{bmatrix} 1 & 1 & 0 \\ 0 & p & 1 \end{bmatrix}$
  - $P \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix} = P \begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$
- $s' = s + e$
  - $e_1 = \begin{bmatrix} 1 \\ 0 \\ 0 \end{bmatrix}$, $e_2 = \begin{bmatrix} 0 \\ 1 \\ 0 \end{bmatrix}$, $e_3 = \begin{bmatrix} 0 \\ 0 \\ 1 \end{bmatrix}$
  - cube representation
  - $P(s') = P(s + e) = P(s) + P(e) = P(e)$,
  - $P(e_1) = \begin{bmatrix} 1 \\ 0 \end{bmatrix}$, $P(e_2) = \begin{bmatrix} 1 \\ 1 \end{bmatrix}$
- error syndrome $\to$ error
  - $Q \begin{bmatrix} 1 \\ 0 \end{bmatrix} = \begin{bmatrix} 1 \\ 0 \\ 0 \end{bmatrix}$, $Q \begin{bmatrix} 1 \\ 1 \end{bmatrix} = \begin{bmatrix} 0 \\ 1 \\ 0 \end{bmatrix}$, $Q \begin{bmatrix} 0 \\ 1 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 1 \end{bmatrix}$
  - $\text{received} + \text{fix} = s' + Q(P s') = s$
- theorem: error detection is possible iff for all errors $e$, $P e \neq 0$
- theorem: error correction is possible iff all $P e$ are different

## hamming distance
- weight of a bitstring $w \colon B^n \to \mathbb N$: $w(s) = \text{number of 1s in $s$}$
- $d(s, t) = w(s - t) = w(s + t)$
- $d$ is a metric
  - $d(s, t) = 0$ iff $s = t$
  - $d(s, t) = d(t, s)$
  - $d(s, t) \leq d(s, x) + d(x, t)$
- want $P G = 0$ with error syndrome that says "no error"
- $d(G) = \min \left \{ d(s, t) : s, t \in G(B^k) \wedge s \neq t \right \} = \min \left \{ w(s) : s \in G(B^k) \wedge s \neq 0^n \right \}$
- $[n, k, d(G)]$
- assumption: $P(\text{bit flip}) = p$
  - $P(\text{at least two bits flip}) = 3 \cdot p^2 (1 - p) + p^3 = 3 p^2 - 2 p^3$
  - $3 p^2 - 2 p^3 < p \Leftrightarrow p (2 p^2 - 3 p + 1) > 0 \Leftrightarrow p < \frac{1}{2}$
- there is a $[7, 4, 3]$ code
- voyager 2 uses $[24, 12, 8]$ code
