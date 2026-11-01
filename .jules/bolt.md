
## 2023-11-01 - Zero-Copy Parsing Avoids Unnecessary String Allocations
**Learning:** In document parsing pathways for JSON and XML in Rust, allocating a `String` from `&[u8]` before parsing forces an extra O(N) allocation and an O(N) UTF-8 validation pass.
**Action:** Use native byte-reader interfaces like `serde_json::from_slice` and `quick_xml::Reader::from_reader` to parse directly from the raw byte slice, avoiding allocations entirely.
