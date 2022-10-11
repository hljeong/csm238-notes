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
- assumption: $f(x) = (a \dot x) \oplus b$
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
