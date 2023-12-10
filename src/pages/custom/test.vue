<template>
  <div>
    <button @click="addNewBlock">Add new block</button>
    <input v-model="newValue" type="number" min="0">
    <button @click="setTestValue(newValue)">Set Test Value</button>
  </div>
</template>

<script>
import Web3 from 'web3';

export default {
  data() {
    return {
      contractABI: [
        {
          "inputs": [
            {
              "internalType": "string",
              "name": "blocName",
              "type": "string"
            },
            {
              "internalType": "string",
              "name": "blocSHA",
              "type": "string"
            },
            {
              "internalType": "address",
              "name": "ownewer",
              "type": "address"
            }
          ],
          "name": "addNewBlock",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "string",
              "name": "name",
              "type": "string"
            },
            {
              "internalType": "string",
              "name": "sha",
              "type": "string"
            }
          ],
          "name": "BlocAlreadyExists",
          "type": "error"
        },
        {
          "inputs": [
            {
              "internalType": "string",
              "name": "name",
              "type": "string"
            }
          ],
          "name": "BlocDoesNotExist",
          "type": "error"
        },
        {
          "anonymous": false,
          "inputs": [
            {
              "indexed": false,
              "internalType": "string",
              "name": "name",
              "type": "string"
            },
            {
              "indexed": false,
              "internalType": "string",
              "name": "sha",
              "type": "string"
            },
            {
              "indexed": false,
              "internalType": "address",
              "name": "creator",
              "type": "address"
            },
            {
              "indexed": false,
              "internalType": "uint256",
              "name": "timestamp",
              "type": "uint256"
            }
          ],
          "name": "BlocAdded",
          "type": "event"
        },
        {
          "inputs": [
            {
              "internalType": "address",
              "name": "_address",
              "type": "address"
            }
          ],
          "name": "setDataContract",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "string",
              "name": "",
              "type": "string"
            }
          ],
          "name": "getBlocCreatorAddres",
          "outputs": [
            {
              "internalType": "address",
              "name": "",
              "type": "address"
            }
          ],
          "stateMutability": "view",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "string",
              "name": "blocName",
              "type": "string"
            }
          ],
          "name": "getBlockInfo",
          "outputs": [
            {
              "internalType": "string",
              "name": "",
              "type": "string"
            },
            {
              "internalType": "address",
              "name": "",
              "type": "address"
            },
            {
              "internalType": "uint256",
              "name": "",
              "type": "uint256"
            }
          ],
          "stateMutability": "view",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "string",
              "name": "",
              "type": "string"
            }
          ],
          "name": "getBlocSHA",
          "outputs": [
            {
              "internalType": "string",
              "name": "",
              "type": "string"
            }
          ],
          "stateMutability": "view",
          "type": "function"
        },
        {
          "inputs": [],
          "name": "getDataContractAddress",
          "outputs": [
            {
              "internalType": "address",
              "name": "",
              "type": "address"
            }
          ],
          "stateMutability": "view",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "string",
              "name": "",
              "type": "string"
            }
          ],
          "name": "getTimestamp",
          "outputs": [
            {
              "internalType": "uint256",
              "name": "",
              "type": "uint256"
            }
          ],
          "stateMutability": "view",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "string",
              "name": "blocName",
              "type": "string"
            },
            {
              "internalType": "string",
              "name": "blocSHA",
              "type": "string"
            }
          ],
          "name": "verifyBlock",
          "outputs": [
            {
              "internalType": "bool",
              "name": "",
              "type": "bool"
            }
          ],
          "stateMutability": "view",
          "type": "function"
        }
      ],
      contractAddress: "0x1737886a838384bc94b1603a87eCe78625d804F9",
      web3: new Web3(window.ethereum),
      contract: null,
      newValue: 0,
    };
  },
  created() {
    this.contract = new this.web3.eth.Contract(this.contractABI, this.contractAddress);
  },
  methods: {
    async getTestValue() {
      const value = await this.contract.methods.get().call();
      console.log("Test value: ", value);
    },
    async addNewBlock() {
      const accounts = await this.web3.eth.getAccounts();
      await this.contract.methods.addNewBlock('block1', 'sha1', accounts[0]).send({ from: accounts[0] });
    },

    async connectToMetaMask() {
      if (window.ethereum) {
        await window.ethereum.request({ method: 'eth_requestAccounts' });
      } else {
        alert("MetaMask is not installed. Please consider installing it: https://metamask.io/download.html");
      }
    },
  },
  mounted() {
    this.connectToMetaMask();
  },
};
</script>