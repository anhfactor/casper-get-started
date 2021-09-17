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

- Deploy counter contract and checking it state:
<img width="1235" alt="Screen Shot 2021-09-17 at 10 32 00" src="https://user-images.githubusercontent.com/13186215/133722394-307d2002-de04-4eff-b739-48c1f519cccd.png">

- The counter is currently set to 1
<img width="853" alt="Screen Shot 2021-09-17 at 11 03 01" src="https://user-images.githubusercontent.com/13186215/133722471-ba38b9f9-753a-481c-8032-42d838eebe30.png">

- After increment the counter again, the counter is set to 2. 
 <img width="1426" alt="Screen Shot 2021-09-17 at 11 07 23" src="https://user-images.githubusercontent.com/13186215/133722689-11689f8b-49c2-40b9-bd4d-cc01d55589f1.png">

3. Demonstrate key management concepts by modifying the client in the Multi-Sig tutorial to address one of the additional scenarios. 
- First clone the keys management project: https://github.com/casper-ecosystem/keys-manager
- Create .env and run npm install
- Create an extension name "scenario-concept.js":
```
const keyManager = require('./key-manager');

(async function () {
    // 1. Weight of `fullAccount` to 2
    // 2. Key Management Threshold to 2
    // 3. Deploy Threshold to 1
    // 4. First new key with weight 1 (deploy key)

    let deploy;

    // 0. Initial state of the account.
    // There should be only one associated key (faucet) with weight 1.
    // Deployment Threshold should be set to 1.
    // Key Management Threshold should be set to 1.
    let masterKey = keyManager.randomMasterKey();
    let fullAccount = masterKey.deriveIndex(1);    // deployment and management
    let deployAccount = masterKey.deriveIndex(2);    // only for deployment

    console.log("\n0.1 Fund main account.\n");
    await keyManager.fundAccount(fullAccount);
    await keyManager.printAccount(fullAccount);
    
    console.log("\n[x]0.2 Install Keys Manager contract");
    deploy = keyManager.keys.buildContractInstallDeploy(fullAccount);
    await keyManager.sendDeploy(deploy, [fullAccount]);
    await keyManager.printAccount(fullAccount);

    // 1. Set fullAccount's weight to 2
    console.log("\n1. Set faucet's weight to 2\n");
    deploy = keyManager.keys.setKeyWeightDeploy(fullAccount, fullAccount, 2);
    await keyManager.sendDeploy(deploy, [fullAccount]);
    await keyManager.printAccount(fullAccount);
    
    // 2. Set Keys Management Threshold to 2.
    console.log("\n2. Set Keys Management Threshold to 2\n");
    deploy = keyManager.keys.setKeyManagementThresholdDeploy(fullAccount, 2);
    await keyManager.sendDeploy(deploy, [fullAccount]);
    await keyManager.printAccount(fullAccount);
    
    // 3. Set Deploy Threshold to 1.
    console.log("\n3. Set Deploy Threshold to 1.\n");
    deploy = keyManager.keys.setDeploymentThresholdDeploy(fullAccount, 1);
    await keyManager.sendDeploy(deploy, [fullAccount]);
    await keyManager.printAccount(fullAccount);
    
    // 4. Add first new key with weight 1 (first account).
    console.log("\n4. Add first new key with weight 1.\n");
    deploy = keyManager.keys.setKeyWeightDeploy(fullAccount, deployAccount, 1);
    await keyManager.sendDeploy(deploy, [fullAccount]);
    await keyManager.printAccount(fullAccount);
    
})();
```
And add scripts in package.json. 
```
start:scenario-concept": "node -r dotenv/config ./src/scenario-concept.js"
```
- Then run command:  
```
npm run start:scenario-concept
```
<img width="685" alt="Screen Shot 2021-09-17 at 12 07 06" src="https://user-images.githubusercontent.com/13186215/133727941-15f76048-e1c1-4aa7-8af8-9820df5ff0e7.png">

<img width="697" alt="Screen Shot 2021-09-17 at 12 07 21" src="https://user-images.githubusercontent.com/13186215/133728003-98637b1c-30dd-4ad6-9045-7157d5218fca.png">



5. Learn to transfer tokens to an account on the Casper Testnet. Check out this documentation.
6. Learn to Delegate and Undelegate on the Casper Testnet. Check out these instructions.
