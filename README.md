# Edexa ENS (EDNS)

## Overview

**Edexa ENS** is a set of smart contracts designed to interact with the Edexa Name Service (EDNS), forked from Ethereum ENS  which facilitates domain registration, management, and resolution. These contracts help manage the registration and resolution of domains on the Ethereum network, using a variety of functionalities to ensure seamless operation and security. This repository includes contracts for domain registration, reverse resolution, and handling EDNS-related processes.


## Features

- **Registrar Contracts**: Handles the process of registering and renewing ENS domains.
- **Reverse Resolution**: Enables reverse resolution using the `.addr.reverse` special-purpose TLD.
- **Commit/Reveal Process**: Avoids frontrunning during domain registration through a commit/reveal process.
- **Price Oracles**: Implements price oracles for domain registration and renewal.
- **Public Resolver**: A resolver supporting various ENS profiles such as ABI, address, content hash, text records, etc.

## Contracts

### EDNS Registry
- **ENSRegistry**: The core contract of the ENS system, responsible for looking up domain information, including owners and resolvers.
- **ENSRegistryWithFallback**: A new version of the ENS Registry after the 2020 ENS Registry Migration.

### Registrar Contracts
- **FIFSRegistrar**: A simple first-in-first-served registrar that issues domains to the first account that requests them.
- **EthRegistrar**: The ENS registrar implementation for the `.edx` TLD.
- **BaseRegistrar**: Manages the TLD in the ENS registry, providing the base functionality for domain registration and renewal.
- **EdxRegistrarController**: Implements the registrar control logic for `.edx` domains, including the commit/reveal process.
- **TestRegistrar**: A test registrar deployed on Ropsten for testing purposes, allowing users to claim domains for test purposes.

### Resolvers
- **PublicResolver**: The general-purpose ENS resolver that supports multiple EIPs and allows modification of ENS records.
    - **ABIResolver** (EIP 205): Supports ABI (Application Binary Interface) records.
    - **AddrResolver** (EIP 137): Resolves contract addresses and supports multi-coin address resolution.
    - **ContentHashResolver** (EIP 1577): Supports content hash resolution.
    - **TextResolver** (EIP 634): Allows text records to be stored and resolved.
    - **NameResolver** (EIP 181): Manages reverse resolution of Ethereum addresses to ENS names.

# Developer Guide



## How to Set Up

1. Clone the repository:
   ```bash
   git clone https://github.com/ensdomains/ens-contracts

    Navigate to the project directory:

cd ens-contracts

Install dependencies:

    bun i

How to Run Tests

To run the tests, use the following command:

    bun run test

How to Publish

To publish, run:

    bun run pub

## Deployment

To deploy, use the following command:

    NODE_OPTIONS='--experimental-loader ts-node/esm/transpile-only' bun run hardhat --network <network_name> deploy



