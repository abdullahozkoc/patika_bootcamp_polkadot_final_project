# Simulating a substrate network

1. Starting the node
   Start a terminal, change directory into the project and run the command below to purge old chain data -
   ````
   ./target/release/node-template purge-chain --base-path /tmp/alice --chain local
2. Start the local blockchain node using the “alice” account by running the following command
   ````
   ./target/release/node-template 

    --base-path /tmp/alice 

    --chain local 

    --alice 

    --port 30333 

    --ws-port 9945 

    --rpc-port 9933 

    --node-key 0000000000000000000000000000000000000000000000000000000000000001 

    --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" 

    --validator

 When you run this command, you get the output in the photo 


![](https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project/blob/main/SimulateNetwork/Ekran%20G%C3%B6r%C3%BCnt%C3%BCs%C3%BC%20(163).png)

## Adding another node

1. To do this, we will open up a new terminal to start and interact with the second node and purge old chain data with the following command -
   ````
   ./target/release/node-template purge-chain --base-path /tmp/bob --chain local -y
2. Now we will start the new node but using “bob” account (just like we used “alice” account last time). Run this command -
   ````
    ./target/release/node-template 

    --base-path /tmp/bob 

    --chain local 

    --bob 

    --port 30334 

    --ws-port 9946 

    --rpc-port 9934 

    --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" 

    --validator 

    --bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWEyoppNCUx8Yx66oV9fJnriXwCcXwDDUA2kj6vnc6iDEp

 When you run this command, you get the output in the photo 
![](https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project/blob/main/SimulateNetwork/Ekran%20G%C3%B6r%C3%BCnt%C3%BCs%C3%BC%20(164).png)


## Verify Block production

After running Alice and Bob nodes, when we look at Alice's node, we will see that it matches Bob's node where I marked in the photo

![](https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project/blob/main/SimulateNetwork/Ekran%20G%C3%B6r%C3%BCnt%C3%BCs%C3%BC%20(165).png)

When we close Bob's node, we see that the match is over. As marked in the photo below

![](https://github.com/abdullahozkoc/patika_bootcamp_polkadot_final_project/blob/main/SimulateNetwork/Ekran%20G%C3%B6r%C3%BCnt%C3%BCs%C3%BC%20(166).png)

   
