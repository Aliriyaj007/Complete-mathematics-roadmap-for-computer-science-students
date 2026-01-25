# **Module 1.2: Set Theory**
*Duration: 3-4 weeks*

## **Week 1: Foundational Set Concepts & Operations**

### **1.1 Sets: The Building Blocks**

#### **What is a Set?**
- **Definition**: A collection of distinct, well-defined objects called elements or members
- **Notation**: 
  - List form: A = {1, 2, 3, 4}
  - Set-builder: {x ∈ ℤ | x > 0 ∧ x < 5}
  - *CS Connection*: Arrays, lists, databases are essentially sets with additional structure

#### **Key Concepts & Terminology**
- **Membership**: a ∈ A (a is in A), a ∉ A (a is not in A)
- **Cardinality**: |A| = number of elements in A (finite, infinite, countable)
- **Important Standard Sets**:
  - ℕ = {0, 1, 2, 3, ...} or {1, 2, 3, ...} (depends on convention)
  - ℤ = {..., -2, -1, 0, 1, 2, ...}
  - ℚ = {p/q | p, q ∈ ℤ, q ≠ 0}
  - ℝ = real numbers
  - ∅ = {} (empty set)
  - *CS Connection*: Data types correspond to these sets (int→ℤ, float→ℝ)

#### **Subsets & Power Sets**
- **Subset**: A ⊆ B iff ∀x(x ∈ A → x ∈ B)
  - **Proper Subset**: A ⊂ B iff A ⊆ B ∧ A ≠ B
  - **Venn Diagrams**: Visual representation
- **Power Set**: P(A) = {X | X ⊆ A}
  - *Example*: If A = {1, 2}, then P(A) = {∅, {1}, {2}, {1, 2}}
  - *Theorem*: If |A| = n, then |P(A)| = 2ⁿ
  - *CS Connection*: All possible states in a system, all subsets in combinatorial problems

#### **Basic Set Operations**
- **Union**: A ∪ B = {x | x ∈ A ∨ x ∈ B}
- **Intersection**: A ∩ B = {x | x ∈ A ∧ x ∈ B}
- **Difference**: A \ B = {x | x ∈ A ∧ x ∉ B} (also A - B)
- **Complement**: Aᶜ = {x ∈ U | x ∉ A} where U is universal set
- **Symmetric Difference**: A Δ B = (A \ B) ∪ (B \ A)
  - *CS Connection*: XOR operation, finding unique elements

### **Practice Problems: Week 1**

#### **Basic Operations**
1. Let A = {1, 3, 5, 7}, B = {2, 4, 6, 8}, C = {1, 2, 3, 4}
   - Find: A ∪ C, B ∩ C, A \ C, C \ A, A Δ C
   - Compute: |P(A ∩ C)|

2. Prove: A \ B = A ∩ Bᶜ

3. Draw Venn diagrams for:
   - (A ∪ B) ∩ C
   - (A \ B) ∪ (B \ A)

#### **CS Applications**
1. **Database Query Translation**:
   - "Employees in DeptA or DeptB but not both" → Set expression
   - Implement as SQL and Python set operations

2. **Memory Management**:
   - Model allocated vs free memory blocks as sets
   - Find fragmentation: contiguous free blocks

## **Week 2: Advanced Set Properties & Proofs**

### **2.1 Set Identities & Proof Techniques**

#### **Important Set Identities** (Dual to Logical Equivalences)
1. **Commutative Laws**: 
   - A ∪ B = B ∪ A
   - A ∩ B = B ∩ A

2. **Associative Laws**:
   - (A ∪ B) ∪ C = A ∪ (B ∪ C)
   - (A ∩ B) ∩ C = A ∩ (B ∩ C)

3. **Distributive Laws**:
   - A ∪ (B ∩ C) = (A ∪ B) ∩ (A ∪ C)
   - A ∩ (B ∪ C) = (A ∩ B) ∪ (A ∩ C)

4. **De Morgan's Laws**:
   - (A ∪ B)ᶜ = Aᶜ ∩ Bᶜ
   - (A ∩ B)ᶜ = Aᶜ ∪ Bᶜ

5. **Idempotent Laws**:
   - A ∪ A = A
   - A ∩ A = A

6. **Identity Laws**:
   - A ∪ ∅ = A
   - A ∩ U = A

7. **Domination Laws**:
   - A ∪ U = U
   - A ∩ ∅ = ∅

