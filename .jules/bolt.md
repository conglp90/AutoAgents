
## 2025-05-15 - Unnecessary clones of large allocations to async functions
**Learning:** We often defensively clone collections (like `Vec<String>`) when passing them to async functions. However, if the source variable isn't used later—or if we can consume it via `into_iter` rather than iterating and cloning individual elements—we can prevent allocating and copying large chunks of memory (especially text allocations).
**Action:** When working with async boundaries and loops, check if large allocations passed as parameters really need `.clone()`. If a function consumes a vector, see if we can use the consumed vector's elements via iterators instead of re-cloning them individually when constructing new structs.
