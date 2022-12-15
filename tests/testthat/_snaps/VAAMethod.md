# Function returns correct values

    Code
      set.seed(1234567)
      VAAMethod(fuzzyValuesA)
    Output
                 [,1]      [,2]     [,3]     [,4]
      [1,]  0.2616731 0.4941634 1.005837 1.238327
      [2,] -0.7226055 0.9613027 1.505364 2.389272
      [3,]  0.4589197 1.3705401 1.429460 2.791080
      [4,] -1.0000000 0.0000000 0.000000 2.000000

---

    Code
      set.seed(1234567)
      VAAMethod(fuzzyValuesA, b = 5)
    Output
                  [,1]      [,2]     [,3]     [,4]
      [1,]  0.07003599 0.5899820 0.910018 1.429964
      [2,] -1.16650312 1.1832516 1.283415 2.833170
      [3,]  0.97529724 1.1123514 1.687649 2.274703
      [4,] -1.00000000 0.0000000 0.000000 2.000000
      [5,] -0.70384987 0.9519249 1.514742 2.370517

---

    Code
      set.seed(1234567)
      VAAMethod(fuzzyValuesIncA, increases = TRUE)
    Output
                [,1]      [,2]     [,3]      [,4]
      [1,] 0.2324903 0.4941634 1.005837 0.2324903
      [2,] 1.6839082 0.9613027 1.505364 0.8839082
      [3,] 0.9116204 1.3705401 1.429460 1.3616204
      [4,] 1.0000000 0.0000000 0.000000 2.0000000

---

    Code
      set.seed(1234567)
      VAAMethod(fuzzyValuesIncA, b = 5, increases = TRUE)
    Output
                [,1]      [,2]     [,3]      [,4]
      [1,] 0.5199460 0.5899820 0.910018 0.5199460
      [2,] 2.3497547 1.1832516 1.283415 1.5497547
      [3,] 0.1370541 1.1123514 1.687649 0.5870541
      [4,] 1.0000000 0.0000000 0.000000 2.0000000
      [5,] 1.6557748 0.9519249 1.514742 0.8557748
