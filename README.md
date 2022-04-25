# Bye To Tents Demo Project (by Tolga Yaz)
Ncd Demo Project

This is a demo project for a planned funding campaign called "Bye To Tents".

The campaign's goal is to build practical houses for needy people who live in tents.

The smart contract coded for this demo project may be used for registering new house(s) to be donated, making donations, viewing the number and situation of the house(s) registered.

You can observe the scripts and the code to learn more.

The loom video for the project: https://www.loom.com/share/c3dcfe2f476e4b0e88de0c826938bfdd

# Requirements

NodeJs, git, yarn, near-cli

# Installation

### 1. Clone this repo
### 2. Run yarn

# Usage

### 1. Run yarn build:release
- to build the contract and get the .wasm file

### 2. Run near dev-deploy ./build/release/bye-to-tents.wasm
- to generate a test account and deploy the contract

### 3. Run export CONTRACT=developer-test-account
- to make the function calls easier (writing the test accounts each time might be hard)

### 4. Observe the code and the scripts then try any of the functions or the scripts

# Functions

### Note: There is a class named "House" and a persistent unordered map called "houses" that the functions work on.

## 1. addHouse
- To register house(s) to be donated
- Fund need and number of houses should be provided as arguments

### An example call:
near call $CONTRACT addHouse '{"fundNeed":"100", "numOfHouses":"1"}' --accountId $CONTRACT

## 2. donateById
- To donate to a house via its id
- House Id and donation amount (in Near) should be provided as arguments

### An example call:
near call $CONTRACT donateById '{"amount":"10","houseId":"1"}' --accountId $CONTRACT

## 3. getDetailsByHouseId

- To see the funding situation of a house
- House Id should be provided as arguments

### An example call:
near call $CONTRACT getDetailsByHouseId '{"houseId":"1"}' --accountId $CONTRACT

## 4. returnHouses

- To get the number of registered houses

### An example call:
near view $CONTRACT returnHouses

## 5. clearAllHouses

- To clear all registered houses (for demo purposes)

### An example call:
near call $CONTRACT clearAllHouses --accountId $CONTRACT
