<template>
    <div class="columns tracking-section">
        <div class="column
                    is-multiline
                    is-8-tablet
                    is-offset-2-tablet
                    is-8-desktop
                    is-offset-2-desktop">

            <div class="column is-12">
                <app-tracking-input @trackingAdded="addTracking"></app-tracking-input>
            </div>

            <transition name="slide">
                <div v-if="showWarning">
                    <article class="message is-warning">
                        <div class="message-body">
                            Código de rastreio já adicionado
                        </div>
                    </article>
                </div>
            </transition>

            <div class="column is-12">
                <app-tracking-tags :numbers="trackingCodes"></app-tracking-tags>
            </div>

            <hr>

            <div
                class="content has-text-centered"
                :class="{ 'm20': !result.length  }">
                <a
                    class="button is-info is-large"
                    :class="{
                        'is-loading': isLoading,
                        'is-disabled': !trackingCodes.length
                    }"
                    @click="checkTrackers">Verificar</a>
                <a
                    class="button is-info is-large"
                    @click="clean">Limpar</a>
            </div>

            <div v-if="result.length">
                <hr>
                <div class="tracking-result">
                    <app-tracking-result :trackingResult="result"></app-tracking-result>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import AppTrackingTags from './TrackingTags.vue'
import AppTrackingInput from './TrackingInput.vue'
import AppTrackingResult from './TrackingResult.vue'
import { url } from '../../config.json'

export default {
    data () {
        return {
            isLoading: false,
            trackingCodes: [],
            showWarning: false,
            result: []
        }
    },
    methods: {
        checkTrackers () {
            this.isLoading = true
            this.$http.post(url, {
                codes: this.trackingCodes
            }).then(
                response => {
                    this.result = response.data.data
                    this.isLoading = false
                    this.trackingCodes = []
                },
                error => console.error(error)
            );
        },
        addTracking (trackingNumber) {
            if( this.trackingCodes.indexOf(trackingNumber) === -1) {
                this.trackingCodes.push(trackingNumber)
            } else {
                this.showWarning = true
                setTimeout( () => {
                    this.showWarning = false
                }, 2000)
            }
        },
        clean () {
            this.result = []
            this.trackingCodes = []
        }
    },

    components: {
        AppTrackingTags, AppTrackingInput, AppTrackingResult
    }
}
</script>

<style lang="scss">
.m20 {
    margin-bottom: 20px;
}

.tracking-result {
    padding: 10px;
}

.slide-enter {
    opacity: 0;
    height: 0;
}

.slide-enter-active {
    animation: slide-in 1s ease-out forwards;
    transition: opacity 1s;
}

.slide-leave-active {
    animation: slide-out 1s ease-out forwards;
    transition: opacity 1s;
    opacity: 0;
    height: 0;
}

@keyframes slide-in {
    from {
        height: 0;
        transform: translateY(-20px);
    }
    to {
        height: 46px;
        transform: translateY(0);
    }
}

@keyframes slide-out {
    from {
        height: 46px;
        transform: translateY(0);
    }
    to {
        height: 0;
        transform: translateY(-20px);
    }
}
</style>
