# **Phase 1: Core Discrete Mathematics**
*Duration: 3-6 months*

## **Module 1.1: Logic & Proofs**
*Duration: 3-4 weeks*

### **Week 1-2: Propositional Logic & Foundations**

#### **1.1.1 Basic Logical Concepts**
- **Propositions & Truth Values**: Statements that can be true or false
  - *Examples*: "2+2=4", "It is raining", "This algorithm runs in O(n²)"
  - *CS Connection*: Boolean variables in programming
  - *Practice*: Identify which sentences are propositions
- **Logical Connectives**:
  - **Negation (¬, ~)**: NOT operator
  - **Conjunction (∧)**: AND operator
  - **Disjunction (∨)**: OR operator (inclusive)
  - **Exclusive OR (⊕)**: XOR operator
  - *CS Connection*: Boolean operators in conditionals

#### **1.1.2 Truth Tables & Logical Equivalence**
- **Constructing Truth Tables**:
  - For simple and compound propositions
  - *Example*: Build truth table for (p ∧ q) → r
  - *CS Connection*: Testing all inputs for a Boolean function
- **Logical Equivalences**:
  - **Identity Laws**: p ∧ T ≡ p, p ∨ F ≡ p
  - **Domination Laws**: p ∨ T ≡ T, p ∧ F ≡ F
  - **Idempotent Laws**: p ∨ p ≡ p, p ∧ p ≡ p
  - **Double Negation**: ¬(¬p) ≡ p
  - **De Morgan's Laws**: ¬(p ∧ q) ≡ ¬p ∨ ¬q, ¬(p ∨ q) ≡ ¬p ∧ ¬q
  - *CS Connection*: Circuit simplification, query optimization
  - *Practice*: Simplify logical expressions using equivalences

#### **1.1.3 Conditional Statements**
- **Implication (→)**: p → q (if p then q)
  - Truth table: False only when p is true and q is false
  - *Common Pitfall*: Confusing with "if and only if"
- **Converse, Inverse, Contrapositive**:
  - Original: p → q
  - Converse: q → p
  - Inverse: ¬p → ¬q
  - Contrapositive: ¬q → ¬p
  - *Important Fact*: A statement is logically equivalent to its contrapositive
  - *CS Connection*: Precondition/postcondition in function design

### **Week 2-3: Predicate Logic & Quantifiers**

#### **1.2.1 Predicates and Quantifiers**
- **Predicates**: Statements with variables
  - *Example*: P(x): "x is prime"
  - *CS Connection*: Functions returning boolean values
- **Universal Quantifier (∀)**: "For all"
  - *Example*: ∀x ∈ ℤ, x² ≥ 0
  - *CS Connection*: Loop invariants, array processing
- **Existential Quantifier (∃)**: "There exists"
  - *Example*: ∃x ∈ ℤ, x² = 4
  - *CS Connection*: Search algorithms, database queries
- **Nested Quantifiers**:
  - *Example*: ∀x∃y, x + y = 0
  - *Translation Practice*: Convert between English and logic
  - *CS Connection*: Nested loops verification

#### **1.2.2 Rules of Inference**
- **Modus Ponens**: p → q, p, ∴ q
- **Modus Tollens**: p → q, ¬q, ∴ ¬p
- **Hypothetical Syllogism**: p → q, q → r, ∴ p → r
- **Disjunctive Syllogism**: p ∨ q, ¬p, ∴ q
- **Addition**: p, ∴ p ∨ q
- *CS Connection*: Automated theorem proving, program verification

### **Week 3-4: Proof Techniques & Applications**

#### **1.3.1 Direct Proofs**
- **Structure**: Assume hypothesis, use definitions and theorems, conclude
- *Example*: Prove "If n is even, then n² is even"
- *CS Connection*: Proving algorithm properties

#### **1.3.2 Proof by Contraposition**
- **Strategy**: Prove ¬q → ¬p instead of p → q
- *Example*: Prove "If n² is odd, then n is odd"
- *CS Connection*: Error case analysis

#### **1.3.3 Proof by Contradiction**
- **Strategy**: Assume negation of conclusion, derive contradiction
- *Example*: Prove "√2 is irrational"
- *CS Connection*: Proving impossibility (e.g., halting problem)

#### **1.3.4 Mathematical Induction**
- **Principle**:
  1. **Base Case**: Prove P(1) is true
  2. **Inductive Hypothesis**: Assume P(k) is true
  3. **Inductive Step**: Prove P(k) → P(k+1)
- **Strong Induction**: Assume P(1), P(2), ..., P(k) to prove P(k+1)
- *CS Connection*: Proving loop correctness, recursive algorithms
- *Examples*:
  - Prove sum of first n integers: 1 + 2 + ... + n = n(n+1)/2
  - Prove binary tree with n nodes has n+1 null pointers

#### **1.3.5 Constructive vs Non-constructive Proofs**
- **Constructive**: Shows how to find/exhibit the object
- **Non-constructive**: Proves existence without showing how to find
- *CS Connection*: Algorithms (constructive) vs existence proofs

### **Practice Problems with CS Applications**

#### **Level 1: Basic Logical Manipulation**
1. Write truth table for: (p → q) ∧ (q → p)
2. Negate: "∀x∃y, P(x,y)"
3. Prove De Morgan's Law using truth tables

#### **Level 2: Intermediate Proofs**
1. Prove: "If n² is divisible by 3, then n is divisible by 3"
2. Prove by induction: 2ⁿ > n² for n ≥ 5
3. Write the contrapositive of: "If the program compiles, then there are no syntax errors"

#### **Level 3: CS Applications**
1. **Algorithm Verification**: 
   ```
   function findMax(array):
       max = array[0]
       for i from 1 to n-1:
           if array[i] > max:
               max = array[i]
       return max
   ```
   Prove using loop invariant that this returns the maximum element.

