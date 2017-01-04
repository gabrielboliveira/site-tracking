<template>
    <div>
        <app-header></app-header>
        <section class="section is-paddingless">
            <div class="container">
                <app-tracking-section></app-tracking-section>
            </div>
        </section>
        <app-footer></app-footer>
    </div>
</template>

<script>
import AppHeader from './components/Header.vue'
import AppTrackingSection from './components/tracking/TrackingSection.vue'
import AppFooter from './components/Footer.vue'
import 'vue-awesome/icons'

export default {
    components: {
        AppTrackingSection, AppHeader, AppFooter
    }
}
</script>

<style lang="sass">
@import "~bulma/bulma.sass"
</style>
