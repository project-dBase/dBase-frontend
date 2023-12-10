<template>
  <div style="height: 300px"></div>
    <v-footer app fixed height="200"  v-if="showFooter" color="secondary">
      <v-footer-row class="flex-grow-1">
        <v-col class="text-right">
          <v-img
            src="@/public/logoFooter.png"
            alt="Veliki Logo"
            max-width="150"
            max-height="150"
          ></v-img>
        </v-col>
      </v-footer-row>


      <v-footer-row>
        <!-- Linkovi za društvene mreže s ikonama -->
        <v-col class="text-right">
          <v-btn icon color="primary" class="ma-1">
            <v-icon>mdi-instagram</v-icon>
          </v-btn >
          <v-btn icon color="primary" class="ma-1">
            <v-icon>mdi-twitter</v-icon>
          </v-btn>
          <v-btn icon color="primary" class="ma-1">
            <v-icon>mdi-facebook </v-icon>
          </v-btn>
        </v-col>
      </v-footer-row>
    </v-footer>
  </template>
  
  <script>
  export default {
    name: "AppFooter",
    data() {
      return {
        showFooter: false,
      };
    },
    mounted() {
      window.addEventListener("scroll", this.handleScroll);
    },
    destroyed() {
      window.removeEventListener("scroll", this.handleScroll);
    },
    methods: {
      handleScroll() {
        const scrollPosition = window.scrollY;
        const windowHeight = window.innerHeight;
        const bodyHeight = document.body.offsetHeight;
        this.showFooter = scrollPosition + windowHeight + 100 >= bodyHeight;
      },
    }
  }
  </script>
  
  <style scoped>
  .footer {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    opacity: 0;
    transition: opacity 0.5s;
  }

  .showFooter {
    opacity: 1;
  }
  </style>
  