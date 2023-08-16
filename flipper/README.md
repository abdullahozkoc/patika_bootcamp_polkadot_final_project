# Flipper Smart Contract Project

## Introduction

This repository contains the source code and instructions for the "flipper" smart contract project, implemented using Rust and the ink! smart contract language. Before you can begin using the project, you need to perform some necessary setup steps.


## Tutorial Objectives

By completing this tutorial, you will achieve the following objectives:

- Build and test a smart contract using the ink! smart contract language.
- Deploy a smart contract on a local Substrate node.
- Interact with a smart contract using the cargo-contract CLI.

## Installation

To get started, follow these steps to set up your development environment:
1. Pre-installation
  First complete the institutions in this issue https://docs.substrate.io/install/

2. Install the cargo-contract CLI tool:

   ```bash
   cargo install --force --locked cargo-contract
3. Install the Substrate Contracts Node:
   ```bash
   cargo install contracts-node --git https://github.com/paritytech/substrate-contracts-node.git --force --locked
4. Install Git
   Follow the instructions on the official Git website to install Git for your operating system.

## Getting Started
1. Clone the project repository to your local machine:
    ````
    git clone https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project.git
    
2. Start your local Substrate node using the following command:
   ````
   substrate-contracts-node --log info,runtime::contracts=debug 2>&1
3. Navigate to the "flipper" project folder and build the contract:
   ````
   cd patika_bootcamp_polkadot_final_project/flipper
   cargo contract build

4. Instantiate the contract with the constructor and arguments:
   ````
   cargo contract instantiate --constructor new --args "false" --suri //Alice --salt $(date +%s)
5. Interact with the contract:
Once the smart contract is deployed, you can interact with it using the following commands:
  . Get the current state using get():
   ````
   cargo contract call --contract $INSTANTIATED_CONTRACT_ADDRESS --message get --suri //Alice --dry-run
  . Flip the state using flip():
  ````
 cargo contract call --contract $INSTANTIATED_CONTRACT_ADDRESS --message flip --suri //Alice

   





   
