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

|| classical | quantum |
| --: | :-: | :-: |
| software | boolean algebra | linear algebra |
| hardware | classical mechanics | quantum mechanics |

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
- comparison between probabilitic and quantum
  |       | probabilistic           | quantum              |
  | --:   | :-:                     | :-:                  |
  |       | real                    | complex              |
  | state | vector of probabilities | vector of amplitudes |
  |       | $\sum p_i = 1$          | $\sum |a|^2 = 1$     |
  | step  | stochastic matrix       | unitary matrix       |
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
