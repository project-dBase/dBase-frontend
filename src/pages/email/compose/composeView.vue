<template>
    <Breadcrumbs main="Page Layout" title="Email Compose" />

    <div class="container-fluid">
        <div class="email-wrap">
            <div class="row">
                <sidePage />
                <div class="col-xl-9 box-col-12">
                    <div class="email-right-aside">
                        <div class="card email-body">
                            <div class="row">
                                <InboxComCard />
                                <ComposeCard />
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import sidePage from '../sidePage.vue'
import InboxComCard from './InboxComCard.vue'
import ComposeCard from './ComposeCard.vue'
import {
    inboxData
} from "../../../data/email/email"

export default {
    name: 'composeView',
    components: {
        sidePage,
        InboxComCard,
        ComposeCard

    },
}
</script>
