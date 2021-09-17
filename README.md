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

- Deploy a simple contract 
<img width="1235" alt="Screen Shot 2021-09-17 at 10 32 00" src="https://user-images.githubusercontent.com/13186215/133720041-7acb575b-fd20-44aa-89c5-5dd6d922cefe.png">


2. Complete one of the existing tutorials for writing smart contracts.   
I choose "A Counter Contract Tutorial". 
- Check faucet account:
```
nctl-view-faucet-account
```
<img width="1029" alt="Screen Shot 2021-09-17 at 10 21 47" src="https://user-images.githubusercontent.com/13186215/133720188-55aa2f45-d1d0-48c2-9529-8c41e496f62d.png">

- Create local network and running node:  

```
nctl-assets-setup && nctl-start
```
<img width="721" alt="Screen Shot 2021-09-17 at 09 17 56" src="https://user-images.githubusercontent.com/13186215/133715043-d7e11384-a0c1-454d-9f28-5c9cd882783e.png">
- Get the state root hash and query actual state. 
<img width="863" alt="Screen Shot 2021-09-17 at 10 38 15" src="https://user-images.githubusercontent.com/13186215/133720400-b37e25d7-0eb6-4939-97b4-def1579caf3b.png">

- Deploy contract and checking it state:


4. Demonstrate key management concepts by modifying the client in the Multi-Sig tutorial to address one of the additional scenarios
5. Learn to transfer tokens to an account on the Casper Testnet. Check out this documentation.
6. Learn to Delegate and Undelegate on the Casper Testnet. Check out these instructions.
