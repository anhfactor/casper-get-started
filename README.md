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


4. Demonstrate key management concepts by modifying the client in the Multi-Sig tutorial to address one of the additional scenarios
5. Learn to transfer tokens to an account on the Casper Testnet. Check out this documentation.
6. Learn to Delegate and Undelegate on the Casper Testnet. Check out these instructions.
