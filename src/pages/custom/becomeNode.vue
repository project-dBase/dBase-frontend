<template>
  <div class="gradientCircle">
    <v-container align="center" class="mt-10">
      <v-card-title cols="12" class="ma-3" style="display: block">Become a Node!</v-card-title>
      <v-row>
        <v-col cols="1"></v-col>
        <v-col cols="12" md="6" class="mx-auto">
          <v-card :style="{ 'border': '5px solid #7066f6', 'border-radius': '20px', 'background-color': 'rgba(160, 162, 177, 0.45)', 'flex-direction': 'column', 'margin': 'auto' }">
            <v-card-text >
              <v-card-title style="color: #D7C3CE;">Become a Node</v-card-title>
              <v-row>
                <v-col cols="12">
                  <v-text-field v-model="nodeEndpoint" label="Input your endpoint" style="color: #D7C3CE;"></v-text-field>
                </v-col>
              </v-row>
              <v-btn @click="submitt" color="#7066f6" class="ma-2" style="color: #D7C3CE;">Submit</v-btn>
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
  name: 'becomeNode',

  data() {
    return {
      scrollPosition: 0,
      nodeEndpoint: '',
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
              "internalType": "uint256",
              "name": "_nodeID",
              "type": "uint256"
            }
          ],
          "name": "collectReward",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "uint256",
              "name": "_nodeID",
              "type": "uint256"
            }
          ],
          "name": "collectRewardAndUnstake",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "uint256",
              "name": "_nodeID",
              "type": "uint256"
            }
          ],
          "name": "deactivateNode",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "uint256",
              "name": "_nodeID",
              "type": "uint256"
            }
          ],
          "name": "deactivateNodeAutomaticly",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "string",
              "name": "_httpsEndpoint",
              "type": "string"
            }
          ],
          "name": "registerAsNode",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [],
          "stateMutability": "nonpayable",
          "type": "constructor"
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
          "inputs": [
            {
              "internalType": "uint256",
              "name": "_minimumStake",
              "type": "uint256"
            }
          ],
          "name": "setMinimumStake",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "uint256",
              "name": "_rewardMultiplayer",
              "type": "uint256"
            }
          ],
          "name": "setrewardMultiplayer",
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
              "name": "_newTokenAddress",
              "type": "address"
            }
          ],
          "name": "updateDataAgregationContractAddress",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "address",
              "name": "_newTokenAddress",
              "type": "address"
            }
          ],
          "name": "updateDBaseTokenAddress",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "uint256",
              "name": "_nodeID",
              "type": "uint256"
            }
          ],
          "name": "updateFuffilledRequest",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "uint256",
              "name": "_nodeID",
              "type": "uint256"
            },
            {
              "internalType": "string",
              "name": "_httpsEndpoint",
              "type": "string"
            }
          ],
          "name": "updateHttpsEndpoint",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "uint256",
              "name": "_nodeID",
              "type": "uint256"
            }
          ],
          "name": "updateTotalRequests",
          "outputs": [],
          "stateMutability": "nonpayable",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "uint256",
              "name": "_nodeID",
              "type": "uint256"
            }
          ],
          "name": "chackReward",
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
              "internalType": "uint256",
              "name": "_nodeID",
              "type": "uint256"
            }
          ],
          "name": "checkActivity",
          "outputs": [
            {
              "internalType": "bool",
              "name": "",
              "type": "bool"
            }
          ],
          "stateMutability": "view",
          "type": "function"
        },
        {
          "inputs": [
            {
              "internalType": "uint256",
              "name": "_nodeID",
              "type": "uint256"
            }
          ],
          "name": "checkHttpsEndpoint",
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
          "inputs": [
            {
              "internalType": "address",
              "name": "_adress",
              "type": "address"
            }
          ],
          "name": "checkMyNodeID",
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
              "internalType": "uint256",
              "name": "_nodeID",
              "type": "uint256"
            }
          ],
          "name": "checkNumberOfFufilledRequests",
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
              "internalType": "uint256",
              "name": "_nodeID",
              "type": "uint256"
            }
          ],
          "name": "checkOwner",
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
              "internalType": "uint256",
              "name": "_nodeID",
              "type": "uint256"
            }
          ],
          "name": "checkStake",
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
          "inputs": [],
          "name": "dBaseToken",
          "outputs": [
            {
              "internalType": "contract ERC20",
              "name": "",
              "type": "address"
            }
          ],
          "stateMutability": "view",
          "type": "function"
        },
        {
          "inputs": [],
          "name": "getDataAgregationContractAddress",
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
          "name": "getDBaseTokenAddress",
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
          "name": "getRandomNode",
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
      contractAddress: "0x8C2e539c53AF937f64B27ab3B43ffc22F00e7919",
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

        const value = await this.contract.methods.registerAsNode(this.nodeEndpoint).send({from: window.ethereum.selectedAddress});


        console.log(value);

      }catch (e) {
        alert(e)
      }
    },





  },
};
</script>

<style scoped>
.gradientCircle {
  background: radial-gradient(circle at center, #4A4A9E,#252E48 , #1A262D, #1A262D);
  color: #D7C3CE;
  min-height: 100vh;
}

</style>
