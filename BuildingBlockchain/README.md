#Building Blockchain with Substrate Node Template

Since we have Rust installed, it is now time to build our own blockchain using Substrate and experiencing the powerful features it brings.

##Compile and starting a substrate node

*1 We need to clone to be able to start a substrate node on our system.
    
    git clone https://github.com/substrate-developer-hub/substrate-node-template

*2 Let’s change our directory and go inside the project that we’ve just cloned - 
    
    cd substrate-node-template
*3 To start the node, we first need to build and compile this project
    
    cargo build --release

 *4 Now we will start the node with the following command 

     ./target/release/node-template --dev



##Install and starting front-end template

Substrate also has a front end template for the dashboard so you can interact with the node through a UI and not just through the terminal.
For the front end, yarn and nodeJS are both required.

*1 Check your nodejs and yarn versions
 
    node --version
    yarn --version
*2 We need to clone the project that has the code for the front-end template
    
    git clone https://github.com/substrate-developer-hub/substrate-front-end-template


*3 We now need to change our directory to the project we just cloned
   
    cd substrate-front-end-template

*4 Now we will install the project using yarn

    yarn install

*5 We just have to start the front end with the following command

    yarn start

http://localhost:8000/ will automatically be opened in your default browser once the front end starts, but you can also open it manually. Now from the dashboard, you will be able to interact with the node.

##Transfer Funds
On the dashboard, you will notice the “balances” section, look at the balances of various users such as Dave, who have zero balance

*1 Now we will try and transfer some money to Dave.

*2 Select dave from the list and transfer at least 1000000000000 to dave

*3 All we need to do is first check the balances table and see if the value was transferred to Dave
