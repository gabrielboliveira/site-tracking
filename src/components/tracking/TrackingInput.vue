<template>
    <div class="columns is-mobile is-multiline">
        <div class="column">
            <p class="control has-icon has-icon-right">
                <input
                    class="input is-large"
                    :class="{ 'is-success': isValid && tracking.length, 'is-danger': !isValid && tracking.length }"
                    type="text"
                    placeholder="DU897123996BR"
                    v-model="tracking">
                <i
                    class="fa"
                    :class="{
                        'fa-check': isValid && tracking.length,
                        'fa-warning': !isValid && tracking.length
                    }">
                </i>
            </p>
        </div>
        <div class="column is-narrow">
            <span
                class="icon is-large"
                :class="{ 'is-disabled': ! isValid }"
                @click="addTracker">
                <i class="fa fa-plus-square"></i>
            </span>
        </div>
    </div>
</template>

<script>
import { isValid } from 'tracking-correios'

export default {
    data() {
        return {
            tracking: '',
            error: false
        }
    },
    methods: {
        addTracker() {
            this.$emit('trackingAdded', this.tracking)
            this.tracking = ''
        }
    },
    computed: {
        isValid () {
            return isValid(this.tracking)
        }
    }
}
</script>

<style lang="sass">
@import "~bulma/sass/utilities/variables.sass"

.icon
    cursor: pointer

    &:hover
        color: $info
</style>
