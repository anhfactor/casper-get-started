# Get Started With Casper

1. Create and deploy a simple, smart contract with cargo casper and cargo test. 
- Installing rust, cargo-casper with rust package manager
- Create the project which I named 1-simple-smart-contract
- Compile contract with WebAssembly and build it
```
cd contract
rustup install $(cat rust-toolchain)
rustup target add --toolchain $(cat rust-toolchain) wasm32-unknown-unknown
cargo build --release

```

<img width="1069" alt="Screen Shot 2021-09-17 at 08 18 54" src="https://user-images.githubusercontent.com/13186215/133709525-16711572-69a0-477b-919b-bfa81c9107e7.png">


- Test the contract. 
<img width="802" alt="Screen Shot 2021-09-17 at 00 02 30" src="https://user-images.githubusercontent.com/13186215/133655047-84889dab-b9bc-4781-951c-a3e83baf4547.png">


2. Complete one of the existing tutorials for writing smart contracts.   
I choose "A Counter Contract Tutorial". 
- Check faucet account:
```
nctl-view-faucet-account
```
<img width="983" alt="Screen Shot 2021-09-15 at 23 59 50" src="https://user-images.githubusercontent.com/13186215/133711067-da08c01c-86ae-47ef-a671-bd915d939620.png">
- Create local network and running node:  

```
nctl-assets-setup && nctl-start
```
<img width="721" alt="Screen Shot 2021-09-17 at 09 17 56" src="https://user-images.githubusercontent.com/13186215/133715043-d7e11384-a0c1-454d-9f28-5c9cd882783e.png">
- Get the state root hash and query actual state

<img width="837" alt="Screen Shot 2021-09-16 at 00 53 33" src="https://user-images.githubusercontent.com/13186215/133716829-1b26db04-51df-4a76-99df-686f64ec2b1f.png">
<img width="796" alt="Screen Shot 2021-09-16 at 01 06 33" src="https://user-images.githubusercontent.com/13186215/133717179-d50718ac-994c-46e4-ba52-f49b1184d957.png">

- Deploy contract and checking it state:

<img width="660" alt="Screen Shot 2021-09-16 at 01 19 51" src="https://user-images.githubusercontent.com/13186215/133717621-8bc86e39-ad1a-45a1-a52c-06a0f43e7048.png">

<img width="822" alt="Screen Shot 2021-09-16 at 01 25 03" src="https://user-images.githubusercontent.com/13186215/133717632-a1c3da2b-1217-4206-8604-a469e7bbc439.png">
<img width="1027" alt="Screen Shot 2021-09-16 at 01 28 25" src="https://user-images.githubusercontent.com/13186215/133717650-d8d386dc-4d04-4384-b671-1de3ba88ba61.png">

4. Demonstrate key management concepts by modifying the client in the Multi-Sig tutorial to address one of the additional scenarios
5. Learn to transfer tokens to an account on the Casper Testnet. Check out this documentation.
6. Learn to Delegate and Undelegate on the Casper Testnet. Check out these instructions.
