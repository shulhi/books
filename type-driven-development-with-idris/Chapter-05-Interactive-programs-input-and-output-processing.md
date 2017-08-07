## Chapter 5 - Interactive programs: input and output processing

```idris
zip : Vect n a -> Vect n b -> Vect n (a, b)
```

The type expresses the following:
- _Assumptions_ - both input vectors have the same length, _n_
- _Guarantee_ - output vector will have the same length as the input vector
- _Guarantee_ - output vector will consist of pairs of the element type of the first and second inputs

Idris checks the arguments satisfy the assumption and the definition of the function satisfies the guarantee


