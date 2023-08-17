# Building a Blockchain with Substrate Node Template

In this guide, we will walk through the process of building and interacting with a blockchain using Substrate Node Template. We'll cover compiling and starting a substrate node, installing and starting the front-end template, transferring funds, and stopping the node.

## Compile and Start a Substrate Node

1. Clone the Substrate Node Template repository:
    ```
    git clone https://github.com/substrate-developer-hub/substrate-node-template
    ```

2. Change to the cloned directory:
    ```
    cd substrate-node-template
    ```

3. Build and compile the project:
    ```
    cargo build --release
    ```

4. Start the node:
    ```
    ./target/release/node-template --dev
    ```

## Install and Start Front-End Template

Substrate provides a front-end template for interacting with the blockchain through a user interface.

1. Check your Node.js and Yarn versions:
    ```
    node --version
    yarn --version
    ```

2. Clone the Substrate front-end template repository:
    ```
    git clone https://github.com/substrate-developer-hub/substrate-front-end-template
    ```

3. Change to the cloned directory:
    ```
    cd substrate-front-end-template
    ```

4. Install the project dependencies:
    ```
    yarn install
    ```

5. Start the front-end:
    ```
    yarn start
    ```

Access the dashboard at http://localhost:8000/ to interact with the node through the user interface.

## Transfer Funds

1. Open the dashboard and navigate to the "balances" section.

2. Select a user, e.g., Dave, and transfer funds to them by specifying the amount.

3. Check the balances table to verify the transfer.

## Stop Node

To stop the local Substrate node:

- Return to the terminal where the node is running.
- Press Control-c to terminate the process.
- Verify that the terminal returns to the substrate-node-template directory.

---

Feel free to explore and experiment with your Substrate-based blockchain!

For screenshots and visual guidance, refer to the [BuildingBlockchain](https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project/tree/main/BuildingBlockchain) directory in the repository.
