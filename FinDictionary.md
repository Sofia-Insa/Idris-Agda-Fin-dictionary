
# Idris-Agda dictionary 
Comparing `Fin` in [Agda standard library](https://github.com/agda/agda-stdlib.git) with `Fin` in [Idris 2](https://github.com/idris-lang/Idris2/tree/main/libs/base)

### datatype Fin 
`Fin n` is a type with n elements, `Fin n` can be seen as natural numbers in the set {m | m < n}.
Same definition of the datatype `Fin` in both languages: 
- type parameter : a natural number is used to parameterize `Fin`
  - In Agda : ℕ
  - In Idris : `(n : Nat)`
- same constructors : a base case and a successor case
  - base case : `zero` in Agda and `FZ` in Idris
  - successor case : `suc` in Agda `FS` in Idris