#### **Proof Methods for Set Equality**
1. **Element-Chasing Proof**:
   - To prove A = B, show: ∀x(x ∈ A ↔ x ∈ B)
   - *Template*:
     (→) Assume x ∈ A, show x ∈ B
     (←) Assume x ∈ B, show x ∈ A

2. **Using Set Identities**:
   - Transform one side to the other using known identities
   - Similar to algebraic manipulation

3. **Venn Diagram Proof** (for visualization, not formal proof)

#### **Example Proof: Distributive Law**
**Prove**: A ∪ (B ∩ C) = (A ∪ B) ∩ (A ∪ C)

**Element-chasing proof**:
(→) Let x ∈ A ∪ (B ∩ C)
    Then x ∈ A ∨ x ∈ (B ∩ C)
    Case 1: x ∈ A → x ∈ A ∪ B ∧ x ∈ A ∪ C → x ∈ (A ∪ B) ∩ (A ∪ C)
    Case 2: x ∈ B ∩ C → x ∈ B ∧ x ∈ C → x ∈ A ∪ B ∧ x ∈ A ∪ C → x ∈ (A ∪ B) ∩ (A ∪ C)

(←) Let x ∈ (A ∪ B) ∩ (A ∪ C)
    Then x ∈ A ∪ B ∧ x ∈ A ∪ C
    If x ∈ A: then x ∈ A ∪ (B ∩ C)
    If x ∉ A: then from x ∈ A ∪ B, x ∈ B; from x ∈ A ∪ C, x ∈ C
              So x ∈ B ∩ C → x ∈ A ∪ (B ∩ C)

### **2.2 Indexed Sets & Infinite Operations**

#### **Indexed Families of Sets**
- **Notation**: {Aᵢ | i ∈ I} where I is an index set
- **Examples**:
  - For i ∈ ℕ, Aᵢ = [0, 1/i] (intervals)
  - For n ∈ ℕ, Sₙ = {k ∈ ℕ | k ≤ n}

#### **Generalized Union & Intersection**
- ⋃_{i∈I} Aᵢ = {x | ∃i ∈ I (x ∈ Aᵢ)}
- ⋂_{i∈I} Aᵢ = {x | ∀i ∈ I (x ∈ Aᵢ)}
- *CS Connection*: Union of multiple tables in database, intersection of search results

#### **Important Examples**
- **De Morgan's for Indexed Sets**:
  - (⋃_{i∈I} Aᵢ)ᶜ = ⋂_{i∈I} Aᵢᶜ
  - (⋂_{i∈I} Aᵢ)ᶜ = ⋃_{i∈I} Aᵢᶜ

- **Distributive Laws**:
  - A ∪ (⋂_{i∈I} Bᵢ) = ⋂_{i∈I} (A ∪ Bᵢ)
  - A ∩ (⋃_{i∈I} Bᵢ) = ⋃_{i∈I} (A ∩ Bᵢ)

### **Practice Problems: Week 2**

#### **Set Proofs**
1. Prove using element-chasing: A Δ B = (A ∪ B) \ (A ∩ B)

2. Prove using set identities: (A \ B) \ C = A \ (B ∪ C)

3. Prove or disprove: If A ∪ B = A ∪ C, then B = C

#### **Indexed Sets**
1. Let Aₙ = {x ∈ ℝ | -1/n ≤ x ≤ 1/n} for n ∈ ℕ⁺
   - Find: ⋂_{n=1}^∞ Aₙ
   - Find: ⋃_{n=1}^∞ Aₙ

2. Prove generalized De Morgan's: (⋃_{i∈I} Aᵢ)ᶜ = ⋂_{i∈I} Aᵢᶜ

#### **CS Applications**
1. **Cache Analysis**:
   - Let Cₜ = set of cache lines at time t
   - Model cache updates as set operations
   - Compute hit rate as |Cₜ ∩ R|/|R| where R is request set

2. **Database Indexing**:
   - Multiple indices as ⋂ operations
   - Union of search conditions as ⋃ operations

## **Week 3: Relations & Functions**

### **3.1 Cartesian Products & Relations**

#### **Ordered Pairs & n-tuples**
- **Ordered Pair**: (a, b) where order matters: (a, b) ≠ (b, a) unless a = b
- **Cartesian Product**: A × B = {(a, b) | a ∈ A ∧ b ∈ B}
  - *Example*: {1, 2} × {a, b} = {(1,a), (1,b), (2,a), (2,b)}
  - |A × B| = |A| × |B| for finite sets
  - *Generalization*: A₁ × A₂ × ... × Aₙ (n-ary tuples)
  - *CS Connection*: Database tuples, multi-dimensional arrays, function parameters

