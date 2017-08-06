## Chapter 4 - User-defined data types

**Types classification**
- _Enumerated types_, types defined by giving the possible values directly
- _Union types_, Enumerated types that carry additional data witch value
  ```Idris
  data Bool = True | False
  ```
- _Recursive types_, Union types that are defined in terms of themselves
  ```Idris
  data Nat = Z | S Nat
  ```
  - Recursive data types need at least one non-recursive case in order to be useful, so at least one of the constructors needs to have a non-recursive argument. If not, it is not possible to construct an element of that type.
- _Generic types_, Types that are parameterized over some other types
  ```Idris
  data Maybe valtype = Nothing | Just valtype
  ```
- _Dependent types_, Types that are computed from some other value
  ```Idris
  Vect : Nat -> Type -> Type
  ```
  The type of a `Vect` depends on its length. There is no syntatic distinction between types and expressions, types can be computed from _any_ expression.
  
**Dependent types example**

A data type to represent vehicles, but some operations might not make sense on some of the values i.e. Can't refuel a bike!

```Idris
data PowerSource = Petrol | Pedal

data Vehicle : PowerSource -> Type where
     Bicycle : Vehicle Pedal
     Car : (fuel : Nat) -> Vehicle Petrol
     Bus : (fuel : Nat) -> Vehicle Petrol
     
refuel : Vehicle Petrol -> Vehicle Petrol
refuel (Car fuel) = Car 100
refuel (Bus fuel) = Bus 200
refuel Bicycle impossible -- you can actually write this
```

**Defining families of types**

For `Vehicle`, there are two type definitions in one declaration (`Vehicle Pedal` and `Vehicle Petrol`). Dependent data types like `Vehicle` therefore referred as `families` of types, because you're defining multiple related types at the same time. The power source is an index of the `Vehicle` family. The index tells which `Vehicle` type we are referring to.

- A _parameter_ is unchanged across the entire structure. i.e. every element of the vector has the same type
- An _index_ may change across a structure. i.e. every subvector has different length
