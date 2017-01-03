<template>
    <div>
        <div v-for="code in trackingResult">
            <app-tracking-success
                :trackingData="code"
                v-if="code.nome"></app-tracking-success>
            <app-tracking-error
                :trackingData="code"
                v-if="code.erro"></app-tracking-error>
        </div>
    </div>
</template>

<script>
import AppTrackingSuccess from './result/TrackingSuccess.vue'
import AppTrackingError from './result/TrackingError.vue'

export default {
    props: {
        trackingResult: {
            type: Array,
            required: true
        }
    },
    components: {
        AppTrackingError, AppTrackingSuccess
    }
}
</script>

<style lang="scss">
.message {
    margin-bottom: 20px;
}
</style>
