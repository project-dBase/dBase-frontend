<template>
<div class="col-xxl-auto col-xl-3 col-sm-6 box-col-6">
    <div class="row">
        <div class="col-xl-12" v-for="puechaseSales in puechaseSalesDetails1" :key="puechaseSales">
            <div class="card widget-1">
                <div class="card-body">
                    <div class="widget-content">
                        <div :class="puechaseSales.widgetClass">
                            <div class="bg-round">
                                <svg class="svg-fill">
                                    <use :xlink:href="require('@/assets/svg/icon-sprite.svg') + `#${puechaseSales.svgIcon1}`"></use>
                                </svg>
                                <svg class="half-circle svg-fill">
                                    <use :xlink:href="require('@/assets/svg/icon-sprite.svg') + `#${puechaseSales.svgIcon2}`"></use>
                                </svg>
                            </div>
                        </div>
                        <div>
                            <h4 class="f-light">{{ puechaseSales.number }}</h4>
                            <span class="f-light">
                                {{ puechaseSales.title }}
                            </span>
                        </div>
                    </div>
                    <div :class="puechaseSales.growthClass">
                        <i :class="puechaseSales.iconClass"></i><span>{{ puechaseSales.growthNumber }}</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>

<div class="col-xxl-auto col-xl-3 col-sm-6 box-col-6">
    <div class="row">
        <div class="col-xl-12" v-for="puechaseSales in puechaseSalesDetails2" :key="puechaseSales">
            <div class="card widget-1">
                <div class="card-body">
                    <div class="widget-content">
                        <div :class="puechaseSales.widgetClass">
                            <div class="bg-round">
                                <svg class="svg-fill">
                                    <use :xlink:href="require('@/assets/svg/icon-sprite.svg') + `#${puechaseSales.svgIcon1}`"></use>
                                </svg>
                                <svg class="half-circle svg-fill">
                                    <use :xlink:href="require('@/assets/svg/icon-sprite.svg') + `#${puechaseSales.svgIcon2}`"></use>
                                </svg>
                            </div>
                        </div>
                        <div>
                            <h4 class="f-light">{{ puechaseSales.number }}</h4>
                            <span class="f-light">
                                {{ puechaseSales.title }}
                            </span>
                        </div>
                    </div>
                    <div :class="puechaseSales.growthClass">
                        <i :class="puechaseSales.iconClass"></i><span>{{ puechaseSales.growthNumber }}</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
import {
    puechaseSalesDetails1,
    puechaseSalesDetails2
} from "../../../data/dashboard/default"
export default {
  props: {
    puechaseSalesDetails1: {
      type: Array,
      required: true,
    },
    puechaseSalesDetails2: {
      type: Array,
      required: true,
    },
  },
    data() {
        return {

        }
    }
}
</script>
