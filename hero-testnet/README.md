---
description: Hero Testnet details and how to connect
---

# Hero Testnet

**Domain:** [testnet.heroesofnft.com](https://testnet.heroesofnft.com/ext/bc/p91WZe6xXivSgCBZwWwJmAfyxM92r819G7sqqRrYYRPzy49bP/rpc)

## Version

**Avalanchego:** v1.9.4 **Subnet EVM:** v0.4.6

### Subnet Details

**VM ID:** nyfSdZmrxTXbJrxdUoqLegVGQzWF6RVL4jYn7Yr6NsMzpdrFA

**Subnet ID:** 21HEmZx5zVHYcP3JzbmRGVsYdm3HjrM2BMEPoCpoS3fHmZshq9

**Chain ID:** 2KV1ighhTjNpuQq8BVgHeJF3QHdF3KxhY9AqB9M1GfUuBCKjNo

#### Subnet network parameters:

```yml
Network ID: 17772
Chain ID: 17772
Block Gas Limit: 16,000,000
10s Gas Target: 24,000,000
Min Fee: 24 GWei
Target Block Rate: 2s (Same as C-Chain)
```

#### Validators

* **Validator 0**
  * **ID:** `NodeID-6tWHHU9uVWAf46qTYTsnTnVZJeL65hwgR`
  * **IP:** `173.249.33.39`
* **Validator 1**
  * **ID:** `NodeID-AGSMAmA7HStwbKCJAYpBzBvDmjyd6BVvd`
  * **IP:** `154.12.249.187`
* **Validator 2**
  * **ID:** `NodeID-7iWipVaLBfGSMjY6WNCXiWtY5yKLe1kTx`
  * **IP:** `66.94.125.28`

#### Adding to MetaMask

```yaml
Network Name: Hero Testnet
RPC URL: https://testnet.heroesofnft.com:443/ext/bc/2KV1ighhTjNpuQq8BVgHeJF3QHdF3KxhY9AqB9M1GfUuBCKjNo/rpc
Chain ID: 17772
Symbol: HRM
Explorer: https://testnet.avascan.info/blockchain/hero/
```

#### Genesis Data

Hero testnet genesis data JSON as follows:

file: `hero-testnet-genesis.json`

{% code lineNumbers="true" %}
```json
{
  "config": {
    "chainID": 17772,
    "homesteadBlock": 0,
    "eip150Block": 0,
    "eip150Hash": "0x2086799aeebeae135c246c65021c82b4e15a2c451340993aacfd2751886514f0",
    "eip155Block": 0,
    "eip158Block": 0,
    "byzantiumBlock": 0,
    "constantinopleBlock": 0,
    "petersburgBlock": 0,
    "istanbulBlock": 0,
    "muirGlacierBlock": 0,
    "subnetEVMTimestamp": 0,
    "feeConfig": {
      "gasLimit": 16000000,
      "minBaseFee": 24000000000,
      "targetGas": 24000000,
      "baseFeeChangeDenominator": 36,
      "minBlockGasCost": 0,
      "maxBlockGasCost": 10000000,
      "targetBlockRate": 2,
      "blockGasCostStep": 500000
    },
    "allowFeeRecipients": false,
    "contractDeployerAllowListConfig": {
      "blockTimestamp": 0,
      "adminAddresses": ["0x0ed6431f48560e943cc8c1edeae3d7f7edde46a7"]
    },
    "contractNativeMinterConfig": {
      "blockTimestamp": 0,
      "adminAddresses": ["0x0ed6431f48560e943cc8c1edeae3d7f7edde46a7"]
    },
    "feeManagerConfig": {
      "blockTimestamp": 0,
      "adminAddresses": ["0x0ed6431f48560e943cc8c1edeae3d7f7edde46a7"],
      "enabledAddresses": []
    }
  },
  "alloc": {
    "0ed6431f48560e943cc8c1edeae3d7f7edde46a7": {
      "balance": "100000000000000000000000000"
    }
  },
  "timestamp": "0x0",
  "gasLimit": "0xF42400",
  "difficulty": "0x0",
  "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
  "coinbase": "0x0000000000000000000000000000000000000000",
  "number": "0x0",
  "gasUsed": "0x0",
  "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000"
}
```
{% endcode %}

### Joining Hero Testnet

**To setup the node for joining Hero Testnet, first we have to join the Avalanche Fuji testnet then install subnet-evm to plugins with the correct VM ID.**

```bash
# First download go
# install the version > 1.18.1
wget https://go.dev/dl/go1.18.8.linux-amd64.tar.gz
# install go
sudo tar -C /usr/local -xzf go1.18.8.linux-amd64.tar.gz
# add go to $PATH by using avalanche/validators/.profile
# copy the content to the last line of user .profile file
echo "export PATH=$PATH:/usr/local/go/bin:/home/admin/go/bin" >>> .profile
# use updated .profile
source .profile

####################################
# Prebuilt Binaries

# Use avalanche-installer script to join Avalanche Fuji network
# **NOTE:** This script uses **sudo**
wget -nd -m https://raw.githubusercontent.com/ava-labs/avalanche-docs/master/scripts/avalanchego-installer.sh;\
chmod 755 avalanchego-installer.sh;\
./avalanchego-installer.sh

# - OR - Directly download the latest pre-built binary to join Avalanche Fuji
cd ~
wget https://github.com/ava-labs/avalanchego/releases/download/vx.x.x/avalanchego-<distro>-vx.x.x.zip
unzip avalanchego-<distro>-v<x.x.x>.zip
# rename the build folder into avalanche-node
mv build avalanche-node

# Download the subnet-evm binaries for joining Hero Testnet
# darwin amd64 for apple amd chips / darwin for arm64 (apple m series chips)
wget https://github.com/ava-labs/subnet-evm/releases/download/vx.x.x/subnet-evm_x.x.x_<distro>_<chip>.tar.gz
tar xfz subnet-evm_x.x.x_<distro>_<chip>.tar.gz
mv subnet-evm nyfSdZmrxTXbJrxdUoqLegVGQzWF6RVL4jYn7Yr6NsMzpdrFA

# copy plugin to avalanchego/plugins
cp ./nyfSdZmrxTXbJrxdUoqLegVGQzWF6RVL4jYn7Yr6NsMzpdrFA ~/avalanche-node/plugins/

# ** Configs **
# Local node config for whitelisting Hero Subnet & connecting to Fuji
vim ~/.avalanchego/configs/node.json
# paste content below
{
  "http-host": "127.0.0.1",
  "http-port": 9650,
  "network-id": "fuji",
  "whitelisted-subnets": "21HEmZx5zVHYcP3JzbmRGVsYdm3HjrM2BMEPoCpoS3fHmZshq9"
}

# Vm alias config
vim ~/.avalanchego/vms/aliases.json
# paste content below
{
  "nyfSdZmrxTXbJrxdUoqLegVGQzWF6RVL4jYn7Yr6NsMzpdrFA": ["hero", "herovm", "hvm"]
}

# Paste the following contents of upgrade.json into
vim ~/.avalanchego/configs/chains/2KV1ighhTjNpuQq8BVgHeJF3QHdF3KxhY9AqB9M1GfUuBCKjNo/upgrade.json

```

Contents of upgrade.json

```json
{
  "precompileUpgrades": [
    {
      "feeManagerConfig": {
        "blockTimestamp": 1671106500,
        "disable": true
      }
    },
    {
      "contractNativeMinterConfig": {
        "blockTimestamp": 1671106500,
        "disable": true
      }
    },
    {
      "feeManagerConfig": {
        "blockTimestamp": 1671112800,
        "adminAddresses": ["0x0ed6431f48560e943cc8c1edeae3d7f7edde46a7"]
      }
    },
    {
      "contractNativeMinterConfig": {
        "blockTimestamp": 1671112800,
        "adminAddresses": ["0x0ed6431f48560e943cc8c1edeae3d7f7edde46a7"]
      }
    },
    {
      "contractNativeMinterConfig": {
        "blockTimestamp": 1671127200,
        "disable": true
      }
    },
    {
      "contractNativeMinterConfig": {
        "blockTimestamp": 1671186630,
        "adminAddresses": [
          "0x0ed6431f48560e943cc8c1edeae3d7f7edde46a7",
          "0x1a3624Ec8355229cC4597c2746C92035cef26241"
        ]
      }
    }
  ]
}

```

Finally execute the avalanchego binary !

```bash
# Execute !
./avalanche-node/avalanchego --config-file=~/.avalanchego/configs/node.json
```