2. **Recursive Algorithm Proof**:
   Prove that merge sort correctly sorts arrays of size n using induction.

3. **Hardware Design**:
   Simplify the circuit: (A ∧ B) ∨ (A ∧ ¬B) ∨ (¬A ∧ B)

4. **Database Query Logic**:
   Translate to predicate logic: "All computer science students who have taken Discrete Math have a GPA above 3.0"

### **CS-Specific Applications Deep Dive**

#### **1. Program Correctness**
- **Preconditions**: Assumptions before execution
- **Postconditions**: Guarantees after execution
- **Loop Invariants**: Properties that hold before each iteration
  - *Example*: Binary search invariant
  - *Practice*: Identify and prove loop invariants for simple algorithms

#### **2. Digital Circuit Design**
- **Boolean Algebra**: Algebraic manipulation of logic circuits
- **Karnaugh Maps**: Visual method for simplifying Boolean expressions
- *Project*: Design a 4-bit adder circuit

#### **3. Database Query Languages**
- **Relational Calculus**: Foundation for SQL
- **Quantifiers in Queries**:
  - ∀ corresponds to "ALL" in SQL
  - ∃ corresponds to "EXISTS" in SQL
- *Practice*: Translate between predicate logic and SQL

#### **4. AI & Knowledge Representation**
- **Propositional Knowledge Bases**
- **Inference Rules**: Forward/backward chaining
- *Example*: Represent "If it rains, the grass is wet" and perform inference

### **Common Pitfalls & Debugging Logical Thinking**

#### **Pitfall 1: Confusing → with ↔**
- **Debug**: Always check if you mean "if-then" or "if and only if"

#### **Pitfall 2: Misplacing Negations with Quantifiers**
- **Rule**: ¬∀x P(x) ≡ ∃x ¬P(x)
- **Rule**: ¬∃x P(x) ≡ ∀x ¬P(x)

#### **Pitfall 3: Proving the Converse Instead**
- **Debug**: Explicitly state what you're proving vs what you're assuming

#### **Pitfall 4: Induction Step Errors**
- **Debug**: Ensure you're using P(k) to prove P(k+1), not assuming P(k+1)

### **Assessment for Module 1.1**

#### **Conceptual Understanding (Written)**
1. Explain the difference between ∀ and ∃ with CS examples
2. Describe when to use contrapositive vs contradiction proof
3. Explain why mathematical induction is valid

#### **Problem-Solving Test**
**Section A: Logic**
1. Simplify: ¬(p → q) ∨ (p ∧ q)
2. Negate: "Every program that halts produces correct output"

**Section B: Proofs**
1. Prove by induction: 3 divides n³ - n for all n ≥ 0
2. Prove: If a graph has n nodes and n-1 edges, it is a tree or disconnected

**Section C: CS Applications**
1. Write loop invariant for linear search
2. Design a circuit that outputs 1 when exactly two of three inputs are 1

#### **Practical Implementation Project**
**Option 1: Truth Table Generator**
- Input: Logical expression with variables
- Output: Truth table with all combinations
- Bonus: Simplify expression using logical equivalences

**Option 2: Proof Checker (Simple)**
- Input: Proof steps in a restricted format
- Output: Validity of proof
- Supports: Modus Ponens, Modus Tollens, hypothetical syllogism

**Option 3: Digital Circuit Simulator**
- Build AND, OR, NOT gates
- Combine to make half-adder
- Visualize truth tables

### **Transition Checklist to Module 1.2**
Before moving to Set Theory, ensure you can:
- ✅ Translate between English and logical notation fluently
- ✅ Construct truth tables for complex expressions
- ✅ Prove simple statements using at least 3 different methods
- ✅ Apply induction to prove properties of algorithms
- ✅ Identify logical errors in arguments

### **Resources for Module 1.1**

#### **Primary Textbook**
- "Discrete Mathematics and Its Applications" by Kenneth Rosen (Chapters 1-2)

#### **Interactive Learning**
- **Logic Games**: 
  - "Keep Talking and Nobody Explodes" (defusing bombs with logic)
  - "The Witness" (environmental logic puzzles)
- **Online Tools**:
  - Truth Table Generator: https://web.stanford.edu/class/cs103/tools/truth-table-tool/
  - Logic Calculator: https://www.erpelstolz.at/logik/rechner.html

#### **Practice Platforms**
- **Project Euler** (Problems 1-15): Mathematical thinking
- **LeetCode** "Math" category: Algorithmic logic
- **Brilliant.org**: Interactive logic courses

#### **Visual Learning**
- **3Blue1Brown**: "Lockdown Math" series
- **MIT OCW 6.042J**: Mathematics for Computer Science

### **Common CS Interview Questions Covered**
- "Prove that √2 is irrational"
- "Prove by induction that a binary tree of height h has at most 2ʰ nodes"
- "What is the contrapositive of this statement about algorithms?"
- "Design a circuit to add two binary numbers"

### **Mindset Development**
- **Think Like a Computer**: Logic is the CPU's native language
- **Embrace Formalization**: The discomfort of precision leads to clarity
- **Proof as Debugging**: Finding errors in arguments trains debugging skills
- **Abstraction Practice**: Moving from concrete to general prepares for algorithm design

---

**Next Module Preview**: Module 1.2: **Set Theory** will build on logic to formalize collections of objects, which directly models data structures, databases, and type systems. You'll learn to prove set identities, work with functions formally, and understand cardinality—key for analyzing algorithm efficiency.

**Immediate Next Step**: Complete the Module 1.1 assessment with ≥85% accuracy before proceeding. If struggling with any concept, revisit with the Feynman Technique: teach the concept to an imaginary student until you can explain it simply.
