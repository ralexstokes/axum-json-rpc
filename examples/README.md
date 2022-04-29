# Running
`cargo run --example simple` 
```sh
curl 'http://127.0.0.1:8080/' -POST -d '{"jsonrpc": "2.0", "method": "div", "params": [7,0], "id": 1}' -H 'Content-Type: application/json'
```