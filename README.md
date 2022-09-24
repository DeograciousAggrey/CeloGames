# zkArcade <!-- omit in toc -->

![zkGamesRepoImage](https://user-images.githubusercontent.com/68210234/185812708-ae6d72d1-34f5-4fb0-9cba-bd3a1f75f2fa.png)

zkArcade is a platform that allows users to play zk (zero knowledge) games and mint an NFT as proof that they have won.


The project is currently on [Polygon Mumbai](https://mumbai.polygonscan.com/) and the frontend is hosted on [Vercel](https://github.com/vercel/vercel).

ZkArcade has 3 games so far: Futoshiki, Skyscrapers and Sudoku.

## ZkArcade Link:

<https://zk-arcade.vercel.app/>


## ZkArcade Demo video:

<https://youtu.be/xzd4vLtB8Lc>

## Contract Deployment Links in the mumbai explorer;

SudokuVerifier Contract deployed to: <https://mumbai.polygonscan.com/address/0xB0a7f823688BdB6125780D1Ebd2940Bf32F14FD6>

Sudoku Contract deployed to: <https://mumbai.polygonscan.com/address/0xD0276C2f1353157A562400309560C9cdCBA47212>

FutoshikiVerifier deployed to: <https://mumbai.polygonscan.com/address/0x164ae108DC16Eb8365C57b2339b3831800132B6C>

Futoshiki deployed to: <https://mumbai.polygonscan.com/address/0x0975D36B1A1125c28816c1106Aeef90df102331a>

SkyscrapersVerifier Contract deployed to: <https://mumbai.polygonscan.com/address/0x9F139c4e22e0d6e203209Ce1b104A843ffBb38e5>

Skyscrapers Contract deployed to: <https://mumbai.polygonscan.com/address/0x403f1B0d43fd40BDA51Dbc990cEDcc174C2DbA8d>






## Table of Contents <!-- omit in toc -->

- [Project Structure](#project-structure)
  - [circuits](#circuits)
  - [contracts](#contracts)
  - [zkarcade-ui](#zkarcade-ui)
- [Zero Knowledge Structure](#zero-knowledge-structure)
- [Run Locally](#run-locally)
  - [Clone the Repository](#clone-the-repository)
  - [Run circuits](#run-circuits)
  - [Run contracts](#run-contracts)
  - [Run zkarcade-ui](#run-zkarcade-ui)
- [Steps to Add a New Game](#steps-to-add-a-new-game)
- [Images of the zkArcade Application](#images-of-the-zkarcade-application)
  - [Initial page](#initial-page)
  - [Futoshiki Game](#futoshiki-game)
  - [Skyscrapers Game](#skyscrapers-game)
  - [Sudoku Game](#sudoku-game)

## Project Structure

The project has three main folders:

- circuits
- contracts
- zkarcade-ui

### circuits

The [circuits folder](/circuits/) contains all the circuits used in zkArcade.

To learn more about the zkArcade circuits, read the [README file](/circuits/README.md) inside the `circuits` folder.

### contracts

The [contracts folder](/contracts/) contains all the smart contracts used in zkArcade.

To learn more about the zkArcade smart contracts, read the [README file](/contracts/README.md) inside the `contracts` folder.

### zkarcade-ui

The [zkarcade-ui folder](/zkarcade-ui/) contains the zkArcade frontend.

To learn more about the zkArcade frontend, read the [README file](/zkarcade-ui/README.md) in the `zkarcade-ui` folder.

## Zero Knowledge Structure

The following graphic shows the structure of the most important zero knowledge elements of the zkGames project.

```text
├── circuits
│   ├── futoshiki
│   │   ├── futoshiki.circom
│   ├── skyscrapers
│   │   ├── skyscrapers.circom
│   ├── sudoku
│   │   ├── sudoku.circom
├── contracts
│   ├── contracts
│   │   ├── Futoshiki
│   │   │   ├── Futoshiki.sol
│   │   │   ├── verifier.sol
│   │   ├── Skyscrapers
│   │   │   ├── Skyscrapers.sol
│   │   │   ├── verifier.sol
│   │   ├── Sudoku
│   │   │   ├── Sudoku.sol
│   │   │   ├── verifier.sol
├── zkarcade-ui
│   ├── public
│   │   ├── zkproof
│   │   │   ├── futoshiki
│   │   │   │   ├── futoshiki.wasm
│   │   │   │   ├── futoshiki_0001.zkey
│   │   │   ├── skyscrapers
│   │   │   │   ├── skyscrapers.wasm
│   │   │   │   ├── skyscrapers_0001.zkey
│   │   │   ├── sudoku
│   │   │   │   ├── sudoku.wasm
│   │   │   │   ├── sudoku_0001.zkey
│   ├── zkproof
│   │   ├── futoshiki
│   │   │   ├── snarkjsFutoshiki.js
│   │   ├── skyscrapers
│   │   │   ├── snarkjsSkyscrapers.js
│   │   ├── sudoku
│   │   │   ├── snarkjsSudoku.js
│   │   ├── snarkjsZkproof.js
```

## Run Locally

### Clone the Repository

```bash
git clone https://github.com/DeograciousAggrey/zkArcade
```

### Run circuits

To run cicuits, go inside the `circuits` folder:

```bash
cd circuits
```

Then, follow the intructions in the [README file](/circuits/README.md) in the `circuits` folder.

### Run contracts

To run contracts, go inside the `contracts` folder:

```bash
cd contracts
```

Then, follow the intructions in the [README file](/contracts/README.md) in the `contracts` folder.

### Run zkarcade-ui

To run the frontend, go inside the `zkarcade-ui` folder:

```bash
cd zkgames-ui
```

Then, follow the intructions in the [README file](/zkarcade-ui/README.md) in the `zkarcade-ui` folder.

## Steps to Add a New Game

Steps to follow to add a new game (in each step you can check how is done with the other games):

1\. **Create the required circom circuits:**

- Inside the circuits folder, create a new folder and inside the new folder, create the necessary circom circuits.
- Compile the circuit and generate the `wasm`, `zkey` and `verifier.sol` files using the `execute.sh` file.

2\. **Create the necessary smart contracts:**

- Inside the `contracts/contracts` folder, create a new folder with the necessary smart contracts. Add here the verifier.sol generated before using snarkjs.
- Change the solidity version to `^0.8.4` (it is the version used in the other smart contracts) and the contract name (to `<gameName>Verifier`) in `verifier.sol`.
- Test the functionalities of the new smart contracts in `scripts/run.js`.
- Update the `contracts/scripts/deploy.js` file and deploy smart contracts.

3\. **Create the user interface of the game:**

- Inside `zkarcade-ui/components`, add a new folder to create all the components needed to render the game.
- Add a new page inside `zkarcade-ui/pages` to access the new game.
- Create the css of that page inside `zkarcade-ui/styles`, called `<GameName>.module.css`.
- Add an image inside `zkarcade-ui/assets` to represent the game (width: 700 pixels and height: 700 pixels).
- Inside `zkarcade-ui/public/zkproof` add a new folder with the wasm and zkey elements generated before.
- Inside `zkgames-ui/utils/abiFiles`, add a new folder with the `json` abi file of the smart contract.
- In `zkarcade-ui/utils/contractaddress.json`, add the new contract address.
- In `zkarcade-ui/zkproof`, create a new folder and inside the new folder create a new file called `snarkjs<NewGame>.js` with the code to export the call data.
- In `zkarcade-ui/components/gameList.js` add the game as follows:

```javascript
 {
   nameGame: "<nameGame>",
   imageGame: nameGameImage,
   urlGame: "/<nameGame>",
 }
```

## Images of the ZkArcade Application

### Initial page

![InitialPage](https://user-images.githubusercontent.com/68210234/185812026-1f5e2d0b-de1c-4c96-94c3-b7360993c5a6.png)

### Futoshiki Game

![FutoshikiGame](https://user-images.githubusercontent.com/68210234/185812023-7a8e7598-c48c-4be7-958d-8a6cec1d444b.png)

### Skyscrapers Game

![SkyscrapersGame](https://user-images.githubusercontent.com/68210234/185812019-02518410-a185-4335-9fc3-fb200295d3a9.png)

### Sudoku Game

![SudokuGame](https://user-images.githubusercontent.com/68210234/185812025-397a303a-f524-419c-8a33-ac6ce69752c1.png)
