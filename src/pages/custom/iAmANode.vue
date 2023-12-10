<template>
  <div class="gradientCircle">


    <v-container align="center" class="mt-10">
      <v-card-title cols="12" class="ma-3" style="display: block">I am Node!</v-card-title>
      <v-row>

        <IAmNodeCards :puechase-sales-details="puechaseSalesDetails1"/>
      </v-row>
      <v-card-title cols="12" class="ma-3" style="display: block">Controll</v-card-title>
      <v-row>
        <v-col cols="12" sm="6" md="4" lg="3" xl="2" v-for="(button, index) in buttons" :key="index">
          <div class="d-flex justify-center align-center" style="height: 100px">
            <v-btn :color="button.color" @click="button.onClick">
              {{ button.title }}
            </v-btn>
          </div>
        </v-col>
      </v-row>

    </v-container>
    <v-dialog v-model="showCard" max-width="500px">
      <v-card style="border: 4px solid #7066f6; border-radius: 20px; background-color: rgba(91,96,110,255);">
        <v-card-title>Unesite podatke</v-card-title>
        <v-card-text>
          <!-- Input polje -->
          <v-text-field v-model="inputValue" label="Unesite nešto"></v-text-field>
        </v-card-text>
        <v-card-actions>
          <!-- Gumbi "Save" i "Cancel" -->
          <v-btn @click="cancel">Cancel</v-btn>
          <v-spacer></v-spacer>
          <v-btn @click="updateHttps">Save</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import Web3 from 'web3';
import IAmNodeCards from "@/pages/dashboard/default/iAmNodeCards.vue";

export default {
  name: 'iAmANode',
  components: {
    IAmNodeCards,
  },

  data() {
    return {
      inputValue: '',

      buttons: [
        {
          title: 'Collect reward',
          color: '#7066f6',
          onClick: this.collectReward
        },
        {
          title: 'Collect reward and unstake',
          color: '#7066f6',
          onClick: this.collectAndUnstake
        }, {
          title: 'Deactivate node',
          color: '#7066f6',
          onClick: this.deactivateNode
        },
        {
          title: 'Update http endpoint',
          color: '#7066f6',
          onClick: this.updateEndpoint
        },

      ],
      scrollPosition: 0,
      nodeEndpoint: '',
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
      contractAddress: "0xc4e887206748B187B7756F3AE34f15De6213f541",
      web3: new Web3(window.ethereum),
      contract: null,
      newValue: 0,


      puechaseSalesDetails1: [{
        widgetClass: "widget-round secondary",
        svgIcon1: "cart",
        svgIcon2: "halfcircle",
        number: "",
        title: "Earned",
        growthClass: "font-secondary f-w-500",
      },
        {
          widgetClass: "widget-round primary",
          svgIcon1: "tag",
          svgIcon2: "halfcircle",
          number: "",
          title: "Fufilled requests",
          growthClass: "font-primary f-w-500",

        },
        {
          widgetClass: "widget-round warning",
          svgIcon1: "return-box",
          svgIcon2: "halfcircle",
          number: "",
          title: "Stake",
          growthClass: "font-warning f-w-500",

        },
        {
          widgetClass: "widget-round success",
          svgIcon1: "rate",
          svgIcon2: "halfcircle",
          number: "",
          title: "Http -endpoint",
          growthClass: "font-success f-w-500",

        }
      ],
      showCard: false,
    };
  },
  created() {
    this.contract = new this.web3.eth.Contract(this.contractABI, this.contractAddress);
    this.checkIfMetaMaskConnected();

  },
  watch: {
    newValue(newVal, oldVal) {
      this.setData(newVal);
    },
  },
  methods: {
    async setData() {
      console.log(this.newValue);

      this.puechaseSalesDetails1[0].number = await this.contract.methods.chackReward(this.newValue).call();
      console.log(this.newValue);

      this.puechaseSalesDetails1[1].number = await this.contract.methods.checkNumberOfFufilledRequests(this.newValue).call();
      console.log(this.newValue);

      this.puechaseSalesDetails1[2].number = await this.contract.methods.checkStake(this.newValue).call();
      console.log(this.newValue);

      this.puechaseSalesDetails1[3].number = await this.contract.methods.checkHttpsEndpoint(this.newValue).call();

    },
    async checkIfMetaMaskConnected() {
      if (window.ethereum) {
        try {

          if (window.ethereum.selectedAddress) {
            await this.checkMyNode();
          } else {
            console.error('Korisnik nije prijavljen na MetaMask.');
          }
        } catch (error) {
          console.error('Pogreška prilikom provjere povezanosti s MetaMaskom:', error);
        }
      } else {
        console.error('MetaMask nije dostupan.');
      }
    },

    async checkMyNode() {

      const value = await this.contract.methods.checkMyNodeID(window.ethereum.selectedAddress).call();
      this.newValue = value;
      return value;
    },

    async collectReward() {
      await window.ethereum.enable();

      const value = await this.contract.methods.collectReward(this.newValue).send({from: window.ethereum.selectedAddress});

      console.log(value);
    },
    async collectAndUnstake() {
      await window.ethereum.enable();

      const value = await this.contract.methods.collectRewardAndUnstake(this.newValue).send({from: window.ethereum.selectedAddress});

      console.log(value);
    },
    async deactivateNode() {
      await window.ethereum.enable();

      const value = await this.contract.methods.deactivateNode(this.newValue).send({from: window.ethereum.selectedAddress});

      console.log(value);

    },
    async updateEndpoint() {
      this.showCard = true;

    },
    async updateHttps() {

      await window.ethereum.enable();

      const value = await this.contract.methods.updateHttpsEndpoint(this.newValue, this.inputValue).send({from: window.ethereum.selectedAddress});

      console.log(value);
      this.showCard = false;
    }, cancel() {
      this.showCard = false;
    }


  },
};
</script>

<style scoped>
.gradientCircle {
  background: radial-gradient(circle at center, #4A4A9E, #252E48, #1A262D, #1A262D);
  color: #D7C3CE;
  min-height: 100vh;
}

</style>