#### **Relations**
- **Definition**: A relation R from A to B is a subset of A × B
  - Notation: a R b means (a, b) ∈ R
  - **Domain**: dom(R) = {a ∈ A | ∃b ∈ B (a R b)}
  - **Range**: ran(R) = {b ∈ B | ∃a ∈ A (a R b)}
- **Types of Relations**:
  - **Binary Relation**: Between two sets
  - **n-ary Relation**: Subset of A₁ × A₂ × ... × Aₙ
  - **Relation on A**: Subset of A × A (most common in CS)

#### **Properties of Relations on a Set A**
1. **Reflexive**: ∀a ∈ A (a R a)
   - *Example*: ≤ on ℤ, "is connected to" in networks

2. **Irreflexive**: ∀a ∈ A ¬(a R a)
   - *Example*: < on ℤ, "is parent of"

3. **Symmetric**: ∀a,b ∈ A (a R b → b R a)
   - *Example*: "is sibling of", "is connected to" in undirected graphs

4. **Antisymmetric**: ∀a,b ∈ A ((a R b ∧ b R a) → a = b)
   - *Example*: ⊆ on sets, ≤ on numbers

5. **Transitive**: ∀a,b,c ∈ A ((a R b ∧ b R c) → a R c)
   - *Example*: "is ancestor of", < on numbers

6. **Equivalence Relation**: Reflexive, symmetric, transitive
   - *CS Connection*: Equality testing, clustering, version control

7. **Partial Order**: Reflexive, antisymmetric, transitive
   - *CS Connection*: Task dependencies, inheritance hierarchies

#### **Special Relations**
- **Equality Relation**: = (smallest equivalence relation)
- **Universal Relation**: A × A (contains all pairs)
- **Empty Relation**: ∅ (contains no pairs)

### **3.2 Equivalence Relations & Partitions**

#### **Equivalence Classes**
- **Definition**: [a] = {x ∈ A | a R x} (the equivalence class of a)
- **Properties**:
  - a ∈ [a] (reflexivity ensures this)
  - [a] = [b] iff a R b
  - Either [a] = [b] or [a] ∩ [b] = ∅ (equivalence classes partition A)

#### **Partitions**
- **Definition**: A partition of A is a collection of nonempty, disjoint subsets whose union is A
- **Fundamental Theorem**: Every equivalence relation induces a partition (its equivalence classes), and every partition induces an equivalence relation
- *CS Connection*: File system directories, modular arithmetic in cryptography, network segmentation

#### **Examples of Equivalence Relations**
1. **Congruence modulo n**: a ≡ b (mod n) iff n | (a - b)
   - Equivalence classes: [0], [1], ..., [n-1]
   - *CS Connection*: Hash functions, circular buffers

2. **Graph Connectivity**: Two vertices are related if there's a path between them
   - Equivalence classes: connected components

3. **String equivalence**: Strings are related if they have same length (or same hash)

### **Practice Problems: Week 3**

#### **Relations**
1. Let R be relation on ℤ: a R b iff a - b is even
   - Prove R is equivalence relation
   - Find equivalence classes
   - How many distinct classes are there?

2. Let R be relation on sets: A R B iff |A| = |B|
   - Prove R is equivalence relation
   - Describe equivalence classes for finite sets

3. For relation "divides" on ℕ: a R b iff a|b
   - Which properties does it have? (reflexive, transitive, antisymmetric?)

#### **CS Applications**
1. **File System Design**:
   - Model directories as equivalence classes (files with same path prefix)
   - Design equivalence relation for file permissions

2. **Network Protocols**:
   - Equivalence relation: "can communicate directly"
   - Partition network into broadcast domains

3. **Object-Oriented Programming**:
   - instanceof relation: is it reflexive, symmetric, transitive?
   - equals() method: should be equivalence relation

## **Week 4: Functions & Cardinality**

### **4.1 Functions as Special Relations**

#### **Function Definition**
- **Function**: A relation f ⊆ A × B such that:
  1. ∀a ∈ A ∃b ∈ B ((a, b) ∈ f)  (total/defined everywhere)
  2. If (a, b₁) ∈ f and (a, b₂) ∈ f, then b₁ = b₂ (well-defined/unambiguous)
- **Notation**: f: A → B
  - **Domain**: A
  - **Codomain**: B  
  - **Range/Image**: f(A) = {f(a) | a ∈ A} ⊆ B

