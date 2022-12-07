# playground-near
Some cool NEAR smart contract playground, mostly another practice collection for near_sdk/rust.

## Note 
Writing smart contract in Near is really simple and delightful experience. 

It's how blockchain development should be, instead of torturing myself into terrible outdated documents/tutorials or obfuscated smart contract languages, NEAR use RUST, a decent native language that is supported out of the box by vscode & vast community.

### Compiling WASM
Something that will be used quite a lot with NEAR contract is this wasm compiling :

      RUSTFLAGS='-C link-arg=-s' cargo build --target wasm32-unknown-unknown --release
      
### Deploy contract
1. Create your contract from your account :

       near create-account contract.account.testnet --masterAccount account.testnet --initialBalance 5

2. Pretty much straightforward :

       near deploy --accountId=contract.account.testnet --wasmFile=target/wasm32-unknown-unknown/release/near_contract.wasm
      
3. Delete contract to re-deploy new one :

       near delete contract.account.testnet account.testnet 
      
4. Call functions :

- init call first :
      
       near call contract.account.testnet init --accountId=account.testnet

- function call be-like :

       near call contract.account.testnet buy_product '{"product_id": "1"}' --depositYocto=1000000000000000000000000 --accountId=buyer.account.testnet
      
- view function call :

       near view contract.account.testnet get_product '{"id": "1"}'
      
