## **libarith: Functional Requirements**

### **Core Infrastructure**
*   `BigInt(std::string)` constructor
*   `BigInt(long long)` constructor
*   `std::string to_string()`
*   `std::ostream& operator<<`
*   `bool operator<(const BigInt&)`
*   `bool operator>(const BigInt&)`
*   `bool operator<=(const BigInt&)`
*   `bool operator>=(const BigInt&)`
*   `bool operator==(const BigInt&)`
*   `bool operator!=(const BigInt&)`

### **Arithmetic Operators**
*   `operator+` and `operator+=`
*   `operator-` and `operator-=` (with sign handling)
*   `operator*` and `operator*=`
*   `operator/` and `operator/=`
*   `operator%` and `operator%=`
*   `operator++` and `operator--` (prefix/postfix)

### **Mathematical Utilities**
*   `pow(BigInt, unsigned int)`
*   `modPow(BigInt base, BigInt exp, BigInt mod)`
*   `gcd(BigInt, BigInt)`
*   `factorial(unsigned int)`
*   `abs()`
*   `isEven()` / `isOdd()`
*   `digitSum()`

---

## **Technical Resources to Study**

### **Algorithms**
*   **Knuth's Algorithm D**: The standard for arbitrary-precision division.
*   **Karatsuba Algorithm**: To optimize multiplication beyond $O(n^2)$.
*   **Binary Exponentiation**: Essential for the `pow` and `modPow` functions.
*   **Schönhage–Strassen algorithm**: (Advanced) If you ever want to handle millions of digits using FFT.

### **Implementation References**
*   **GMP (GNU Multiple Precision Arithmetic Library)**: The "gold standard." Don't look at the source code yet (it's dense C), but look at their API documentation for inspiration.
*   **Modern C++ Design**: Specifically, research "Expression Templates." This is a way to make `a + b + c + d` not create three temporary objects, which is a huge performance win for BigInts.

---

## **Development Milestones**

1.  **Phase 1: The "String" Prototype.** Get addition and multiplication working using Base 10. It will be slow, but easy to debug.
2.  **Phase 2: The Base $10^9$ Migration.** Move the internal storage to `std::vector<uint32_t>` using Base $10^9$ to utilize the CPU's 64-bit registers efficiently.
3.  **Phase 3: The "Euler Stress Test".** Use **libarith** to solve Project Euler Problem 16 ($2^{1000}$) and Problem 20 ($100!$). If the answers match, your core logic is solid.
4.  **Phase 4: Optimization.** Implement Karatsuba multiplication for when numbers exceed ~128 limbs.



Since you are aiming for a professional library, are you planning to write unit tests for each operator as you build them?
