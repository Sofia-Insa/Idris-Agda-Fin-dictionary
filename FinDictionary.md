
# Idris-Agda dictionary 
Comparing `Fin` in [Agda standard library](https://github.com/agda/agda-stdlib.git) with `Fin` in [Idris 2](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr)

### datatype Fin 
`Fin n` is a type with n elements, `Fin n` can be seen as natural numbers in the set {m | m < n}.
Same definition of the datatype `Fin` in both languages: 
- type parameter : a natural number is used to parameterize `Fin`
  - In Agda : ℕ
  - In Idris : `(n : Nat)`
- same constructors : a base case and a successor case
  - base case : `zero` in Agda and `FZ` in Idris
  - successor case : `suc` in Agda `FS` in Idris

### Conversion from Fin 
- A conversion from `Fin n` to the natural number n
  - In Agda : `toℕ : Fin n → ℕ`
  - In Idris : `finToNat : Fin n -> Nat`
    this function `finToNat` is injective, as shown in proof `finToNatInjective`
- A conversion from `Fin n` to the integer n
  - In Idris only : `finToInteger : Fin n -> Integer`

### Conversion to Fin 
Conversion of a natural number x to the corresponding element of Fin n
- using a proof that x < n 
  - In Agda : [`fromℕ< : m ℕ.< n → Fin n`](https://github.com/agda/agda-stdlib/blob/master/src/Data/Fin/Base.agda) and `fromℕ<″ : ∀ m {n} → m ℕ.<″ n → Fin n`
    `ℕ.< ` and `ℕ.<″` are defined in [Data.Nat.Base](https://github.com/agda/agda-stdlib/blob/master/src/Data/Nat/Base.agda)
  - In Idris : `natToFinLT : (x : Nat) -> {0 n : Nat} -> {auto 0 prf : x LT n} -> Fin n`
    a variant with a diffent proof also exists `natToFinLt : (x : Nat) -> {0 n : Nat} ->{auto 0 prf : So (x < n)} -> Fin n`
- without a proof 
  - In Idris : `natToFin : Nat -> (n : Nat) -> Maybe (Fin n)`  returns an element of `Fin n` only if the first argument is lower than n.
- Conversion from an Integer, only exist in Idris 
  - `integerToFin : Integer -> (n : Nat) -> Maybe (Fin n)` same as `natToFin` but takes an Integer
  -  `finFromInteger` same as `natToFinLt` but takes `(x : Integer)` instead of `(x : Nat)`
  -   `fromInteger : (x : Integer) -> {auto 0 prf : So (integerLessThanNat x n)} -> Fin n` uses a proof `integerLessThanNat : Integer -> Nat -> Bool` that cheks if `x < n` without slowing down typechecking.

### Injections 
- Weaken the bound on a Fin by 1. Transform an element of `Fin n` to one of `Fin n+1`
  - In Agda : `inject₁ : Fin n → Fin (suc n) `
  - In Idris : `weaken : Fin n -> Fin (S n)`
- Weaken the bound on a Fin by some amount
  - In Agda : `_↑ʳ_ : ∀ {m} n → Fin m → Fin (n ℕ.+ m)`
  - In Idris :  `weakenN : (0 n : Nat) -> Fin m -> Fin (m + n)`
- Weaken the bound on a Fin using a constructive comparison
  - In Agda :  `inject≤ : Fin m → m ℕ.≤ n → Fin n`
  - In Idris : `weakenLTE : Fin n -> LTE n m -> Fin m`
- Left and right injections only in Agda
  - left Agda :  `_↑ˡ_ : ∀ {m} → Fin m → ∀ n → Fin (m ℕ.+ n)`
  - right Agda : `_↑ʳ_ : ∀ {m} n → Fin m → Fin (n ℕ.+ m)` 

### Reduction 
- Tighten the bound on a Fin. Agda ask for `n ≢ toℕ i` while Idris attempt to return the tighten bound if there is one, otherwise it returns nothing.  
  - In Agda : `lower₁ : ∀ (i : Fin (suc n)) → n ≢ toℕ i → Fin n`
  - In Agda : `strengthen : ∀ (i : Fin n) → Fin′ (suc i)` returns a Set Fin and not an element of Fin n
  - In Idris : `strengthen : {n : _} -> Fin (S n) -> Maybe (Fin n)`
    


