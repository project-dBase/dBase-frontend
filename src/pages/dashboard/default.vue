<template>
    <div>
        <Breadcrumbs main="Dashboard" title="default" />

        <div class="container-fluid">
            <div class="row widget-grid">
                <WelcomeCard />
                <PurchaseSaleCard :puechase-sales-details1="puechaseSalesDetails" :puechase-sales-details2="puechaseSalesDetails2"/>
                <OrdersProfitCard />



              <div class="col-sm-6 col-md-3 mb-3">
                <div class="card text-center mb-0">
                  <div class="card-header b-l-primary mb-0">
                    <h6 class="mb-0">Rent your data</h6>
                  </div>
                  <div class="card-body f-light">
                    <p>Rent your data to other users and earn money!</p>
                    <button @click="search_open" class="btn btn-primary mx-auto">Look now</button>
                  </div>
                </div>
              </div>


              <div class="col-sm-6 col-md-3 mb-3">
                <div class="card text-center mb-0">
                  <div class="card-header b-l-primary mb-0">
                    <h6 class="mb-0">Sell your data</h6>
                  </div>
                  <div class="card-body f-light">
                    <p>Sell your data to other users!</p>
                    <button @click="search_open" class="btn btn-primary mx-auto">Look now</button>
                  </div>
                </div>
              </div>

              <div class="col-sm-6 col-md-3 mb-3">
                <div class="card text-center mb-0">
                  <div class="card-header b-l-primary mb-0">
                    <h6 class="mb-0">Verify your data</h6>
                  </div>
                  <div class="card-body f-light">
                    <p>Verify your data and stay safe!</p>
                    <button @click="search_open" class="btn btn-primary mx-auto">Look now</button>

                  </div>

                </div>
              </div>

              <div class="col-sm-6 col-md-3 mb-3">
                <div class="card text-center mb-0">
                  <div class="card-header b-l-primary mb-0">
                    <h6 class="mb-0">Get statistics</h6>
                  </div>
                  <div class="card-body f-light">
                    <p>Get needed statistics without knowing them!</p>
                    <button @click="search_open" class="btn btn-primary mx-auto">Look now</button>
                  </div>
                </div>
              </div>

<div class="mt-4"></div>


              <v-container align="center" class="mt-10">
                <v-card-title cols="12" class="ma-3" style="display: block">Verify your data, try it now!</v-card-title>
                <v-row>
                  <v-col cols="12" md="6" class="mx-auto">
                    <v-card :style="{ 'border': '5px solid #4C7987', 'border-radius': '20px', 'background-color': 'rgba(160, 162, 177, 0.45)', 'flex-direction': 'column', 'margin': 'auto' }">
                      <v-card-text >
                        <!-- Block Name Input -->
                        <v-card-title style="color: #D7C3CE;">Playground</v-card-title>
                        <v-text-field v-model="blockName" label="Input block name" style="color: #D7C3CE;"></v-text-field>
                        <v-text-field v-model="sha" label="Input hash" style="color: #D7C3CE;"></v-text-field>

                        <!-- Key-Value Inputs -->


                        <!-- Add Button -->
                        <v-btn @click="submit" color="#4C7987" class="ma-2" style="color: #D7C3CE;">Submit</v-btn>
                      </v-card-text>
                    </v-card>
                  </v-col>
                </v-row>
              </v-container>

            </div>
        </div>
    </div>

</template>