#### **Function Properties**
1. **Injective (One-to-One)**: ∀a₁,a₂ ∈ A (f(a₁) = f(a₂) → a₁ = a₂)
   - *Visual*: No two arrows hit same element in B
   - *CS Connection*: Hash functions (ideal), encryption

2. **Surjective (Onto)**: ∀b ∈ B ∃a ∈ A (f(a) = b)
   - *Visual*: Every element in B gets hit
   - *CS Connection*: Total coverage in mappings

3. **Bijective**: Both injective and surjective
   - *Implication*: Inverse function exists
   - *CS Connection*: Perfect hashing, bijective compression

#### **Function Operations**
- **Composition**: f: A → B, g: B → C, then g∘f: A → C, (g∘f)(a) = g(f(a))
  - *Associative*: h∘(g∘f) = (h∘g)∘f
  - *Not commutative* in general

- **Inverse**: If f is bijective, f⁻¹: B → A exists with f⁻¹(b) = a iff f(a) = b
  - *Properties*: f⁻¹∘f = id_A, f∘f⁻¹ = id_B

- **Identity Function**: id_A: A → A, id_A(a) = a

#### **Special Functions in CS**
1. **Floor/Ceiling**: ⌊x⌋, ⌈x⌉
2. **Factorial**: n!
3. **Logarithm**: log_b(x)
4. **Modulo**: f(x) = x mod n
5. **Hash Functions**: Ideally injective, practically not

### **4.2 Cardinality & Countability**

#### **Comparing Set Sizes**
- **Same Cardinality**: |A| = |B| if ∃ bijection f: A → B
- **Finite Sets**: Cardinality = number of elements
- **Infinite Sets**: More subtle!

#### **Countably Infinite Sets**
- **Definition**: |A| = |ℕ| (can be listed: a₀, a₁, a₂, ...)
- **Examples**:
  - ℤ: List as 0, 1, -1, 2, -2, 3, -3, ...
  - ℕ × ℕ: Use Cantor pairing: (0,0), (0,1), (1,0), (0,2), (1,1), (2,0), ...
  - ℚ: More complex listing exists

#### **Uncountable Sets**
- **Definition**: Infinite but not countably infinite
- **Cantor's Diagonal Argument**: Proves |ℝ| > |ℕ|
  - *CS Connection*: Existence of uncomputable functions

#### **Important Theorems**
1. **Cantor's Theorem**: For any set A, |A| < |P(A)|
   - *Proof*: Diagonalization argument
   - *CS Connection*: Hierarchy theorems in complexity

2. **Schröder-Bernstein Theorem**: If |A| ≤ |B| and |B| ≤ |A|, then |A| = |B|
   - (Where |A| ≤ |B| means ∃ injection A → B)

3. **Countable Union of Countable Sets is Countable**

### **4.3 Sequences & Summations**

#### **Sequences as Functions**
- **Sequence**: Function a: ℕ → S, written a₀, a₁, a₂, ...
- **Types**:
  - Arithmetic: aₙ = a + nd
  - Geometric: aₙ = arⁿ
  - Recurrence: aₙ defined in terms of previous terms
  - *CS Connection*: Arrays, time series data, algorithm iterations

#### **Summations & Series**
- **Notation**: ∑_{i=m}^{n} aᵢ
- **Important Formulas**:
  - ∑_{i=1}^{n} i = n(n+1)/2
  - ∑_{i=1}^{n} i² = n(n+1)(2n+1)/6
  - ∑_{i=0}^{n} rⁱ = (rⁿ⁺¹ - 1)/(r - 1) for r ≠ 1
- *CS Connection*: Algorithm analysis, loop computations

#### **Big-O Notation Preview**
- f(n) = O(g(n)) means ∃c,n₀ ∀n≥n₀ (f(n) ≤ c·g(n))
- *CS Connection*: Algorithm complexity analysis (coming in Phase 2)

### **Practice Problems: Week 4**

#### **Functions**
1. For f: ℤ → ℤ, f(x) = 2x + 3
   - Is f injective? surjective? bijective?
   - Find f⁻¹ if it exists

2. Prove: Composition of two injective functions is injective
   - Give counterexample if not true for surjective

3. Let f: A → B, g: B → C
   - Prove: If g∘f is injective, then f is injective
   - Disprove: If g∘f is injective, then g is injective

