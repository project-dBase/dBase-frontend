<template>
  <v-row>
    <v-col
        cols="12"
        sm="6"
        md="3"
        v-for="puechaseSales in puechaseSalesDetails"
        :key="puechaseSales"
    >
      <v-card
          class="widget-1"
          style="border: 4px solid #7066f6; border-radius: 20px; background-color: rgba(160, 162, 177, 0.45);"
      >
        <v-row class="d-flex align-center">
          <v-col cols="3" class="m-2" style="min-height: 50px;">
            <div class="widget-content d-flex align-center mt-2 ml-2">
              <div :class="puechaseSales.widgetClass">
                <div class="bg-round">
                  <svg class="svg-fill">
                    <use :xlink:href="require('@/assets/svg/icon-sprite.svg') + `#${puechaseSales.svgIcon1}`"></use>
                  </svg>
                </div>
              </div>
            </div>
          </v-col>
          <v-col cols="8">
            <v-card-text>
              <h4 class="f-light" @click="toggleText(puechaseSales)">
                {{ displayText(puechaseSales) }}
              </h4>
              <span class="f-light">{{ puechaseSales.title }}</span>
            </v-card-text>
            <v-card-actions :class="puechaseSales.growthClass">
              <i :class="puechaseSales.iconClass"></i
              ><span>{{ puechaseSales.growthNumber }}</span>
            </v-card-actions>
          </v-col>
        </v-row>
      </v-card>
    </v-col>
  </v-row>
</template>




<script>
import {
  puechaseSalesDetails1,
  puechaseSalesDetails2
} from "../../../data/dashboard/default"

export default {
  props: {
    puechaseSalesDetails: {
      type: Array,
      required: true,
    },
  },
  computed(){
    console.log(puechaseSalesDetails);
  },
  methods: {
    toggleText(puechaseSales) {
      this.expandedText[puechaseSales.title] =
          !this.expandedText[puechaseSales.title];
    },
    displayText(puechaseSales) {
      const text = String(puechaseSales.number);
      if (
          this.expandedText[puechaseSales.title] ||
          text.length <= this.maxDisplayChars
      ) {
        return text;
      } else {
        return text.slice(0, this.maxDisplayChars) + "...";
      }
    },
  },
  data() {
    return {
      expandedText: {},
      maxDisplayChars: 7,
      buttons: [
        {
          title: 'Collecrt reward',
          color: '#7066f6',
          onClick: this.button1Clicked
        },
        {
          title: 'Collect reward and unstake',
          color: '#7066f6',
          onClick: this.button2Clicked
        },{
          title: 'Deactivate node',
          color: '#7066f6',
          onClick: this.button1Clicked
        },
        {
          title: 'Update http endpoint',
          color: '#7066f6',
          onClick: this.button2Clicked
        },

      ],

    }
  }
}
</script>
