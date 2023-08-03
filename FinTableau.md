# Fin 
[Agda](https://github.com/agda/agda-stdlib/blob/master/src/Data/Fin.agda)
[Idirs](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr)

| Agda | Idris |
|----------|:-------------:|
|[`toℕ : Fin n → ℕ`](https://github.com/agda/agda-stdlib/blob/master/src/Data/Fin.agda)|[`finToNat : Fin n -> Nat`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr) |
||[`finToInteger : Fin n -> Integer`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr) |
|[`fromℕ< : m ℕ.< n → Fin n`](https://github.com/agda/agda-stdlib/blob/master/src/Data/Fin.agda)|[`natToFinLT : (x : Nat) -> {0 n : Nat} -> {auto 0 prf : x LT n} -> Fin n`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr) |
||[`natToFinLt : (x : Nat) -> {0 n : Nat} ->{auto 0 prf : So (x < n)} -> Fin n`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr) |
||[`natToFin : Nat -> (n : Nat) -> Maybe (Fin n)`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr) |
|[`inject₁ : Fin n → Fin (suc n) `](https://github.com/agda/agda-stdlib/blob/master/src/Data/Fin.agda)|[`weaken : Fin n -> Fin (S n)`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr)|
|[`_↑ʳ_ : ∀ {m} n → Fin m → Fin (n ℕ.+ m)`](https://github.com/agda/agda-stdlib/blob/master/src/Data/Fin.agda)|[`weakenN : (0 n : Nat) -> Fin m -> Fin (m + n)`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr)|
|[`_inject≤ : Fin m → m ℕ.≤ n → Fin n`](https://github.com/agda/agda-stdlib/blob/master/src/Data/Fin.agda)|[`weakenLTE : Fin n -> LTE n m -> Fin m`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr)|



Only in Idris
| Agda | Idris |
|----------|:-------------:|
||[`natToFin : Nat -> (n : Nat) -> Maybe (Fin n)`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr)|
||[`finFromInteger`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr)|
||[`fromInteger : (x : Integer) -> {auto 0 prf : So (integerLessThanNat x n)} -> Fin n`]( https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr)|
||[`integerLessThanNat : Integer -> Nat -> Bool`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr)|
||[`restrict : (n : Nat) -> Integer -> Fin (S n)`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr)|
||[`shift : (m : Nat) -> Fin n -> Fin (m + n)`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Fin.idr)|

