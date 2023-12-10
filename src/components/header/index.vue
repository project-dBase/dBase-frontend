<template>
  <div class="header-wrapper row m-0">
    <SearchBar />
    <Logo />
    <div class="left-header col-xxl-5 col-xl-6 col-lg-5 col-md-4 col-sm-3 p-0">
      <swiper
          :slidesPerView="1"
          :autoplay="{delay: 2500,disableOnInteraction: false}"
          :modules="modules"
          class="notification-slider"
          direction="vertical"
      >
        <swiper-slide class="h-100">
          <div class="d-flex hover-100" style=" height: 50px">
            <img src="@/assets/images/littleLogo.png" class="img-fluid full-cover" alt="gif" />
            <h6 class="mb-0 f-w-400">
              <span class="font-primary">Hackathon! This is not the final app for production</span>
            </h6>
            <i class="icon-arrow-top-right f-light"></i>
          </div>
        </swiper-slide>

      </swiper>
    </div>
    <div class="nav-right col-xxl-7 col-xl-6 col-md-7 col-8 pull-right right-header p-0 ms-auto">
      <ul class="nav-menus">
        <button
            v-if="!connected"
            @click="connect"
            class="btn btn-primary search-box ml-3 mr-3"
        >
          <i class="icon-plus"></i> Connect wallet
        </button>
        <p v-if="connected" class="text-success ml-3">Wallet connected!</p>
        <p v-if="errorConnecting" class="text-danger ml-3">{{ connectionErrorMessage }}</p>
      </ul>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
import Bookmark from "../bookmark";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay } from "swiper";
import "swiper/css";
import Language from "./language";
import Notifications from "./notifications.vue";
import Cart from "./cart";
import Profile from "./profile";
import Logo from "./logo.vue";
import SearchBar from "./search";
import Web3 from "web3";

export default {
  components: {
    Bookmark,
    Language,
    Notifications,
    Cart,
    Profile,
    Logo,
    Swiper,
    SwiperSlide,
    SearchBar,
  },
  mounted() {
    // this.initWeb3();
  },
  data() {
    return {
      bookmark: false,
      connected: false,
      errorConnecting: false,
      connectionErrorMessage: "",
      web3: null,
      accounts: [],
      contract: null,
    };
  },
  computed: {
    ...mapState({
      menuItems: (state) => state.menu.searchData,
      megamenuItems: (state) => state.menu.megamenu,
      searchOpen: (state) => state.menu.searchOpen,
    }),
  },
  methods: {
    async initWeb3() {
      if (window.ethereum) {
        this.web3 = new Web3(window.ethereum);
        try {
          await window.ethereum.enable();
          this.loadAccounts();
         // this.loadContract();
        } catch (error) {
          this.errorConnecting = true;
          this.connectionErrorMessage = "User denied account access";
          console.error(error);
        }
      } else if (window.web3) {
        this.web3 = new Web3(window.web3.currentProvider);
        this.loadAccounts();
       // this.loadContract();
      } else {
        this.errorConnecting = true;
        this.connectionErrorMessage =
            "Non-Ethereum browser detected. You should consider trying MetaMask!";
        console.error(
            "Non-Ethereum browser detected. You should consider trying MetaMask!"
        );
      }
    },
    connect: function () {
      if (window.ethereum) {
        if (window.ethereum.isConnected()) {
          this.connected = true;
          this.initWeb3();
        } else {
          window.ethereum
              .request({ method: "eth_requestAccounts" })
              .then(() => {
                this.connected = true;
                this.initWeb3();
              })
              .catch((error) => {
                this.errorConnecting = true;
                this.connectionErrorMessage = "Error connecting wallet";
                console.error(error);
              });
        }
      }
    },

    async loadAccounts() {
      this.accounts = await this.web3.eth.getAccounts();
      console.log("Account:", this.accounts[0]);
    },

    async callSmartContractFunction() {
      const functionName = "your_function_name";
      // const functionParams = [...]; // Set the function parameters
      const gasLimit = 200000; // Set the appropriate gas limit

      try {
        const result = await this.contract.methods[functionName](...functionParams).send({ from: this.accounts[0], gas: gasLimit });
        console.log("Transaction successful:", result);
      } catch (error) {
        console.error("Transaction failed:", error);
      }
    },
    async loadContract() {
      const contractAddress = "0xd20344c447ae183A1CC3368f8b2B6Ee08b1b36BE";

      this.contract = new this.web3.eth.Contract(contractABI, contractAddress);
      console.log(this.contract);
    },

    callContract() {
      let web3 = new Web3(window.ethereum);
      console.log(web3);
      let contractAddress = "0xd20344c447ae183A1CC3368f8b2B6Ee08b1b36BE";

      let contract = new web3.eth.Contract(abi, contractAddress);
      console.log(contract);
    },

    search_open() {
      this.$store.state.menu.searchOpen = true;
    },
    bookmark_open() {
      this.bookmark = !this.bookmark;
    },
  },
  setup() {
    return {
      modules: [Autoplay],
    };
  },
};
</script>
<style>
.full-cover {

 min-width: 50px;
  object-fit: contain;
  object-position: center;
}
</style>