<script>
import WelcomeCard from "./default/WelcomeCard.vue";
import PurchaseSaleCard from "./default/PurchaseSaleCard.vue";
import OrdersProfitCard from "./default/OrdersProfitCard.vue";
import OverallBalanceCard from "./default/OverallBalanceCard.vue";
import RecentOrdersCard from "./default/RecentOrdersCard.vue";
import ActivitiesCard from "./default/ActivitiesCard.vue";
import RecentSalesCard from "./default/RecentSalesCard.vue";
import TimelineCard from "./default/TimelineCard.vue";
import ProAccountCard from "./default/ProAccountCard.vue";
import TotalUsersGrowthCard from "./default/TotalUsersGrowthCard.vue";
import PaperNoteCard from "./default/PaperNoteCard.vue";
import CreativeCard from "../../pages/advance/creativeCard/creative_card.vue"
//import CreativeCard from '.../pages/advance/creativeCard/creative_card.vue'
import FourCard from "@/pages/widgets/general/fourCard.vue";
import Web3 from "web3";
export default {
    components: {
        WelcomeCard,
        PurchaseSaleCard,
        OrdersProfitCard,
        OverallBalanceCard,
        RecentOrdersCard,
        ActivitiesCard,
        RecentSalesCard,
        TimelineCard,
        ProAccountCard,
        TotalUsersGrowthCard,
        PaperNoteCard,
        CreativeCard,
      FourCard
    },
    data() {
        return {
          puechaseSalesDetails: [{
            widgetClass: "widget-round secondary",
            svgIcon1: "cart",
            svgIcon2: "halfcircle",
            number: "",
            title: "Stored blocks",
            growthClass: "font-secondary f-w-500",
          },
            {
              widgetClass: "widget-round primary",
              svgIcon1: "tag",
              svgIcon2: "halfcircle",
              number: "",
              title: "Acessed blocks",
              growthClass: "font-primary f-w-500",

            },

          ],
          puechaseSalesDetails2:[{
            widgetClass: "widget-round warning",
            svgIcon1: "return-box",
            svgIcon2: "halfcircle",
            number: "",
            title: "Stored functions",
            growthClass: "font-warning f-w-500",

          },
            {
              widgetClass: "widget-round success",
              svgIcon1: "rate",
              svgIcon2: "halfcircle",
              number: "",
              title: "Network nodes",
              growthClass: "font-success f-w-500",

            }
          ],
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
          contractABI2: [
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
              "inputs": [
                {
                  "internalType": "uint256",
                  "name": "_index",
                  "type": "uint256"
                }
              ],
              "name": "getNodeDetails",
              "outputs": [
                {
                  "components": [
                    {
                      "internalType": "string",
                      "name": "httpsEndpoint",
                      "type": "string"
                    },
                    {
                      "internalType": "address",
                      "name": "ownerAddres",
                      "type": "address"
                    },
                    {
                      "internalType": "bool",
                      "name": "isActive",
                      "type": "bool"
                    },
                    {
                      "internalType": "uint256",
                      "name": "nodeID",
                      "type": "uint256"
                    },
                    {
                      "internalType": "uint256",
                      "name": "stakedAmount",
                      "type": "uint256"
                    },
                    {
                      "internalType": "uint256",
                      "name": "fufilledRequest",
                      "type": "uint256"
                    },
                    {
                      "internalType": "uint256",
                      "name": "totalRequests",
                      "type": "uint256"
                    },
                    {
                      "internalType": "uint256",
                      "name": "rewardedAmount",
                      "type": "uint256"
                    }
                  ],
                  "internalType": "struct BaseNode.Node",
                  "name": "",
                  "type": "tuple"
                }
              ],
              "stateMutability": "view",
              "type": "function"
            },
            {
              "inputs": [],
              "name": "getNodesLenght",
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
              "name": "updateDBaseTokenAddress",
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
            }
          ]
          ,
          contractAddress2:'0x34E1e6f8beA0c678f4b6a58464b64cd8e199B1E2',
          web3: new Web3(window.ethereum),
          contract: null,
          contract2: null,
          newValue: 0,
        };
    },

  created() {
    this.contract = new this.web3.eth.Contract(this.contractABI, this.contractAddress);
    this.contract2 = new this.web3.eth.Contract(this.contractABI2, this.contractAddress2);
  },
  methods: {
       async submit() {
         try{
           const value = await this.contract.methods.verifyBlock(this.blockName, this.sha).call();
           if(value===true ){
             alert("Block Verified and true")
           }else{
             alert("Block not Verified and false")
           }
         }
         catch(err){
           alert("Block not Verified and false")
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
