<template>
  <v-card-title class="ma-3">About Us!</v-card-title>

  <v-row justify="center" align="center">
    <v-col cols="12" md="4">
      <v-row>
        <v-col cols="12" class="d-flex justify-center">
          <div
              style="height: 250px; width: 250px; border: 10px solid #4C7987; border-radius: 130px; overflow: hidden; position: relative;"
          >
            <v-img :src="blaz" cover></v-img>
          </div>
        </v-col>
        <v-col cols="12" class="text-center" style="color: #4C7987;">
          <b>Blaž Perić</b>
        </v-col>
        <v-col cols="12">
          <div style="text-align: justify;">
            <p>
              I am a 19-year-old student currently pursuing a degree in Computer Science at the University of Mostar. I have been involved in programming since my early years, primarily focusing on Flutter. Recently, I have delved into blockchain and web 3 technologies, finding great enthusiasm for their potential. While this project excites me for its innovative aspects, it is not my first venture. I have garnered recognition through numerous awards, triumphing in both hackathons and startup competitions. A notable achievement includes winning the STUp international startup competition.

              Through my participation in various competitions and hackathons, I gained a holistic perspective. Despite being primarily a programmer, these experiences enabled me to explore fields such as economics and management. At the age of 18, I proudly initiated my own startup, SmartNest.   </p>
          </div>
        </v-col>
      </v-row>
    </v-col>

    <v-col cols="12" md="4">
      <v-row>
        <v-col cols="12" class="d-flex justify-center">
          <div
              style="height: 250px; width: 250px; border: 10px solid #D7C3CE; border-radius: 130px; overflow: hidden; position: relative;"
          >
            <v-img :src="andjela" cover></v-img>
          </div>
        </v-col>
        <v-col cols="12" class="text-center" style="color: #D7C3CE;">
          <b>Anđela Jurić</b>
        </v-col>
        <v-col cols="12">
          <div style="text-align: justify;">
            <p>

              I am a 21-year-old computer engineering bachelor currently pursuing my master's degree in computer engineering at the Faculty of Mechanical Engineering, Computing, and Electrical Engineering at the University of Mostar. My journey into the world of programming began at the age of 17, and my passion for it has only grown since. Currently, I am actively involved in significant projects at SUMIT, the university's IT center, and I hold the role of a demonstrator at the faculty.

              Along my academic path, I've achieved notable recognition, having been honored with two Dean's awards for academic excellence and the Rector's award for academic excellence. Beyond the classroom, I am dedicated to continuous learning and have completed numerous courses in the IT field. These include Programming 1, 2, 3, HTML-CSS, WordPress, QA testing, Angular, Database 1, 2, Web Programming, and others.
            </p>
          </div>
        </v-col>
      </v-row>
    </v-col>
  </v-row>
</template>

<script>
import blaz from '../../../public/blaz.jpeg'
import andjela from '../../../public/andjela.jpg'
export default {
  name: "AboutUs",
  data() {
    return {
      blaz,
      andjela
    }
  }
};
</script>

<style scoped>
</style>