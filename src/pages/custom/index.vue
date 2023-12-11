<template>
  <div>
    <v-container align="center" class="mt-10">
      <v-card-title class="ma-3">Welcome to dBase!</v-card-title>


      <v-row>
        <v-col cols="12" md="4">
          <card-for-home-page
              :path="'/verifydata'"
              cardTitle="Verify your database"
              cardText="If you want to ensure that your data is not modified and you want to be able to see all modifications that were done to your dataset, verify your database at dBase."
              card_color="#4C7987"
              card_color_border="#D7C3CE"
          ></card-for-home-page>
        </v-col>

        <v-col cols="12" md="4">
          <card-for-home-page
              :path="'/readdata'"
              cardTitle="Get needed data"
              cardText="Do you need data that is not accessible on the net? You can rent data for some period of time or buy it so you have lifetime access - get needed data on dBase"
              card_color="#D7C3CE"
              card_color_border="#4C7987"
          ></card-for-home-page>
        </v-col>

        <v-col cols="12" md="4">
          <card-for-home-page
              :path="'/'"
              cardTitle="Get needed statistics"
              cardText="Get needed statistics without knowledge of the data. We offer you to sell your data for statistic, but the user cannot read your data - just see the statistic"
              card_color="#86899F"
              card_color_border="#D7C3CE"
          ></card-for-home-page>
        </v-col>
      </v-row>

      <vision-for-home-page></vision-for-home-page>
      <about-us></about-us>
    </v-container>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import CardForHomePage from "../../components/custom/cardForHomePage.vue";
import VisionForHomePage from "../../components/custom/VisionForHomePage.vue";
import AboutUs from "../../components/custom/AboutUs.vue";
import Web3 from 'web3';

export default defineComponent({
  name: "home",
  components: { AboutUs, VisionForHomePage, CardForHomePage },
  data() {
    return {
      connected: false,
      contractResult: null,
      web3: null,
      accounts: [],
      contract: null,
    };
  },
  mounted() {
  },
  methods: {

  },
});
</script>

<style>
</style>
