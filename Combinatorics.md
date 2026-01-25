# **Module 1.3: Combinatorics**
*Duration: 3-4 weeks*

## **Week 1: Fundamental Counting Principles**

### **1.1 Basic Counting Rules**

#### **Sum Rule (Rule of Addition)**
- **Principle**: If there are m ways to do task A and n ways to do task B, and they cannot be done simultaneously, then there are m + n ways to choose one task
- **Formal**: |A ∪ B| = |A| + |B| when A ∩ B = ∅
- *Example*: 3 appetizers + 5 main dishes = 8 choices if choosing one item
- *CS Connection*: Menu options, error types, alternative algorithms

#### **Product Rule (Rule of Multiplication)**
- **Principle**: If task A can be done in m ways, and after that task B can be done in n ways, then there are m × n ways to do both
- **Generalization**: For k tasks: m₁ × m₂ × ... × mₖ
- *Example*: 3 shirts × 4 pants = 12 outfits
- *CS Connection*: Nested loops, password combinations, file paths

#### **Subtraction Rule (Inclusion-Exclusion for Two Sets)**
- **Principle**: |A ∪ B| = |A| + |B| - |A ∩ B|
- *Example*: Students taking CS or Math: 40 + 30 - 15 = 55
- *CS Connection*: Union of search results, overlapping permissions

#### **Division Rule**
- **Principle**: If there's a k-to-1 correspondence, divide by k
- *Example*: Counting circular arrangements: n!/n = (n-1)!
- *CS Connection*: Symmetry reduction in search, eliminating duplicates

### **1.2 The Pigeonhole Principle**

#### **Basic Principle**
- **Statement**: If n items are put into m containers with n > m, then at least one container has more than one item
- *Example*: 13 people → at least 2 share a birth month
- *Formal*: ⌈n/m⌉ gives minimum in some container

#### **Generalized Pigeonhole Principle**
- **Statement**: If n items into m containers, then some container has at least ⌈n/m⌉ items
- *Proof*: By contradiction - assume all have < ⌈n/m⌉, then total < m × ⌈n/m⌉ ≤ n

#### **Strong Forms & Applications**
1. **Dirichlet's Principle**: The basic form
2. **Erdős–Szekeres Theorem**: Any sequence of n²+1 distinct numbers contains an increasing or decreasing subsequence of length n+1
3. *CS Applications*:
   - Hashing collisions guaranteed if more keys than buckets
   - Load balancing: some server gets more than average load
   - Cache eviction: if more data than cache size, some data must be evicted
   - Error detection: duplicate check digits, checksums

#### **Constructive vs Non-constructive**
- **Non-constructive**: Proves existence without finding which container
- **Constructive**: Actually finds the crowded container
- *CS Connection*: Existence proofs vs algorithms

### **1.3 Tree Diagrams & Decision Trees**

#### **Systematic Counting with Trees**
- **Root**: Starting point
- **Branches**: Possible choices at each step
- **Leaves**: Final outcomes
- *Example*: Coin flips: H/T branches, 2ⁿ leaves for n flips

#### **Applications to Algorithms**
- **Decision Trees for Sorting**: Minimum height = ⌈log₂(n!)⌉ → Ω(n log n) bound
- **Game Trees**: Chess, tic-tac-toe
- **Parse Trees**: For context-free grammars

### **Practice Problems: Week 1**

#### **Basic Counting**
1. License plates: 3 letters followed by 3 digits. How many possible?
2. Functions f: {1,2,3} → {a,b,c,d}:
   - Total functions: 4³ = 64
   - Injective functions: P(4,3) = 24
   - Surjective functions? (Harder - wait for inclusion-exclusion)

#### **Pigeonhole Problems**
1. Prove: In any 5 points within a unit square, some two are within √2/2 distance
2. Show: Any set of 6 people contains 3 mutual friends or 3 mutual strangers (Ramsey number R(3,3)=6)
3. In a list of n+1 numbers from {1,...,2n}, some number divides another

#### **CS Applications**
1. **Hash Table**: 1000 keys, 100 buckets. What's guaranteed minimum in fullest bucket?
2. **Network**: 10 computers, each connects to at least 1 other. Show at least 2 have same number of connections
3. **File Storage**: 1 million files, 65,536 inodes. What does pigeonhole principle say?

## **Week 2: Permutations & Combinations**

### **2.1 Permutations (Order Matters)**

#### **Basic Permutations**
- **n distinct objects**: n! arrangements
  - 0! = 1 (convention, empty arrangement)
  - *Growth*: n! grows faster than exponential
