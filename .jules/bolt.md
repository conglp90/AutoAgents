
## 2024-05-18 - Avoid Memory Leaks in Trait Implementations
**Learning:** Found a critical anti-pattern where `Box::leak(String::into_boxed_str())` was used inside getter methods (`name` and `description`) of the `ToolT` trait implementation for `McpToolAdapter` in `crates/autoagents-toolkit/src/mcp/adapter.rs`. Because these methods return `&str` with an elided lifetime tied to `&self`, simply returning a reference to the struct fields `&self.name` and `&self.description` is perfectly valid and avoids massive heap allocations and intentional memory leaks on every call.
**Action:** When returning a `&str` bounded by `&self` from a getter method, always return a direct reference to the string field instead of converting it to a static lifetime and leaking it.
