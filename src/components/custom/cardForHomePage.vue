<template>
  <div>
    <v-card :style="{ 'border': `4px solid ${card_color}`, 'border-radius': '20px', 'background-color': 'rgba(160, 162, 177, 0.45)' }">
      <v-card-title class="ma-5" style="color: #D7C3CE">
        {{ cardTitle }}
      </v-card-title>
      <v-card-text style="color: #D7C3CE">
        {{ cardText }}
      </v-card-text>
      <router-link  :to="{ path }">
        <v-btn class="ma-5"
               :color="card_color"
               :style="{ border: `2px ${card_color_border} solid` , 'color':`${card_color_border}`, width:'80%', 'border-radius': '13px' }">
          See more...
        </v-btn>
      </router-link>
    </v-card>

  </div>

</template>

<script>
export default {
  name: "cardForHomePage",
  props: {
    path: String,
    cardTitle: String,
    cardText: String,
    card_color: String,
    card_color_border: String,
  }
}
</script>

<style scoped>

</style>