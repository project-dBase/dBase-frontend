<template>
<div class="col-sm-12">
    <div class="card">
        <div class="profile-img-style">
            <div class="row g-2">
                <div class="col-sm-8">
                    <div class="media"><img class="img-thumbnail rounded-circle me-3" src="@/assets/images/user/7.jpg" alt="Generic placeholder image">
                        <div class="media-body align-self-center">
                            <h5 class="mt-0 user-name">JOHAN DIO</h5>
                        </div>
                    </div>
                </div>
                <div class="col-sm-4 align-self-center">
                    <div class="float-sm-end"><small>10 Hours ago</small></div>
                </div>
            </div>
            <hr>
            <p>you are going to use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden in the middle of text. All the Lorem Ipsum generators on the Internet tend to repeat predefined chunks as necessary, making this the first true generator on the Internet.</p>
            <div class="row mt-4 pictures" id="aniimated-thumbnials-2"><a class="col-sm-6" href="javascript:void(0)"><img class="img-fluid rounded" src="@/assets/images/other-images/profile-style-img.png" alt="gallery"></a><a class="col-sm-6" href="javascript:void(0)"><img class="img-fluid rounded" src="@/assets/images/other-images/profile-style-img.png" alt="gallery"></a></div>
            <div class="like-comment mt-4">
                <ul class="list-inline">
                    <li class="list-inline-item border-right pe-3">
                        <label class="m-0"><a href="#"><i class="fa fa-heart"></i></a>  Like</label><span class="ms-2 counter">
                            <number class="bold counter" ref="number1" :from="0" :to="2659" :duration="5" :delay="0" easing="Power1.easeOut" /></span>
                    </li>
                    <li class="list-inline-item ms-2">
                        <label class="m-0"><a href="#"><i class="fa fa-comment"></i></a>  Comment</label><span class="ms-2 counter">
                            <number class="bold counter" ref="number1" :from="0" :to="569" :duration="5" :delay="0" easing="Power1.easeOut" /></span>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</div>
</template>
