<template>
  <div class="gradientCircle">


    <v-container align="center" class="mt-10">
      <v-card-title cols="12" class="ma-3" style="display: block">Read data!</v-card-title>
      <v-row>
        <v-col cols="12" md="6" class="mx-auto">
          <v-card :style="{ 'border': '5px solid #D7C3CE', 'border-radius': '20px', 'background-color': 'rgba(160, 162, 177, 0.45)', 'flex-direction': 'column', 'margin': 'auto' }">
            <v-card-text >
              <v-card-title style="color: #D7C3CE;">Read data</v-card-title>
<v-row>
  <v-col cols="6">
    <v-text-field v-model="blockName" label="Input block name" style="color: #D7C3CE;"></v-text-field>
  </v-col>
  <v-col cols="6">
    <v-text-field v-model="keyVal" label="Key" style="color: #D7C3CE;"  ></v-text-field>
  </v-col>

</v-row>




              <!-- Add Button -->
              <v-btn @click="submitt" color="#D7C3CE" class="ma-2" style="color: #1A262D;">Submit</v-btn>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import Web3 from 'web3';

export default {
  name: 'ReadData',

  data() {
    return {
      scrollPosition: 0,
      blockName: '',
     keyVal: '',

      contractABI:[
        {
          "inputs": [],
          "name": "acceptOwnership",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "string",
              "name": "_code",
              "type": "string"
            }
          ],
          "stateMutability": "nonpayable",
          "type": "constructor"
        },
        {
          "inputs": [],
          "name": "EmptyArgs",
          "type": "error"
        },
        {
          "inputs": [],
          "name": "EmptySource",
          "type": "error"
        },
        {
          "inputs": [
            {
              "internalType": "string",
              "name": "fieldToSearch",
              "type": "string"
            },
            {
              "internalType": "string",
              "name": "blockName",
              "type": "string"
            },
            {
              "internalType": "address",
              "name": "contractAddress",
              "type": "address"
            }
          ],
          "name": "getDataSafeToContract",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "bytes32",
              "name": "requestId",
              "type": "bytes32"
            },
            {
              "internalType": "bytes",
              "name": "response",
              "type": "bytes"
            },
            {
              "internalType": "bytes",
              "name": "err",
              "type": "bytes"
            }
          ],
          "name": "handleOracleFulfillment",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [],
          "name": "NoInlineSecrets",
          "type": "error"
        },
        {
          "inputs": [],
          "name": "OnlyRouterCanFulfill",
          "type": "error"
        },
        {
          "anonymous": false,
          "inputs": [
            {
              "indexed": true,
              "internalType": "address",
              "name": "from",
              "type": "address"
            },
            {
              "indexed": true,
              "internalType": "address",
              "name": "to",
              "type": "address"
            }
          ],
          "name": "OwnershipTransferRequested",
          "type": "event"
        },
        {
          "anonymous": false,
          "inputs": [
            {
              "indexed": true,
              "internalType": "address",
              "name": "from",
              "type": "address"
            },
            {
              "indexed": true,
              "internalType": "address",
              "name": "to",
              "type": "address"
            }
          ],
          "name": "OwnershipTransferred",
          "type": "event"
        },
        {
          "anonymous": false,
          "inputs": [
            {
              "indexed": true,
              "internalType": "bytes32",
              "name": "id",
              "type": "bytes32"
            }
          ],
          "name": "RequestFulfilled",
          "type": "event"
        },
        {
          "anonymous": false,
          "inputs": [
            {
              "indexed": true,
              "internalType": "bytes32",
              "name": "id",
              "type": "bytes32"
            }
          ],
          "name": "RequestSent",
          "type": "event"
        },
        {
          "anonymous": false,
          "inputs": [
            {
              "indexed": false,
              "internalType": "bytes32",
              "name": "requestId",
              "type": "bytes32"
            },
            {
              "indexed": false,
              "internalType": "bytes",
              "name": "response",
              "type": "bytes"
            },
            {
              "indexed": false,
              "internalType": "bytes",
              "name": "err",
              "type": "bytes"
            }
          ],
          "name": "newBlockReaded",
          "type": "event"
        },
        {
          "inputs": [
            {
              "internalType": "uint64",
              "name": "subscriptionId",
              "type": "uint64"
            },
            {
              "internalType": "string",
              "name": "fieldToSearch",
              "type": "string"
            },
            {
              "internalType": "string",
              "name": "blockName",
              "type": "string"
            },
            {
              "internalType": "string",
              "name": "baseURL",
              "type": "string"
            },
            {
              "internalType": "address",
              "name": "contractAddress",
              "type": "address"
            },
            {
              "internalType": "uint256",
              "name": "nodeId",
              "type": "uint256"
            }
          ],
          "name": "sendRequest",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "address",
              "name": "to",
              "type": "address"
            }
          ],
          "name": "transferOwnership",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "address",
              "name": "newAddress",
              "type": "address"
            }
          ],
          "name": "updateBaseOperatorsAddress",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "address",
              "name": "newAddress",
              "type": "address"
            }
          ],
          "name": "updateDataStorageAddress",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "uint32",
              "name": "newGasLimit",
              "type": "uint32"
            }
          ],
          "name": "updateGasLimit",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "address",
              "name": "newAddress",
              "type": "address"
            }
          ],
          "name": "updateTokenContractAddress",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [],
          "name": "getBaseOperatorsAddress",
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
          "inputs": [],
          "name": "getCode",
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
          "name": "getDataStorageAddress",
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
          "inputs": [],
          "name": "getDonID",
          "outputs": [
            {
              "internalType": "bytes32",
              "name": "",
              "type": "bytes32"
            }
          ],
          "stateMutability": "view",
          "type": "function"
        },
        {
          "inputs": [],
          "name": "getGasLimit",
          "outputs": [
            {
              "internalType": "uint32",
              "name": "",
              "type": "uint32"
            }
          ],
          "stateMutability": "view",
          "type": "function"
        },
        {
          "inputs": [],
          "name": "getRouter",
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
          "inputs": [],
          "name": "getTokenContractAddress",
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
          "inputs": [],
          "name": "owner",
          "outputs": [
            {
              "internalType": "address",
              "name": "",
              "type": "address"
            }
          ],
          "stateMutability": "view",
          "type": "function"
        }
      ],
      contractAddress: "0xD9f0Fc9EFEbB71Ca5cDdED914C6B7a6079F4Ace6",
      web3: new Web3(window.ethereum),
      contract: null,
      newValue: 0,
    };
  },
  created() {
    this.contract = new this.web3.eth.Contract(this.contractABI, this.contractAddress);
  },
  methods: {
    async submitt() {
      try {

        // Add this line to enable MetaMask
        await window.ethereum.enable();

        const value = await this.contract.methods.sendRequest(1072, this.keyVal, this.blockName, 'http://178.79.181.117:80/api/collections/bloc/records', '0xC8fB30c47501EE3746528a7F77620491388ef766', 0).send({from: window.ethereum.selectedAddress});


        console.log(value);
        console.log(this.blockName);
      }catch (e) {
        alert(e)
      }
    },





  },
};
</script>

<style scoped>
.gradientCircle {
  background: radial-gradient(circle at center, #A599A3, #434850, #1A262D, #1A262D);
  color: #D7C3CE;
  min-height: 100vh;
}

</style>
