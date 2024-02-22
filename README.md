# PYTH
PYTH contact
on:
  pull_request:
    paths:
      - target_chains/aptos/contracts/**
  push:
    branches:
      - main
    paths:
      - target_chains/aptos/contracts/**

name: Aptos Contract

jobs:
  aptos-tests:
    name: Aptos tests
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: target_chains/aptos/contracts/
    steps:
      - uses: actions/checkout@v3

      - name: Download CLI
        run: wget https://github.com/aptos-labs/aptos-core/releases/download/aptos-cli-v1.0.4/aptos-cli-1.0.4-Ubuntu-22.04-x86_64.zip

      - name: Unzip CLI
        run: unzip aptos-cli-1.0.4-Ubuntu-22.04-x86_64.zip

      - name: Run tests
        run: ./aptos move test
