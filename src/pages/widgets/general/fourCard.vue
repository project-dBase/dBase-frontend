<template>
  <div class="col-sm-6 col-xl-3 col-lg-6 box-col-6">
    <div class="card widget-1">
      <div class="card-body">
        <div class="widget-content">

          <div>
            <h4 class="f-light">{{ number1 }}</h4><span class="f-light">{{ text1 }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="col-sm-6 col-xl-3 col-lg-6 box-col-6">
    <div class="card widget-1">
      <div class="card-body">
        <div class="widget-content">

          <div>
            <h4 class="f-light">{{ number2 }}</h4><span class="f-light">{{ text2 }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="col-sm-6 col-xl-3 col-lg-6 box-col-6">
    <div class="card widget-1">
      <div class="card-body">
        <div class="widget-content">
          <div>
            <h4 class="f-light">{{ number3 }}</h4><span class="f-light">{{ text3 }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="col-sm-6 col-xl-3 col-lg-6 box-col-6">
    <div class="card widget-1">
      <div class="card-body">
        <div class="widget-content">
          <div>
            <h4 class="f-light">{{ number4 }}</h4><span class="f-light">{{ text4 }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    text1: String,
    text2: String,
    text3: String,
    text4: String,
    number1: String,
    number2: String,
    number3: String,
    number4: String
  }
}

</script>