#### **Cardinality**
1. Prove: |ℤ| = |ℕ|
2. Prove: |(0,1)| = |ℝ|
3. Prove: Power set of ℕ is uncountable
4. Is set of all Java programs countable? Why?

#### **CS Applications**
1. **Database Design**:
   - Primary key field must be injective function
   - Foreign key is function from one table to another

2. **Memory Addressing**:
   - Virtual to physical address mapping: should be bijective
   - Page table as function

3. **Cryptography**:
   - Encryption: should be bijective (to decrypt)
   - Hash functions: aim for injective (no collisions)

## **Comprehensive Assessment for Module 1.2**

### **Theory Exam (Sample)**
**Part A: Definitions (20%)**
1. Define: power set, equivalence relation, bijective function, countable set
2. Give CS example for each

**Part B: Proofs (40%)**
1. Prove: A ∩ (B ∪ C) = (A ∩ B) ∪ (A ∩ C) using element-chasing
2. Prove: Composition of surjective functions is surjective
3. Prove: If R is equivalence relation, then [a] = [b] iff a R b
4. Prove: |A ∪ B| = |A| + |B| - |A ∩ B| for finite sets

**Part C: Problems (40%)**
1. Let A = {n ∈ ℕ | 1 ≤ n ≤ 10}, relation R: a R b iff a + b is even
   - Show R is equivalence relation
   - Find all equivalence classes

2. Function f: ℝ → ℝ, f(x) = x³ - x
   - Is f injective? surjective? Find f([0,2]) (image of interval)

3. Are these sets countable? Prove:
   - Set of all finite binary strings
   - Set of all infinite binary sequences

### **Practical Implementation Projects**

#### **Project 1: Set Operations Library**
```python
class MathSet:
    def __init__(self, elements):
        self.elements = set(elements)
    
    def union(self, other):
        # Implement
        pass
    
    def intersection(self, other):
        # Implement
        pass
    
    def complement(self, universe):
        # Implement
        pass
    
    def is_subset(self, other):
        # Implement
        pass
    
    def power_set(self):
        # Implement - generate all subsets
        pass
    
    def cartesian_product(self, other):
        # Implement
        pass
    
    def is_equivalence_relation(self, pairs):
        # Given list of pairs (a,b), check if it's equivalence relation
        pass
```

#### **Project 2: Function Analyzer**
- Input: Domain, codomain, list of (input, output) pairs
- Output: Determines if function is well-defined, injective, surjective, bijective
- Bonus: If bijective, compute and verify inverse

#### **Project 3: Cardinality Comparator**
- For given sets (described algorithmically), determine if they have same cardinality
- Implement Cantor pairing for ℕ × ℕ → ℕ
- Implement diagonalization proof visualization

### **Common CS Interview Questions Covered**
1. "What's the difference between ∈ and ⊆?"
2. "Prove that a set with n elements has 2ⁿ subsets"
3. "Is the set of all programs countable? Why?"
4. "Design an equivalence relation for version control"
5. "Why must encryption be a bijective function?"

### **Transition Checklist to Module 1.3**
Before moving to Combinatorics, ensure you can:
- ✅ Perform all basic set operations without hesitation
- ✅ Prove set identities using element-chasing
- ✅ Determine if a relation is reflexive/symmetric/transitive
- ✅ Classify functions as injective/surjective/bijective
- ✅ Explain countability and give examples
- ✅ Implement set operations in code

### **Resources for Module 1.2**

#### **Primary Texts**
- "Book of Proof" by Richard Hammack (Chapters 1-4, 12)
- "Discrete Mathematics and Its Applications" by Rosen (Chapters 2, 9)

#### **Interactive Tools**
- **Desmos**: Venn diagram visualization
- **Python sets**: Hands-on practice
- **ProofWiki**: For alternative proofs

#### **Visual Learning**
- **3Blue1Brown**: "The paradox at the heart of mathematics: Gödel's Incompleteness Theorem" (mentions sets)
- **Numberphile**: "Infinity is bigger than you think"

#### **Practice Platforms**
- **LeetCode**: "Math" problems involving sets
- **Project Euler**: Problems 1-50 use set thinking
- **Brilliant.org**: Set theory course

---

**Next Module**: **Module 1.3: Combinatorics** - Learn to count systematically, essential for probability, algorithm analysis, and optimization. You'll master permutations, combinations, and the binomial theorem.

**Immediate Action**: Complete the Module 1.2 assessment. If you score <85%, revisit weak areas using the Feynman Technique: teach each concept to someone (or a rubber duck) until you can explain it simply.
