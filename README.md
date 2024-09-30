# Defi-Empire: A Simplified DeFi Kingdom Clone

## Overview

This project demonstrates how to build a custom subnet on Avalanche using SubnetEVM. It walks through setting up the local network, deploying contracts, and interacting with them on a custom blockchain. This guide uses tools like the Avalanche CLI, MetaMask, and Remix IDE to streamline the process.

## Getting Started

### Prerequisites

To run this project, you’ll need the following tools:

- **Avalanche CLI**: Install the Avalanche CLI by following the official guide [here](https://docs.avax.network/tooling/cli-guides/install-avalanche-cli). To make the CLI accessible from anywhere, add it to your system path:
  ```bash
  export PATH=~/bin:$PATH
  ```
  - Add this to your `.bashrc` (for bash) or `.zshrc` (for zsh) to make the change permanent.

- **MetaMask**: Install the MetaMask browser extension and create an account.

- **Remix IDE**: Use the Remix IDE available at [remix.ethereum.org](https://remix.ethereum.org) to interact with your contracts.

### Project Workflow

1. **Set Up Avalanche CLI**

   After installing the CLI, run the following command to create a custom subnet:
   ```bash
   avalanche subnet create <your-subnet-name>
   ```
   Provide a unique chain ID and token symbol when prompted. Choose default options for other settings unless you want to customize further.

2. **Deploy Your Subnet Locally**

   Once your subnet is configured, deploy it to your local network:
   ```bash
   avalanche subnet deploy <your-subnet-name>
   ```

   Example output includes important details like RPC URL, funded addresses, and network parameters:
   ```
   RPC URL:           http://127.0.0.1:9650/ext/bc/2Jz8iH5KWAeYeutjeR7e2ymnyhTd8fvUB4bmsJ2PWLHnriQDcD/rpc
   Funded address:    0x8db97C7cEcE249c2b98bDC0226Cc4C2A57BF52FC (1000000 tokens)
   Chain ID:          234
   Currency Symbol:   DIV
   ```

3. **Connect MetaMask to Your Subnet**

   - Use the output from the previous step to add a new custom network in MetaMask.
   - Import the funded address by adding a new account using the provided private key.

4. **Deploy Contracts Using Remix IDE**

   - Copy `ERC20.sol` and `Vault.sol` from this repository.
   - Paste them into Remix IDE.
   - Choose the **Injected Web3** environment and deploy the `ERC20.sol` contract first, followed by `Vault.sol` (using the `ERC20.sol` contract address as a constructor argument).

5. **Mint Tokens and Manage Vault**

   - Mint tokens using the `mint` function in the `ERC20.sol` contract.
   - Deposit tokens into the vault and receive shares in return through `Vault.sol`.

## Example Commands

- **Creating a Subnet**: 
   ```bash
   avalanche subnet create defi-empire
   ```
- **Deploying to Local Network**: 
   ```bash
   avalanche subnet deploy defi-empire
   ```
- **Adding a Custom MetaMask Network**:
   - RPC URL: `http://127.0.0.1:9650/ext/bc/your-custom-url/rpc`
   - Chain ID: `Your Custom Chain ID`
   - Currency Symbol: `Your Token Symbol`

## License

This project is distributed under the MIT License.
