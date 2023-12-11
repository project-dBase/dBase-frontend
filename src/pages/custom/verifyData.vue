<template>
  <div class="gradientCircle">
        <v-container align="center" class="mt-10">
          <v-card-title cols="12" class="ma-3" style="display: block">Verify your data, try it now!</v-card-title>
          <v-row>
            <v-col cols="12" md="6" class="mx-auto">
              <v-card :style="{ 'border': '5px solid #4C7987', 'border-radius': '20px', 'background-color': 'rgba(160, 162, 177, 0.45)', 'flex-direction': 'column', 'margin': 'auto' }">
                <v-card-text >
                  <v-card-title style="color: #D7C3CE;">Playground</v-card-title>
                  <v-text-field v-model="blockName" label="Input block name" style="color: #D7C3CE;"></v-text-field>
                  <v-text-field v-model="sha" label="Input hash" style="color: #D7C3CE;"></v-text-field>
                  <v-btn @click="submit" color="#4C7987" class="ma-2" style="color: #D7C3CE;">Submit</v-btn>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
  </div>
</template>

<script>
import CreativeCard from "../../pages/advance/creativeCard/creative_card.vue"
import FourCard from "@/pages/widgets/general/fourCard.vue";
import Web3 from "web3";
export default {
  name: "verifyData",
  components: {
    CreativeCard,
    FourCard
  },
  data() {
    return {
      blockName: '',
      sha:'',
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
    async submit() {
      try{
        const value = await this.contract.methods.verifyBlock(this.blockName, this.sha).call();
        if(value===true ){
          alert("Data is correct")
        }else{
          alert("Data is not correct")
        }
      }
      catch(err){
        alert("Data is not correct")
      }
    },
    async getData(){
      this.puechaseSalesDetails[0].number = await this.contract.methods.getNodesLenght(this.blockName).call();
      this.puechaseSalesDetails[1].number = await this.contract.methods.getTimestamp(this.blockName).call();
      this.puechaseSalesDetails2[0].number = await this.contract.methods.getTimestamp(this.blockName).call();
      this.puechaseSalesDetails2[1].number = await this.contract.methods.getTimestamp(this.blockName).call();
    }


  },
};
</script>
<style>
.gradientCircle {
  background: radial-gradient(circle at center, #406772, #23353D , #1A262D, #1A262D);
  color: #D7C3CE;
  min-height: 100vh;
}
</style>
