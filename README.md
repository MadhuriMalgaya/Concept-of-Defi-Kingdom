# Basic Concept of Defi Kingdom
This guide demonstrates how to set up a custom EVM subnet on Avalanche and deploy two essential smart contracts using the Remix platform. The first contract is an ERC20 token (Defi), providing 
functionalities for minting, burning, transferring, and approving tokens. The second contract is a Vault, enabling users to deposit and withdraw tokens in exchange for shares. These contracts form 
the building blocks for creating your own DeFi platform.

# Description
This code consists of two smart contracts: Defi and Vault, designed to work on the Avalanche EVM subnet and deployed using the Remix platform.

* Defi Contract
1. Type: ERC20-like token
2. Functions: Minting, burning, transferring, and approving tokens.
3. Events: Transfer and Approval.
   
* Vault Contract
1. Type: Token vault for depositing and withdrawing Defi tokens.
2. Functions: Depositing tokens to receive vault shares and withdrawing tokens by burning shares.
3. Interactions: Utilizes the Defi token for deposit and withdrawal operations.

The first contract (Defi) implements an ERC20-like token with functionalities for transferring, approving, minting, and burning tokens. The second contract (Vault) interacts with an ERC20 token by 
allowing users to deposit tokens in exchange for vault shares and withdraw tokens by burning those shares. When integrated, the Vault can be used to manage and interact with the Defi token.

# Installation
# Compatibility
Here, I have use Linux Ubuntu. Windows is currently not supported. you can also use Mac.

# Instructions
* Install the Avalanche CLI tool: To get started, you will need to install the Avalanche Command Line Interface (CLI) tool. This tool is used to interact with the Avalanche network from your terminal.
* To download a binary for the latest release, run on terminal:
  
```
curl -sSfL https://raw.githubusercontent.com/ava-labs/avalanche-cli/main/scripts/install.sh | sh -s
```
* The binary will be installed inside the ~/bin directory.
 To add the binary to your path, run
```
export PATH=~/bin:$PATH
```
* After installing, launch your own custom subnet:
```
avalanche subnet create Defi
✔ Subnet-EVM
Enter your subnet's ChainId. It can be any positive integer.
ChainId:957512 (You can use anything here but in numeric).
Select a symbol for your subnet's native token
Token symbol: RUPE (you can use as you want but in string).
✔ Use latest version
✔ Low disk use    / Low Throughput    1.5 mil gas/s (C-Chain's setting)
✔ Airdrop 1 million tokens to the default address (do not use in production)
✔ No
```
* Now Deploy the subnet
```
avalanche subnet deploy Defi
```
After deploying you will see like this:

```
"It is just for Example, Don't copy this"

Browser Extension connection details (any node URL from above works):
RPC URL:          http://127.0.0.1:9650/ext/bc/SPqou41AALqxDquEycNYuTJmRvZYbfoV9DYApDJVXKXuwVFPz/rpc. (it is just for example).
Funded address:   <Here,funded address with private key which is use for importing your funded address on metamask for tokens>
Network name:     Defi
Chain ID:         957512
Currency Symbol:  RUPE
```
This information is used for connecting your network to Metamask Wallet.

* Shut down your local deployment with:
```
avalanche network stop
```
* Restart your local deployment (from where you left off) with:
```
avalanche network start
```

* Deploy basic building blocks: You can use Solidity and Remix to deploy the basic building blocks of your game, such as smart contracts for battling, exploring, and trading. 

Here I have two codes:
1. Defi.sol
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;

contract Defi {
    uint public totalSupply;
    mapping(address => uint) public balanceOf;
    mapping(address => mapping(address => uint)) public allowance;
    string public name = "Defi";
    string public symbol = "RUPE";
    uint8 public decimals = 0;

		event Transfer(address indexed from, address indexed to, uint value);
    event Approval(address indexed owner, address indexed spender, uint value);

    ------ Rest of your code -----

```
  
2. Vault.sol
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;
interface IERC20 {
    function totalSupply() external view returns (uint);

    function balanceOf(address account) external view returns (uint);

    function transfer(address recipient, uint amount) external returns (bool);

    function allowance(address owner, address spender) external view returns (uint);

    function approve(address spender, uint amount) external returns (bool);

    function transferFrom(
        address sender,
        address recipient,
        uint amount
    ) external returns (bool);

--------Rest of your code------
```


# Authors
Madhuri Malgaya
Gmail: madhumalgaya@gamil.com

# License
This project is licensed under the MIT License - see the LICENSE.md file for details
