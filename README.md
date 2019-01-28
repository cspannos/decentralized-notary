# Decentralized Notary  
This Decentralized Notary harnesses the power of the Ethereum blockchain and the InterPlanetary File System (IPFS) to verify the authenticity of files. It does so by, not only using IPFS as a peer-to-peer hosting platform for this dApp, but by also utilizing the IPFS hash of files as Proof-of-Existance and storing the proofs on the Ethereum blockchain. Additionally, this notary returns a transaction receipt certifying that the IPFS hash was registered on the blockchain. It is possible to send your file’s IPFS hash to an Ethereum account as likewise users can send their file hashes to you.   

Please note that this is an MVP and I am still building out specifications and squashing bugs.

## Getting Started
The environment for this implementation relies upon:
* Linux (Debian Stretch / Ubuntu Bionic Beaver)
* Truffle v5.0.2
* Ganache GUI (v2.0.0-beta.2) / CLI (v6.2.5)
* NPM 6.7.0
* Infura gateway API
* IPFS

### Dependencies
    * ipfs-http-client: 29.0.1
    * openzeppelin-solidity: 2.1.2
    * react: 16.6.3
    * react-dom: 16.6.3
    * react-scripts: 2.1.3
    * web3: 1.0.0-beta.37

### How to install:
* Truffle: ``$ npm install truffle -g``
* Ganache: download the AppImage for GUI / CLI ``$ npm install -g ganache-cli``
* IPFS (if deploying): To install:
``$ tar xvfz go-ipfs.tar.gz``
``$ cd go-ipfs``
``$ ./install.sh``,
then to initialize run ``ipfs init``.

To spin this implementation up on your own machine, follow these steps:
- clone this repository;
- cd into the root directory ‘decentralized-notary’;
-  run Ganache (GUI or CLI (cmd: ``$ ganache-cli``) ;
- use the mnemonic code that Ganache provides to open MetaMask. Place the mnemonic in MetaMask’s option to ‘Import using account seed phrase’, and initialize your account.
- in another terminal, also in the root directory, run ``$ truffle develop``;
- in another terminal, cd to ‘decentralized-notary/client’, run ``$ npm run start``;

This last step will initialize a local implementation of this project and load in your browser at: http://localhost:3000/ . You will be able to upload a file from your local disk to IPFS and have the file’s hash returned in your browser.

### Deployment
To deploy the dApp, you must first initiate a production build. Change directory to ‘/decentralized-notary/client’ and ``$ run npm run build``. Once the build is done, in a separate terminal run ``$ ipfs deamon``. In another separate terminal, cd to /decentralized-notary/client and run ``$ ipfs add -r build``, copy the last hash returned, indicating the root for the ‘build’ directory, then run ``$ ipfs swarm peers``, then ``$ ipfs name publish yourhashforthebuilddirectory``. Go to a gateway, such as https://ipfs.infura.io and load the hash with index.html as such: /ipfs/QmY6u6UwUnsZgRd5tzMhMojnNRhyGX2PziAyHZ3Z5bp3wM/index.html
Go have a coffee, check your notifications and see if the dApp has loaded in your browser.

**You can interact with this contract on the Ropsten test network:**
https://ipfs.infura.io/ipfs/QmY6u6UwUnsZgRd5tzMhMojnNRhyGX2PziAyHZ3Z5bp3wM/index.html

## Authors
Chris Spannos -  Consensys Academy Developer Bootcamp 2019
