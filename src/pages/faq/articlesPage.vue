<template>
<div class="col-lg-12">
    <div class="header-faq">
        <h5 class="mb-0">Latest articles and videos</h5>
    </div>
    <div class="row">
        <div class="col-xl-4 col-md-6" >
            <div class="row">
                <div class="col-sm-12" v-for="faq in faqs.codepen" from :key="faq">
                    <div class="card">
                        <div class="card-body">
                            <div class="media">
                                <vue-feather class="m-r-30" :type="faq.iconType"></vue-feather>
                                <div class="media-body">
                                    <h6 class="f-w-500">{{ faq.title }}</h6>
                                    <p>{{ faq.decription }}</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="col-xl-4 col-md-6">
            <div class="row">
                <div class="col-sm-12">
                    <div class="card">
                        <div class="card-body">
                            <div class="media">
                                <vue-feather class="m-r-30" type="file-text"></vue-feather>
                                <div class="media-body">
                                    <h6 class="f-w-500"> Donec pede justo</h6>
                                    <p> Cras dapibus. Vivamus elementum semper nisi. Aenean vulputate eleifend tellus. </p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-sm-12">
                    <div class="card">
                        <div class="card-body">
                            <div class="media">
                                <vue-feather class="m-r-30" type="file-text"></vue-feather>
                                <div class="media-body">
                                    <h6 class="f-w-500"> Nam quam nunc</h6>
                                    <p> Cras dapibus. Vivamus elementum semper nisi. Aenean vulputate eleifend tellus.</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-sm-12">
                    <div class="card">
                        <div class="card-body">
                            <div class="media">
                                <vue-feather class="m-r-30" type="file-text"></vue-feather>
                                <div class="media-body">
                                    <h6 class="f-w-500">Using Video </h6>
                                    <p>Cras dapibus. Vivamus elementum semper nisi. Aenean vulputate eleifend tellus.</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <articles2 />
    </div>
</div>
</template>

<script>
import articles from "../../data/faq/faq.json"
import articles2 from "./articles2Page.vue"
export default {
    components: {
        articles2
    },
    data() {
      return {
        faqs:articles
      }
    },
  }
</script>
