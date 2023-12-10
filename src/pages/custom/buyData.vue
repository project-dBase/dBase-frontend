<template>
  <div class="gradientCircle">


    <v-container align="center" class="mt-10">

      <v-card-title cols="12" class="ma-3" style="display: block">You want to buy some data, try it now!</v-card-title>
      <v-row>
        <v-col cols="12" md="6" class="mx-auto">
          <v-card
              :style="{ 'border': '5px solid #D7C3CE', 'border-radius': '20px', 'background-color': 'rgba(160, 162, 177, 0.45)', 'flex-direction': 'column', 'margin': 'auto' }">
            <v-card-title style="color: #D7C3CE;">Playground</v-card-title>
            <v-card-text>
              <v-container>
                <v-row>
                  <v-col>
                    <v-select
                        color="#D7C3CE"
                        v-model="selectedItem"
                        :items="items"
                        label="Select item"
                        @change="updateAttributes"
                    ></v-select>
                  </v-col>
                </v-row>
                <v-row v-if="selectedItem">
                  <v-col v-for="(attribute, index) in attributes" :key="index" cols="6">
                    <v-text-field v-model="attribute.value" :label="attribute.label"
                                  style="color: #D7C3CE;" ></v-text-field>
                  </v-col>
                </v-row>
              </v-container>
              <v-btn @click="submitt" color="#D7C3CE" class="ma-2" style="color: #1A262D;">Get data!</v-btn>

            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'BuyData',

  data() {
    return {
      selectedItem: null,
      items: ['Voda', 'Vatra', 'Zemlja'],
      attributesData: {
        Voda: [
          {label: 'ph', value: ''},
          {label: 'temperatura', value: ''},
          {label: 'čistoća', value: ''},
          {label: 'gustoća', value: ''},
        ],
        Vatra: [
          {label: 'temperatura', value: ''},
          {label: 'boja plamena', value: ''}
        ],
        Zemlja: [
          {label: 'težina', value: ''},
          {label: 'boja tla', value: ''}
        ]
      },
      attributes: [],
    };
  },
  watch: {
    selectedItem() {
      this.updateAttributes();
    }
  },

  methods: {
    updateAttributes() {
      this.attributes = this.attributesData[this.selectedItem];
    },
    submitt() {
      this.attributes.forEach(attribute => {
        attribute.value = Math.random();
      });
    }
  },
};
</script>

<style scoped>
.gradientCircle {
  background: radial-gradient(circle at center, #A599A3, #434850, #1A262D, #1A262D);
  color: #D7C3CE;
  min-height: 100vh;
}

</style>
