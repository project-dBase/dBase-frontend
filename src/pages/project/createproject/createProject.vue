<template>
    <Breadcrumbs main="Project" title="Project Create" />

    <div class="container-fluid">
        <div class="row">
            <div class="col-sm-12">
                <div class="card">
                    <div class="card-body">
                        <div class="form theme-form">
                            <div class="row">
                                <div class="col">
                                    <div class="mb-3">
                                        <label>Project Title</label>
                                        <input class="form-control" type="text" placeholder="Project name *">
                                    </div>
                                </div>
                            </div>
                            <div class="row">
                                <div class="col">
                                    <div class="mb-3">
                                        <label>Client name</label>
                                        <input class="form-control" type="text" placeholder="Name client or company name">
                                    </div>
                                </div>
                            </div>
                            <div class="row">
                                <div class="col-sm-4">
                                    <div class="mb-3">
                                        <label>Project Rate</label>
                                        <input class="form-control" type="text" placeholder="Enter project Rate">
                                    </div>
                                </div>
                                <div class="col-sm-4">
                                    <div class="mb-3">
                                        <label>Project Type</label>
                                        <select class="form-select">
                                            <option>Hourly</option>
                                            <option>Fix price</option>
                                        </select>
                                    </div>
                                </div>
                                <div class="col-sm-4">
                                    <div class="mb-3">
                                        <label>Priority</label>
                                        <select class="form-select">
                                            <option>Low</option>
                                            <option>Medium</option>
                                            <option>High</option>
                                            <option>Urgent</option>
                                        </select>
                                    </div>
                                </div>
                            </div>
                            <div class="row">
                                <div class="col-sm-4">
                                    <div class="mb-3">
                                        <label>Project Size</label>
                                        <select class="form-select">
                                            <option>Small</option>
                                            <option>Medium</option>
                                            <option>Big</option>
                                        </select>
                                    </div>
                                </div>
                                <div class="col-sm-4">
                                    <div class="mb-3">
                                        <label>Starting date</label>
                                        <Datepicker1 class="datepicker-here form-control digits" v-model="date4" range
                                            data-language="en"></Datepicker1>
                                    </div>
                                </div>
                                <div class="col-sm-4">
                                    <div class="mb-3">
                                        <label>Ending date</label>
                                        <Datepicker1 class="datepicker-here form-control digits" v-model="date4" range
                                            data-language="en"></Datepicker1>
                                    </div>
                                </div>
                            </div>
                            <projectForm />
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import projectForm from "./projectForm.vue"
import Datepicker1 from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css'
export default {
    name: 'createProject',
    components: {
        Datepicker1, projectForm
    },
}
</script>
