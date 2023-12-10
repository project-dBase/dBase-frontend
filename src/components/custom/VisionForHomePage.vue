<template>
  <v-card-title class="ma-3">Our vision!</v-card-title>
  <v-container cols="12" align="center">
    <!-- Prvi red -->
    <v-row justify="center" align="center">
      <v-col cols="12" md="5" style="color: #4C7987;text-align: left;">
        <div>
          <p>
            In the quest for secure and transparent data management, dBase emerges as a reliable solution. If
            safeguarding your data against unauthorized modifications is a priority, and you seek comprehensive
            visibility into all alterations made to your dataset, consider verifying your database through the dBase
            platform. With a commitment to data integrity, dBase offers robust tools to authenticate and monitor
            changes, providing you with peace of mind and control over your information. The platform not only assures
            protection against unauthorized modifications but also allows you to trace and review every change made to
            your dataset. Empower your data management practices by choosing dBase for a secure and transparent database
            verification experience.
          </p>
        </div>
      </v-col>

      <v-col cols="12" md="3" class="d-flex justify-center">
        <div style="height: 200px; width: 200px; border: 10px solid #4C7987;border-radius: 100px; overflow: hidden">
          <v-img :src="security"></v-img>
        </div>
      </v-col>


    </v-row>

    <!-- Drugi red -->
    <v-row justify="center" align="center" v-if="screenWidth >= 960">


      <v-col cols="12" md="3" class="d-flex justify-center">
        <div
            style="height: 200px; width: 200px; border: 10px solid #D7C3CE; border-radius: 100px; overflow: hidden; position: relative;"
        >
          <v-img :src="data" cover></v-img>
        </div>
      </v-col>
      <v-col cols="12" md="5" style="color: #D7C3CE; text-align: right;">
        <div>
          <p>
            Are you in search of data that goes beyond what is readily available on the internet? Look no further – we
            offer solutions tailored to your needs. Whether it's a temporary requirement or a long-term necessity, you
            have the flexibility to either rent the data for a specific period or secure lifetime access through a
            purchase. Our platform, dBase, provides a comprehensive repository of data, ensuring that you can access the
            information crucial to your projects. With a user-friendly interface and a diverse range of datasets, dBase
            stands as your go-to source for acquiring valuable and unique data. Empower your endeavors with the right
            information – explore the possibilities with dBase today!

          </p>
        </div>
      </v-col>
    </v-row>
    <v-row justify="center" align="center" v-else>
      <v-col cols="12" md="5" style="color: #D7C3CE; text-align: right;">
        <div>
          <p>
            Are you in search of data that goes beyond what is readily available on the internet? Look no further – we
            offer solutions tailored to your needs. Whether it's a temporary requirement or a long-term necessity, you
            have the flexibility to either rent the data for a specific period or secure lifetime access through a
            purchase. Our platform, dBase, provides a comprehensive repository of data, ensuring that you can access the
            information crucial to your projects. With a user-friendly interface and a diverse range of datasets, dBase
            stands as your go-to source for acquiring valuable and unique data. Empower your endeavors with the right
            information – explore the possibilities with dBase today!

          </p>
        </div>
      </v-col>

      <v-col cols="12" md="3" class="d-flex justify-center">
        <div
            style="height: 200px; width: 200px; border: 10px solid #D7C3CE; border-radius: 100px; overflow: hidden; position: relative;"
        >
          <v-img :src="data" cover></v-img>
        </div>
      </v-col>
    </v-row>

    <!-- Treći red -->
    <v-row justify="center" align="center">
      <v-col cols="12" md="5" style="color: #86899F;text-align: left;">
        <div>
          <p>

            Unlock valuable insights without revealing the intricacies of your data. Our service enables you to sell
            your data for statistical purposes, ensuring the privacy and confidentiality of your information. With this
            innovative approach, users gain access to comprehensive statistics derived from your data without having the
            ability to read the raw data itself. This safeguards sensitive details while still allowing organizations
            and researchers to derive meaningful insights. Whether you're a business looking to monetize your data or an
            individual interested in contributing to broader statistical analyses, our platform provides a secure and
            mutually beneficial solution. Embrace the power of data-driven decision-making without compromising data
            privacy.
          </p>
        </div>
      </v-col>

      <v-col cols="12" md="3" class="d-flex justify-center">
        <div style="height: 200px; width: 200px; border: 10px solid #86899F;border-radius: 100px; overflow: hidden">
          <v-img :src="statistics" cover></v-img>
        </div>
      </v-col>


    </v-row>
  </v-container>
</template>

<script>
import security from '../../../public/security.png'
import statistics from '../../../public/statistics.png'
import data from '../../../public/data.png'

export default {
  name: "VisionForHomePage",
  methods: {
    handleResize() {
      this.screenWidth = window.innerWidth;
    }
  }, data() {
    return {
      screenWidth: window.innerWidth,
      security,
      statistics,
      data
    }
  },
  created() {
    window.addEventListener('resize', this.handleResize);
  },
  destroyed() {
    window.removeEventListener('resize', this.handleResize);
  }
};
</script>

<style scoped>
</style>