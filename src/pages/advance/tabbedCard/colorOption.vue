<template>
  <div class="col-xl-6 xl-100 col-lg-12 box-col-12">
    <div class="card">
      <div class="card-header">
        <h5 class="pull-left">Color Option</h5>
      </div>
      <div class="card-body">
        <div class="tabbed-card">
          <ul class="pull-right nav nav-pills nav-secondary" id="pills-clrtabsuccess" role="tablist">
            <li class="nav-item" v-on:click="changetab('timeline')"><a class="nav-link" :class="{ 'show active': showtab == 'timeline' }" id="pills-clrhome-tabsuccess" data-bs-toggle="pill" href="#pills-clrhomesuccess" role="tab" aria-controls="pills-clrhome" aria-selected="true"><i class="fa fa-home"></i>Home</a></li>
            <li class="nav-item" v-on:click="changetab('about')"><a class="nav-link" :class="{ 'show active': showtab == 'about' }" id="pills-clrprofile-tabsuccess" data-bs-toggle="pill" href="#pills-clrprofilesuccess" role="tab" aria-controls="pills-clrprofile" aria-selected="false"><i class="fa fa-user"></i>Profile
            </a></li>
            <li class="nav-item" v-on:click="changetab('friends')"><a class="nav-link" :class="{ 'show active': showtab == 'friends' }" id="pills-clrcontact-tabsuccess" data-bs-toggle="pill" href="#pills-clrcontactsuccess" role="tab" aria-controls="pills-clrcontact" aria-selected="false"><i class="fa fa-address-book">
            </i>Contact</a></li>
          </ul>
          <div class="tab-content" id="pills-clrtabContentsuccess">
            <div class="tab-pane fade " :class="{'show active': showtab == 'timeline' }" id="pills-clrhomesuccess" role="tabpanel" aria-labelledby="pills-clrhome-tabsuccess">
              <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum</p>
            </div>
            <div class="tab-pane fade" :class="{'show active': showtab == 'about' }" id="pills-clrprofilesuccess" role="tabpanel" aria-labelledby="pills-clrprofile-tabsuccess">
              <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum</p>
            </div>
            <div class="tab-pane fade" :class="{'show active': showtab == 'friends' }" id="pills-clrcontactsuccess" role="tabpanel" aria-labelledby="pills-clrcontact-tabsuccess">
              <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
 
</template>
<script>
export default {
    data(){
        return{
            showtab:'timeline',
        }
    },
    methods:{
          changetab(tab) {
        this.showtab = tab;
      }
    }
};
</script>