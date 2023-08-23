# Adding trusted nodes to a network

## Generate account and keys

Open up a terminal and change directory into the project where you have compiled the node.

1. Generate a random secret phrase and keys by running the following command:
   ````
   ./target/release/node-template key generate --scheme Sr25519 --password-interactive

2. Use the secret phrase for the account you just generated to derive keys using the Ed25519 signature scheme.
   For example, run a command similar to the following:
   ````
   ./target/release/node-template key inspect --password-interactive --scheme Ed25519 "pig giraffe ceiling enter weird liar orange decline behind total despair fly"


You can see my outputs in the photo
![](https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project/blob/main/AddingTrustedNode/1.png)

## Create a custom chain specification

1. Export the local chain specification to a file named customSpec.json by running the following command:
   ````
   ./target/release/node-template build-spec --disable-default-bootnode --chain local > customSpec.json
2. Open the customSpec.json file in a text editor.
3. Modify the name field to identify this chain specification as a custom chain specification.
4. Modify aura field to specify the nodes with the authority to create blocks by adding the Sr25519 SS58 address keys for each network participant.
5. Modify the grandpa field to specify the nodes with the authority to finalize blocks by adding the Ed25519 SS58 address keys for each network participant.
6. Save your changes and close the file.

## Convert the chain specification to raw format
1. Convert the customSpec.json chain specification to the raw format with the file name customSpecRaw.json by running the following command:
      ````
      ./target/release/node-template build-spec --chain=customSpec.json --raw --disable-default-bootnode > customSpecRaw.json

You can see my outputs in the photos:
1. ![](https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project/blob/main/AddingTrustedNode/2.png)
2. ![](https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project/blob/main/AddingTrustedNode/3.png)
3. ![](https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project/blob/main/AddingTrustedNode/4.png)

   
## Start the first node
1. Start the first node using the custom chain specification by running a command similar to the following:
   ````
   ./target/release/node-template \
   --base-path /tmp/node01 \
   --chain ./customSpecRaw.json \
   --port 30333 \
   --rpc-port 9945 \
   --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
   --validator \
   --rpc-methods Unsafe \
   --name MyNode01 \
   --password-interactive

## Add keys to the keystore

1. Insert the aura secret key generated from the key subcommand by running a command similar to the following:
   ````
   ./target/release/node-template key insert --base-path /tmp/node01 \
   --chain customSpecRaw.json \
   --scheme Sr25519 \
   --suri <your-secret-seed> \
   --password-interactive \
   --key-type aura

2. Insert the grandpa secret key generated from the key subcommand by running a command similar to the following:
   ````
   ./target/release/node-template key insert \
   --base-path /tmp/node01 \
   --chain customSpecRaw.json \
   --scheme Ed25519 \
   --suri <your-secret-key> \
   --password-interactive \
   --key-type gran

3. Verify that your keys are in the keystore for node01 by running the following command:
   ````
   ls /tmp/node01/chains/local_testnet/keystore


You can see my outputs in the photo:
![](https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project/blob/main/AddingTrustedNode/5.png)

## Generate a second set of keys

1. You can repeat the steps in the previous section using a different identity on your local computer to generate a second key pair.
   Like this:
   ![](https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project/blob/main/AddingTrustedNode/6.png)



## Enable other participants to join

1. Start a second blockchain node by running a command similar to the following:
   ````
   ./target/release/node-template \
   --base-path /tmp/node02 \
   --chain ./customSpecRaw.json \
   --port 30334 \
   --rpc-port 9946 \
   --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
   --validator \
   --rpc-methods Unsafe \
   --name MyNode02 \
   --bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWLmrYDLoNTyTYtRdDyZLWDe1paxzxTw5RgjmHLfzW96SX \
   --password-interactive

2. If you don't set the correct bootnode identifier, you see errors like this:
   ![](https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project/blob/main/AddingTrustedNode/7.png)


3. Add the aura secret key generated from the key subcommand by running a command similar to the following:
   ````
   ./target/release/node-template key insert --base-path /tmp/node02 \
   --chain customSpecRaw.json \
   --scheme Sr25519 \
   --suri <second-participant-secret-seed> \
   --password-interactive \
   --key-type aura
4. Add the grandpa secret key generated from the key subcommand to the local keystore by running a command similar to the following:
   ````
   ./target/release/node-template key insert --base-path /tmp/node02 \
   --chain customSpecRaw.json \
   --scheme Ed25519 --suri <second-participant-secret-seed> \
   --password-interactive \
   --key-type gran
5. Verify that your keys are in the keystore for node02 by running the following command:
    ````
    ls /tmp/node02/chains/local_testnet/keystore

Like this:

![](https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project/blob/main/AddingTrustedNode/8.png)

6. Restart the second blockchain node by running the following command:
   ````
   ./target/release/node-template \
   --base-path /tmp/node02 \
   --chain ./customSpecRaw.json \
   --port 30334 \
   --rpc-port 9946 \
   --telemetry-url 'wss://telemetry.polkadot.io/submit/ 0' \
   --validator \
   --rpc-methods Unsafe \
   --name MyNode02 \
   --bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWLmrYDLoNTyTYtRdDyZLWDe1paxzxTw5RgjmHLfzW96SX \
   --password-interactive

After both nodes have added their keys to their respective keystores—located under /tmp/node01 and /tmp/node02—and been restarted, you should see the same genesis block and state root hashes.

You should also see that each node has one peer (1 peers), and they have produced a block proposal (best: #2 (0xe111…c084)). After a few seconds, you should see new blocks being finalized on both nodes.
   
   
