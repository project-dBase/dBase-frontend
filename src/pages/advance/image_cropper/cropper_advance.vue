<template>
  <Breadcrumbs title="Image Cropper" main="Bonus UI"  />
  <div class="container-fluid">
            <div class="img-cropper">
              <div class="row">
                <div class="col-sm-12 ">
                    <imageCropper/>
                </div>
              </div>
            </div>
            </div>
</template>
<script>
import imageCropper from "./imageCropper.vue"
export default {
    components:{
        imageCropper,
    }
}
</script>