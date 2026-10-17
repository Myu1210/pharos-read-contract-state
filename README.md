Pharos Read Contract State — Sample Output
Method label: Direct JSON-RPC via curl (NOT Chain MCP). This sample was produced by sending raw eth_call / eth_blockNumber / eth_chainId JSON-RPC requests to the Pharos Atlantic Testnet RPC endpoint. No MCP server was registered or used in this session.

Target
Field	Value
Network	Pharos Atlantic Testnet
Chain ID	688689 (0xa8231)
RPC URL	https://atlantic.dplabs-internal.com
Contract	USDC 0xcfC8330f4BCAB529c625D12781b1C19466A9Fc8B
Reference block	31529560 (0x1e11a58)
Explorer	https://atlantic.pharosscan.xyz/address/0xcfC8330f4BCAB529c625D12781b1C19466A9Fc8B
Chain & Block Verification
eth_chainId
curl -s -X POST -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","method":"eth_chainId","params":[],"id":1}' \
  https://atlantic.dplabs-internal.com
Response:

{"jsonrpc":"2.0","id":1,"result":"0xa8231"}
Decoded: 0xa8231 = 688689 ✅ matches Atlantic Testnet.

eth_blockNumber
curl -s -X POST -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":2}' \
  https://atlantic.dplabs-internal.com
Response:

{"result":"0x1e11a58","id":2,"jsonrpc":"2.0"}
Decoded: 0x1e11a58 = 31,529,560.

Contract Reads (ERC-20 public values)
All four calls use eth_call with "latest" block tag against to: 0xcfC8330f4BCAB529c625D12781b1C19466A9Fc8B.

1. name() — selector 0x06fdde03
curl -s -X POST -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","method":"eth_call","params":[{"to":"0xcfC8330f4BCAB529c625D12781b1C19466A9Fc8B","data":"0x06fdde03"},"latest"],"id":3}' \
  https://atlantic.dplabs-internal.com
Raw result:

0x0000000000000000000000000000000000000000000000000000000000000020
0000000000000000000000000000000000000000000000000000000000000004
5553444300000000000000000000000000000000000000000000000000000000
Decoded (ABI: string): offset = 0x20, length = 4, bytes = 55 53 44 43 → USDC.

2. symbol() — selector 0x95d89b41
curl -s -X POST -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","method":"eth_call","params":[{"to":"0xcfC8330f4BCAB529c625D12781b1C19466A9Fc8B","data":"0x95d89b41"},"latest"],"id":4}' \
  https://atlantic.dplabs-internal.com
Raw result:

0x0000000000000000000000000000000000000000000000000000000000000020
0000000000000000000000000000000000000000000000000000000000000004
5553444300000000000000000000000000000000000000000000000000000000
Decoded (ABI: string): → USDC.

3. decimals() — selector 0x313ce567
curl -s -X POST -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","method":"eth_call","params":[{"to":"0xcfC8330f4BCAB529c625D12781b1C19466A9Fc8B","data":"0x313ce567"},"latest"],"id":5}' \
  https://atlantic.dplabs-internal.com
Raw result:

0x0000000000000000000000000000000000000000000000000000000000000006
Decoded (ABI: uint8): → 6.

4. totalSupply() — selector 0x18160ddd
curl -s -X POST -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","method":"eth_call","params":[{"to":"0xcfC8330f4BCAB529c625D12781b1C19466A9Fc8B","data":"0x18160ddd"},"latest"],"id":6}' \
  https://atlantic.dplabs-internal.com
Raw result:

0x00000000000000000000000000000000000000000000000000005b0c40615d25
Decoded (ABI: uint256):

Raw integer: 0x5b0c40615d25 = 100,108,177,857,829
Human-readable (÷ 10⁶, since decimals = 6): 100,108,177.857829 USDC
Summary Table
#	Function	Selector	Raw hex	Decoded value
1	name()	0x06fdde03	0x20…55534443…	USDC
2	symbol()	0x95d89b41	0x20…55534443…	USDC
3	decimals()	0x313ce567	0x06	6
4	totalSupply()	0x18160ddd	0x5b0c40615d25	100,108,177,857,829 raw → 100,108,177.857829 USDC
Block number: 31,529,560 (0x1e11a58) Chain ID: 688689 (0xa8231) — Atlantic Testnet ✅

Method Disclosure
Transport: HTTPS POST, JSON-RPC 2.0.
Tool: curl issuing raw eth_call, eth_blockNumber, eth_chainId requests.
NOT Chain MCP: No MCP server was registered in this session (MCP tools: 0). The mcp:chain:* tool surface was unavailable, so this sample was produced entirely via direct JSON-RPC against the public Atlantic Testnet RPC endpoint.
No private keys, no write operations. All calls are read-only and stateless; they do not mutate chain state and require no authentication.
Reproducing Locally
RPC="https://atlantic.dplabs-internal.com"
USDC="0xcfC8330f4BCAB529c625D12781b1C19466A9Fc8B"

