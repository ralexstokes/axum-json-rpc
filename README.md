# Json RPC extractor for axum

`JsonRpcExtractor` parses JSON-RPC requests and validates it's correctness.

```rust
use axum_jrpc::{JsonRpcResult, JsonRpcExtractor, JsonRpcResponse};

fn router(req: JsonRpcExtractor) -> JsonRpcResult {
    let req_id = req.get_request_id()?;
    let method = req.method();
    let response =
        match method {
            "add" => {
                let params: [i32; 2] = req.parse_params()?;
                JsonRpcResponse::success(req_id, params[0] + params[1]);
            }
            m => req.method_not_found(m)
        };

    Ok(response)
}
```

[![Crates.io](https://img.shields.io/crates/v/axum-json-rpc)](https://crates.io/crates/axum-json-rpc)
[![Documentation](https://docs.rs/axum-json-rpc/badge.svg)](https://docs.rs/axum-json-rpc)