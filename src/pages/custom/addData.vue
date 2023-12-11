<template>
  <div class="gradientCircle">


    <v-container align="center" class="mt-10">
        <v-card-title cols="12" class="ma-3" style="display: block">Add your data, try it now!</v-card-title>
      <v-row>
        <v-col cols="12" md="6" class="mx-auto">
          <v-card :style="{ 'border': '5px solid #D7C3CE', 'border-radius': '20px', 'background-color': 'rgba(160, 162, 177, 0.45)', 'flex-direction': 'column', 'margin': 'auto' }">
            <v-card-text >
              <!-- Block Name Input -->
              <v-card-title style="color: #D7C3CE;">Playground</v-card-title>
              <v-text-field v-model="blockName" label="Input block name" style="color: #D7C3CE;"></v-text-field>

              <!-- Key-Value Inputs -->
              <v-row v-for="(item, index) in items" :key="index">
                <v-col cols="5">
                  <v-text-field v-model="item.key" label="Key" style="color: #D7C3CE;"  ></v-text-field>
                </v-col>
                <v-col cols="5">
                  <v-text-field v-model="item.value" label="Value" style="color: #D7C3CE;"></v-text-field>
                </v-col>
                <v-col cols="2">
                  <v-btn @click="removeItem(index)" x-small class="mt-2" color="#1A262D" style="border: 1px solid #D7C3CE; border-radius: 35%; min-width: 14px; min-height: 14px;color: #D7C3CE">
                    -
                  </v-btn>
                </v-col>
              </v-row>

              <!-- Add Button -->
              <v-btn @click="addItem" color="#D7C3CE" class="ma-2" style="min-width: 14px; color:#1A262D">+</v-btn>
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
  name: 'AddData',

  data() {
    return {
      scrollPosition: 0,
      blockName: '',
      items: [{ key: '', value: '' }],

      contractABI: [
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
          "name": "newBlockAdded",
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
              "name": "blockName",
              "type": "string"
            },
            {
              "internalType": "string",
              "name": "jsonData",
              "type": "string"
            },
            {
              "internalType": "string",
              "name": "baseURL",
              "type": "string"
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
              "internalType": "string",
              "name": "_code",
              "type": "string"
            }
          ],
          "name": "updateCode",
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
          "name": "aaaaa",
          "outputs": [
            {
              "internalType": "uint256",
              "name": "id",
              "type": "uint256"
            },
            {
              "internalType": "string",
              "name": "blockName",
              "type": "string"
            },
            {
              "internalType": "string",
              "name": "jsonData",
              "type": "string"
            },
            {
              "internalType": "string",
              "name": "baseURL",
              "type": "string"
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

      contractAddress: "0x3A3a25d8F19419a8A323F252b6C5b44579DF7816",
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
        let json = this.items.reduce((obj, item) => {
          obj[item.key] = item.value;
          return obj;
        }, {});
        json = JSON.stringify(json);
        var tekstSaJednostrukim = json.replace(/"/g, "'");
        console.log("" + tekstSaJednostrukim);
        tekstSaJednostrukim = "'field:'" + tekstSaJednostrukim + "'";

        console.log(typeof tekstSaJednostrukim);

        // Add this line to enable MetaMask
        await window.ethereum.enable();

        const value = await this.contract.methods.sendRequest(1072, this.blockName,""+ tekstSaJednostrukim, 'http://178.79.181.117:80/api/collections/bloc/records').send({from: window.ethereum.selectedAddress});

        console.log(value);
        console.log(this.blockName);
      }catch (e) {
        alert(e)
      }
    },


    addItem() {
      this.items.push({ key: '', value: '' });
    },

    removeItem(index) {
      this.items.splice(index, 1);
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