- **r-permutations**: P(n,r) = n!/(n-r)!
  - *Example*: Race with 8 runners, gold/silver/bronze: P(8,3) = 8×7×6 = 336

#### **Permutations with Repetition**
- **n objects with n₁ identical of type 1, n₂ of type 2, ...**
  - Formula: n!/(n₁! n₂! ... nₖ!)
  - *Example*: MISSISSIPPI: 11!/(1!4!4!2!)
  - *Derivation*: Divide by symmetry (swapping identical items doesn't change arrangement)

#### **Circular Permutations**
- **n objects around circle**: (n-1)!
- **n beads on necklace**: (n-1)!/2 (flipping indistinguishable)
- *CS Connection*: Round-robin scheduling, ring networks

### **2.2 Combinations (Order Doesn't Matter)**

#### **Basic Combinations**
- **n choose r**: C(n,r) = n!/(r!(n-r)!) = $\binom{n}{r}$
  - *Notation*: $\binom{n}{r}$ read "n choose r"
  - *Example*: Lottery 6/49: $\binom{49}{6}$ ≈ 14 million
  - *Symmetry*: $\binom{n}{r} = \binom{n}{n-r}$

#### **Combinations with Repetition**
- **r-combinations from n types with unlimited repetition**: $\binom{n+r-1}{r}$
  - *Stars and Bars*: Represent selection as stars (*) separated by bars (|)
  - *Example*: Choose 5 fruits from 3 types: $\binom{3+5-1}{5} = \binom{7}{5} = 21$
  - *CS Connection*: Number of solutions to x₁ + x₂ + ... + xₙ = r in nonnegative integers

#### **Important Special Cases**
1. $\binom{n}{0} = \binom{n}{n} = 1$
2. $\binom{n}{1} = \binom{n}{n-1} = n$
3. $\binom{n}{2} = n(n-1)/2$ (handshake problem)
4. $\binom{n}{3} = n(n-1)(n-2)/6$

### **2.3 Combinatorial Identities**

#### **Pascal's Identity & Triangle**
- **Pascal's Rule**: $\binom{n}{k} = \binom{n-1}{k-1} + \binom{n-1}{k}$
- **Pascal's Triangle**: Each entry is sum of two above
- *CS Connection*: Dynamic programming for binomial coefficients

#### **Vandermonde's Identity**
- $\binom{m+n}{r} = \sum_{k=0}^{r} \binom{m}{k} \binom{n}{r-k}$
- *Combinatorial Proof*: Choose r from m+n by splitting between two groups

#### **Other Important Identities**
1. **Sum of row**: $\sum_{k=0}^{n} \binom{n}{k} = 2^n$
2. **Alternating sum**: $\sum_{k=0}^{n} (-1)^k \binom{n}{k} = 0$ for n ≥ 1
3. **Column sums**: $\sum_{k=r}^{n} \binom{k}{r} = \binom{n+1}{r+1}$ (hockey-stick identity)

### **Practice Problems: Week 2**

#### **Permutations**
1. How many anagrams of "COMPUTER" have all vowels together?
2. Arrange 5 math, 4 CS, 3 physics books. How many if same subject together?
3. Round table: 4 couples (8 people). How many arrangements if couples sit together?

#### **Combinations**
1. Poker hands:
   - Total: $\binom{52}{5}$
   - One pair: $\binom{13}{1} \binom{4}{2} \binom{12}{3} \binom{4}{1}^3$
   - Calculate probabilities
2. Committee of 5 from 7 men, 6 women:
   - At least 3 women
   - John and Jane won't serve together

#### **Stars and Bars**
1. Nonnegative integer solutions to x+y+z = 10: $\binom{10+3-1}{10} = \binom{12}{10} = 66$
2. Positive solutions to x+y+z = 10: $\binom{10-1}{3-1} = \binom{9}{2} = 36$
3. Solutions with x ≥ 2, y ≥ 0, z ≥ 1: Let x' = x-2, z' = z-1, then x'+y+z' = 7

#### **CS Applications**
1. **Bit Strings**: How many length-n bit strings with exactly k ones? $\binom{n}{k}$
2. **Network Paths**: Grid 10×10, only right/up moves. Paths from bottom-left to top-right? $\binom{20}{10}$
3. **Error Detection**: 10-bit strings with at most 2 ones: $\binom{10}{0} + \binom{10}{1} + \binom{10}{2}$

## **Week 3: Binomial Theorem & Advanced Counting**

### **3.1 The Binomial Theorem**

#### **Statement & Proof**
- $(x + y)^n = \sum_{k=0}^{n} \binom{n}{k} x^{n-k} y^k$
- **Proof**:
  1. Combinatorial: Choose which factors contribute y (k of them)
  2. Inductive: Using Pascal's identity
- **Examples**:
  - $(1+x)^n = \sum_{k=0}^{n} \binom{n}{k} x^k$
  - $(1+1)^n = 2^n = \sum_{k=0}^{n} \binom{n}{k}$
  - $(1-1)^n = 0 = \sum_{k=0}^{n} (-1)^k \binom{n}{k}$ for n ≥ 1

#### **Multinomial Theorem**
- $(x₁ + x₂ + ... + xₖ)^n = \sum_{n₁+...+nₖ=n} \frac{n!}{n₁! n₂! ... nₖ!} x₁^{n₁} x₂^{n₂} ... xₖ^{nₖ}$
- *Example*: Coefficient of x²y³z in (x+y+z)⁶: 6!/(2!3!1!) = 60

### **3.2 Inclusion-Exclusion Principle**

#### **Principle for n Sets**
- $|A₁ ∪ A₂ ∪ ... ∪ Aₙ| = \sum |Aᵢ| - \sum |Aᵢ ∩ Aⱼ| + \sum |Aᵢ ∩ Aⱼ ∩ Aₖ| - ... + (-1)^{n+1} |A₁ ∩ ... ∩ Aₙ|$
- **Pattern**: Add singles, subtract pairs, add triples, subtract quads, ...

#### **Derangements (Fixed-Point Free Permutations)**
- **!n or Dₙ**: Permutations with no element in original position
- **Formula**: $!n = n! \sum_{k=0}^{n} \frac{(-1)^k}{k!}$
- **Recurrence**: $!n = (n-1)(!(n-1) + !(n-2))$ with !0=1, !1=0
- *Example*: 4! = 24 permutations, !4 = 9 derangements
- *CS Connection*: Hat-check problem, secret Santa, error-free arrangements

#### **Counting with "At Least" Conditions**
- **Strategy**: Convert to inclusion-exclusion
- *Example*: How many permutations of {1,...,8} have at least one fixed point?
  - Let Aᵢ = permutations fixing i
  - Answer = total - !8 = 8! - !8

### **3.3 Recurrence Relations (Combinatorial View)**

#### **Modeling with Recurrences**
- **Fibonacci**: Fₙ = Fₙ₋₁ + Fₙ₋₂, F₀=0, F₁=1
  - *Combinatorial meaning*: Ways to tile 1×n board with 1×1 and 1×2 tiles
- **Catalan Numbers**: Cₙ = $\frac{1}{n+1}\binom{2n}{n}$
  - *Recurrence*: Cₙ = $\sum_{i=0}^{n-1} C_i C_{n-1-i}$, C₀=1
  - *Applications*: Balanced parentheses, binary trees, polygon triangulation

#### **Solving Simple Recurrences**
1. **Iteration/Unfolding**: Keep applying recurrence
2. **Guess & Verify**: Guess closed form, prove by induction
3. *Example*: aₙ = 2aₙ₋₁ + 1, a₀=0 → aₙ = 2ⁿ - 1

### **Practice Problems: Week 3**

#### **Binomial Theorem**
1. Expand $(2x - 3y)^5$
2. Find coefficient of $x^4$ in $(1+2x)^{10}$
3. Prove: $\sum_{k=0}^{n} \binom{n}{k}^2 = \binom{2n}{n}$ (Hint: $(1+x)^n(1+x)^n = (1+x)^{2n}$)

#### **Inclusion-Exclusion**
1. How many integers 1-1000 are divisible by 2, 3, or 5?
   - |A∪B∪C| = |A|+|B|+|C| - |A∩B|-|A∩C|-|B∩C| + |A∩B∩C|
   - = 500 + 333 + 200 - 166 - 100 - 66 + 33 = 734
2. How many onto functions f: {1,2,3,4} → {a,b,c}?
   - Total: 3⁴ = 81
   - Subtract those missing at least one element
   - Answer: 81 - 3×2⁴ + 3×1⁴ - 0 = 36
3. Secret Santa with 5 people. Probability no one gets own gift? !5/5! = 44/120

#### **Recurrences**
1. Solve: aₙ = 3aₙ₋₁, a₀=5 → aₙ = 5·3ⁿ
2. Solve: aₙ = aₙ₋₁ + n, a₀=0 → aₙ = n(n+1)/2
3. Binary strings length n with no consecutive 0s: aₙ = aₙ₋₁ + aₙ₋₂ (Fibonacci)

#### **CS Applications**
1. **Cache Line Conflict**: 4 lines, 8 addresses mapping to lines. Probability no line has >2 addresses?
2. **Error Correction**: 8-bit codewords with at least 3 ones and at most 5 ones. How many?
3. **Database Queries**: 3 tables join. Estimate result size using inclusion-exclusion on key constraints.

## **Week 4: Advanced Topics & Applications**

### **4.1 Generating Functions**

#### **Ordinary Generating Functions (OGFs)**
- **Definition**: For sequence a₀, a₁, a₂, ...: G(x) = $\sum_{n=0}^{∞} a_n x^n$
- **Examples**:
  - aₙ = 1: 1/(1-x) = 1 + x + x² + ...
  - aₙ = $\binom{m}{n}$: (1+x)ᵐ
  - Fibonacci: F(x) = x/(1-x-x²)

#### **Solving Recurrences with OGFs**
1. Write recurrence
2. Multiply by xⁿ and sum over n
3. Solve for G(x)
4. Extract coefficients
- *Example*: Fibonacci: Fₙ = Fₙ₋₁ + Fₙ₋₂ → F(x) = x/(1-x-x²) → Fₙ = (φⁿ - ψⁿ)/√5

#### **Applications to Counting**
- **Combinatorial Interpretation**: xⁿ represents choosing something n times
- *Example*: OGF for number of ways to make change with pennies, nickels, dimes:
  - G(x) = 1/((1-x)(1-x⁵)(1-x¹⁰))

### **4.2 Stirling Numbers**

#### **Stirling Numbers of the First Kind**
- **s(n,k)**: Number of permutations of n elements with k cycles
- **Recurrence**: s(n,k) = s(n-1,k-1) + (n-1)s(n-1,k)
- *Example*: s(4,2) = 11 (permutations of 4 with 2 cycles)

#### **Stirling Numbers of the Second Kind**
- **S(n,k)**: Number of ways to partition n elements into k nonempty subsets
- **Recurrence**: S(n,k) = S(n-1,k-1) + k·S(n-1,k)
- *CS Connection*: Equivalence relations with k classes, clustering into k groups

#### **Relation to Bell Numbers**
- **Bell Number Bₙ**: Total partitions of n elements
  - Bₙ = $\sum_{k=0}^{n} S(n,k)$
  - Recurrence: Bₙ₊₁ = $\sum_{k=0}^{n} \binom{n}{k} B_k$

### **4.3 Combinatorial Optimization Preview**

#### **Matching Problems**
- **Bipartite Matching**: Assign tasks to workers
- **Stable Marriage**: Gale-Shapley algorithm
- *CS Connection*: Job scheduling, resource allocation

#### **Graph Coloring & Scheduling**
- **Chromatic Number**: Minimum colors for no adjacent same color
- **Application**: Register allocation in compilers
- **Course Scheduling**: Courses as vertices, conflicts as edges

### **4.4 Probability Fundamentals (Preview)**

#### **Sample Spaces & Events**
- **Sample Space S**: Set of all outcomes
- **Event E ⊆ S**: Subset of outcomes
- **Probability for equally likely**: P(E) = |E|/|S|

#### **Basic Probability via Counting**
- *Example*: Poker hand probabilities
  - Royal flush: 4/$\binom{52}{5}$ ≈ 0.000154%
  - Full house: Calculate using combinations

#### **Birthday Paradox**
- With 23 people, probability of shared birthday > 50%
- With 50 people, probability > 97%
- *Analysis*: Use product rule for complements
  - P(no shared) = 365/365 × 364/365 × ... × (365-n+1)/365

### **Practice Problems: Week 4**

#### **Generating Functions**
1. Find OGF for aₙ = 2ⁿ + 3ⁿ: 1/(1-2x) + 1/(1-3x)
2. Use OGF to solve: aₙ = 2aₙ₋₁ + 2ⁿ, a₀=1
3. How many ways to make $1 with pennies, nickels, dimes, quarters? (Coin problem)

#### **Stirling Numbers**
1. Compute S(5,2) and S(5,3)
2. Prove: $\sum_{k=0}^{n} S(n,k) x(x-1)...(x-k+1) = x^n$ (Stirling inversion)
3. Number of onto functions f: {1,...,n} → {1,...,k} = k! S(n,k)

#### **Probability via Counting**
1. Poker: Probability of flush (not straight flush)?
2. Bridge: Probability 13-card hand has all cards of same suit?
3. Birthday paradox: For n=30, calculate exact probability of at least one shared birthday

#### **CS Applications**
1. **Cache Analysis**: Direct-mapped cache with 8 lines. 9 addresses map randomly. Probability of no conflicts?
2. **Load Balancing**: 10 jobs to 3 servers. Probability some server gets ≥5 jobs?
3. **Network Reliability**: 20 links, each fails with probability 0.01. Probability network remains connected?

## **Comprehensive Assessment for Module 1.3**

### **Theory Exam (Sample)**
**Part A: Definitions (15%)**
1. Define: pigeonhole principle, combination vs permutation, derangement, Stirling number of second kind
2. State binomial theorem and inclusion-exclusion principle

**Part B: Proofs (35%)**
1. Prove: $\binom{n}{k} = \binom{n-1}{k-1} + \binom{n-1}{k}$ combinatorially
2. Prove: Number of solutions to x₁+...+xₖ=n in nonnegative integers is $\binom{n+k-1}{n}$
3. Prove: !n = n! $\sum_{k=0}^{n} (-1)^k/k!$ using inclusion-exclusion

**Part C: Problems (50%)**
1. How many 5-card hands have at least one card from each suit?
2. How many ways to arrange letters in "ALGORITHM" with no two vowels adjacent?
3. Solve recurrence: aₙ = 4aₙ₋₁ - 4aₙ₋₂, a₀=1, a₁=3
4. In a group of 10 people, what's probability that no 3 share same birth month?

### **Practical Implementation Projects**

#### **Project 1: Combinatorics Calculator Library**
```python
class Combinatorics:
    def factorial(self, n):
        # Implement with memoization
        
    def nCr(self, n, r):
        # Using Pascal's rule for efficiency
        
    def nPr(self, n, r):
        # Permutations
        
    def stars_and_bars(self, n, k):
        # Solutions to x1+...+xk=n
        
    def derangement(self, n):
        # !n calculation
        
    def stirling2(self, n, k):
        # S(n,k) using recurrence
        
    def binomial_expand(self, expr, n):
        # Expand (ax+by)^n
```

#### **Project 2: Birthday Paradox Simulator**
- Input: Group size n
- Simulation: Generate random birthdays, check collisions
- Analytical: Compute exact probability
- Visualize: Probability vs group size

#### **Project 3: Poker Hand Analyzer**
- Generate all 5-card combinations ($\binom{52}{5}$ = 2.6M)
- Classify each hand (pair, two pair, etc.)
- Compute exact probabilities
- Compare with theoretical values

### **Common CS Interview Questions Covered**
1. "How many trailing zeros in 100!?" (Count factors of 5)
2. "How many ways to climb n stairs taking 1 or 2 steps?" (Fibonacci)
3. "Probability that two numbers randomly chosen from 1..n are coprime?" (≈ 6/π²)
4. "How many BSTs with n nodes?" (Catalan numbers)
5. "Design a hash function to minimize birthday paradox collisions"

### **Transition Checklist to Module 1.4**
Before moving to Graph Theory, ensure you can:
- ✅ Apply product/sum rules to multi-step counting problems
- ✅ Use pigeonhole principle in proofs and algorithm analysis
- ✅ Calculate permutations/combinations with and without repetition
- ✅ Apply binomial theorem and understand combinatorial identities
- ✅ Use inclusion-exclusion for complex counting problems
- ✅ Set up and solve simple recurrence relations
- ✅ Compute probabilities via counting for equally likely outcomes

### **Resources for Module 1.3**

#### **Primary Texts**
- "Concrete Mathematics" by Graham, Knuth, Patashnik (Chapters 5-7)
- "Discrete Mathematics and Its Applications" by Rosen (Chapters 6, 8)

#### **Interactive Tools**
- **Python's itertools**: permutations(), combinations()
- **Desmos**: Plotting generating functions
- **Wolfram Alpha**: Binomial expansions, Stirling numbers

#### **Visual Learning**
- **3Blue1Brown**: "Binomial Theorem & Pascal's Triangle"
- **Numberphile**: "The Pigeonhole Principle", "Birthday Paradox"

#### **Practice Platforms**
- **Project Euler**: Problems 15, 53, 113, 240 (combinatorics)
- **LeetCode**: "Combination Sum", "Permutations" problems
- **Brilliant.org**: Combinatorics course

---

**Next Module**: **Module 1.4: Graph Theory Basics** - Modeling networks, social connections, web pages, and more with vertices and edges. Essential for algorithms, databases, and networking.

**Immediate Action**: Complete the Module 1.3 assessment. If struggling with any concept, try the "combinatorial proof" approach: explain why both sides of an identity count the same thing in different ways.
