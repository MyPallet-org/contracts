# Getting Started

Smart contracts for ERC-4337 account and paymaster implementations.

## Table of contents

- [Repository structure](#repository-structure)
  - [Git Clone](#git-clone)
  - [Sensible Defaults](#sensible-defaults)
  - [VSCode Integration](#vscode-integration)
  - [GitHub Actions](#github-actions)
- [Usage](#usage)
  - [Pre Requisites](#pre-requisites)
  - [Compile](#compile)
  - [TypeChain](#typechain)
  - [Test](#test)
  - [Lint Solidity](#lint-solidity)
  - [Lint TypeScript](#lint-typescript)
  - [Coverage](#coverage)
  - [Report Gas](#report-gas)
  - [Clean](#clean)
  - [Deploy](#deploy)
- [License](#license)
- [Contact](#contact)

# Repository structure

This repository builds upon the following frameworks and libraries:

- [Hardhat](https://github.com/nomiclabs/hardhat): compile, run and test smart contracts
- [TypeChain](https://github.com/ethereum-ts/TypeChain): generate TypeScript bindings for smart contracts
- [Ethers](https://github.com/ethers-io/ethers.js/): renowned Ethereum library and wallet implementation
- [Solhint](https://github.com/protofire/solhint): code linter
- [Solcover](https://github.com/sc-forks/solidity-coverage): code coverage
- [Prettier Plugin Solidity](https://github.com/prettier-solidity/prettier-plugin-solidity): code formatter

## Git Clone

The account-abstraction directory in this repository uses git submodules to include
[eth-infinitism/account-abstraction](https://github.com/eth-infinitism/account-abstraction) as a workspace. Make sure to
include the `--recurse-submodules` flag in your git clone command.

```bash
git clone --recurse-submodules https://github.com/stackup-wallet/contracts.git
```

## Sensible Defaults

This repository comes with sensible default configurations in the following files:

```text
├── .editorconfig
├── .eslintignore
├── .eslintrc.yml
├── .gitignore
├── .prettierignore
├── .prettierrc.yml
├── .solcover.js
├── .solhint.json
└── hardhat.config.ts
```

## VSCode Integration

This repository is IDE agnostic, but for the best user experience, you may want to use it in VSCode alongside Nomic
Foundation's [Solidity extension](https://marketplace.visualstudio.com/items?itemName=NomicFoundation.hardhat-solidity).

## GitHub Actions

All contracts will be linted and tested on every push and pull request made to the `main` branch.

# Usage

Below are some useful commands for development.

## Pre Requisites

Before being able to run any command, you need to create a `.env` file and set your environment variables. You can
follow the example in `.env.example`.

### Deployment methods

By default, all non test contract deployments will use the BIP-39 compatible mnemonic set in the `.env` file. If you
don't already have a mnemonic, you can use this [website](https://iancoleman.io/bip39/) to generate one.

If you do not want to use your mnemonic to deploy contracts, you can also use local providers like
[frame](https://github.com/floating/frame) to connect this repository to an alternative signing method (e.g. hardware
wallet). Make sure to set `DEPLOY_WITH_LOCAL_RPC` to the correct url in your `.env` file. **This is the preferred method
for security.**

> ℹ️ Note: If you are using `DEPLOY_WITH_LOCAL_RPC` make sure the local provider is configured to the correct network.
> If using [frame](https://github.com/floating/frame), make sure the dApp's default network is set to the correct chain.

```sh
cp .env.example .env
```

Then, proceed with installing dependencies:

```sh
yarn install
```

## Compile

Compile the smart contracts with Hardhat:

```sh
yarn run compile
```

## TypeChain

Compile the smart contracts and generate TypeChain bindings:

```sh
yarn run typechain
```

## Test

Run the tests with Hardhat:

```sh
yarn run test
```

## Lint Solidity

Lint the Solidity code:

```sh
yarn run lint:sol
```

## Lint TypeScript

Lint the TypeScript code:

```sh
yarn run lint:ts
```

## Coverage

Generate the code coverage report:

```sh
yarn run coverage
```

## Report Gas

See the gas usage per unit test and average gas per method call:

```sh
REPORT_GAS=true yarn run test
```

## Clean

Delete the smart contract artifacts, the coverage reports and the Hardhat cache:

```sh
yarn run clean
```

## Deploy

Deploy the contracts to Hardhat Network:

```sh
yarn run deploy:VerifyingPaymaster
```

# License

Distributed under the GPL-3.0 License. See [LICENSE](./LICENSE.md) for more information.
