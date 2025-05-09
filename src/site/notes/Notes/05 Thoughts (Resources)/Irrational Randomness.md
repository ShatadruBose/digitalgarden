---
{"dg-publish":true,"dg-home":null,"tags":["thoughts"],"aliases":null,"permalink":"/notes/05-thoughts-resources/irrational-randomness/","dgPassFrontmatter":true,"updated":"2025-05-09T10:46:00.301+05:30"}
---

# **Irrational Randomness: A Hybrid Stochastic-Analytical Decision System**

**Author**: Shatadru Bose  
**Date**: May 2025

---

## **Abstract**

_Irrational Randomness_ is a novel stochastic decision-making system that builds upon the foundation of _Ultra Randomness_ by incorporating irrational constants such as π (pi) and _e_ (Euler’s number) to model unpredictability and complexity in multi-element evaluations. This system introduces an alternating irrational-weighted scoring technique that breaks symmetry and injects controlled chaos into selection processes. The method offers a unique lens through which to understand randomness as both structured and irrational.

---

## **1. Introduction**

Randomness, especially in the context of decision-making and simulations, often leans toward pseudo-random number generation. However, natural systems and human cognition experience randomness in more nuanced forms. The _Ultra Randomness_ model already introduced a deterministic chaos-based measure, optimizing selections by combining spread and centrality.

_Irrational Randomness_ extends this idea into a new domain by leveraging transcendental numbers to distort outcome probabilities in a mathematically rich yet intuitive way.

---

## **2. Preliminaries**

### 2.1 Ultra Randomness (Base Layer)

Let each element EiE_iEi​ be assigned a continuous range [Li,Ui]⊂[0,1][L_i, U_i] \subset [0,1][Li​,Ui​]⊂[0,1].

From this:

- Two random values r1,r2∈[Li,Ui]r_1, r_2 \in [L_i, U_i]r1​,r2​∈[Li​,Ui​] are selected.
    
- The **spread** Δi=∣r1−r2∣\Delta_i = |r_1 - r_2|Δi​=∣r1​−r2​∣
    
- The **center** ci=r1+r22c_i = \frac{r_1 + r_2}{2}ci​=2r1​+r2​​
    
- The **w-score**:
    
    wi=ciΔiw_i = \frac{c_i}{\Delta_i}wi​=Δi​ci​​

The element with the maximum wiw_iwi​ is selected as the base winner under Ultra Randomness.

---

## **3. Irrational Randomness Algorithm**

### 3.1 Concept

To inject irrational complexity, each wiw_iwi​ is transformed using a predefined irrational multiplier. This mimics how real-world randomness often follows chaotic, non-repeating behaviors.

### 3.2 Rules

- If **only two** elements:
    
    - Larger www → multiplied by π\piπ
        
    - Smaller www → multiplied by eee
        
- If **more than two** elements:
    
    - Multiplier alternates:
        
        w1⋅π,w2⋅e,w3⋅π,w4⋅e,…w_1 \cdot \pi,\quad w_2 \cdot e,\quad w_3 \cdot \pi,\quad w_4 \cdot e,\quad \ldotsw1​⋅π,w2​⋅e,w3​⋅π,w4​⋅e,…

Let the new score be called WiW_iWi​:

Wi={wi⋅πif i≡1(mod2)wi⋅eif i≡0(mod2)W_i = \begin{cases} w_i \cdot \pi & \text{if } i \equiv 1 \pmod{2} \\ w_i \cdot e & \text{if } i \equiv 0 \pmod{2} \end{cases}Wi​={wi​⋅πwi​⋅e​if i≡1(mod2)if i≡0(mod2)​

### 3.3 Selection

The element EkE_kEk​ with the **maximum WkW_kWk​** is declared the winner under Irrational Randomness.

---

## **4. Example Calculation**

Suppose we have 3 elements:

- E1E_1E1​: r1=0.3,r2=0.6r_1 = 0.3, r_2 = 0.6r1​=0.3,r2​=0.6 → w1=0.450.3=1.5w_1 = \frac{0.45}{0.3} = 1.5w1​=0.30.45​=1.5
    
- E2E_2E2​: r1=0.4,r2=0.7r_1 = 0.4, r_2 = 0.7r1​=0.4,r2​=0.7 → w2=0.550.3=1.83w_2 = \frac{0.55}{0.3} = 1.83w2​=0.30.55​=1.83
    
- E3E_3E3​: r1=0.2,r2=0.8r_1 = 0.2, r_2 = 0.8r1​=0.2,r2​=0.8 → w3=0.50.6=0.83w_3 = \frac{0.5}{0.6} = 0.83w3​=0.60.5​=0.83
    

Now apply irrational multipliers:

- W1=1.5⋅π=4.712W_1 = 1.5 \cdot \pi = 4.712W1​=1.5⋅π=4.712
    
- W2=1.83⋅e=4.972W_2 = 1.83 \cdot e = 4.972W2​=1.83⋅e=4.972
    
- W3=0.83⋅π=2.609W_3 = 0.83 \cdot \pi = 2.609W3​=0.83⋅π=2.609
    

**Winner**: E2E_2E2​, as W2=4.972W_2 = 4.972W2​=4.972 is the highest.

---

## **5. Applications**

- **Decision Theory**: Adds stochastic "flavor" to deterministic models.
    
- **Game Design**: Enhances unpredictability while maintaining fairness.
    
- **AI Randomization**: Simulates human-like irrational decisions.
    
- **Physics Simulations**: Mimics chaos and symmetry-breaking in system selection.
    

---

## **6. Discussion**

The usage of π and _e_, both irrational and non-repeating, creates a bridge between structured randomness and pure unpredictability. The alternating multiplier system mirrors the Fibonacci-like unpredictability found in natural systems.

One key advantage of Irrational Randomness is its balance of **rigid structure** (Ultra Randomness) and **irrational noise** (π, _e_), providing outcomes that are neither purely chance-driven nor fully predictable.

---

## **7. Conclusion**

_Irrational Randomness_ reframes the role of chaos in computation. By combining deterministic variance with irrational distortion, it offers a compelling framework for simulating complex systems. Whether used in simulations, games, or even creative decision-making tools, this approach offers both depth and unpredictability—a true homage to the beautifully chaotic nature of real-world randomness.

---

## **8. Future Work**

Potential extensions include:

- Introducing additional irrational constants (like φ – the golden ratio).
    
- Embedding the system into AI agents for strategic random behavior.
    
- Exploring entropy-based performance metrics.