## 2026-10-24 - Replace Vec::new with Vec::with_capacity where size is known
**Learning:** Preallocating vector capacity avoids unnecessary reallocations when pushing elements in a loop with a known length.
**Action:** Always prefer `Vec::with_capacity(len)` over `Vec::new()` when initializing a vector whose required capacity is known in advance from an existing slice, iterator or API response length.
