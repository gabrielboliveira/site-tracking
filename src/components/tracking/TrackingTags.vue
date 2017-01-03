<template>
    <span>
        <span class="tag is-info is-medium" v-for="tracking in numbers">
            {{ tracking }}
            <button
                class="delete is-small"
                @click="removeNumber(tracking)"></button>
        </span>
    </span>
</template>

<script>

export default {
    props: {
        numbers: {
            type: Array,
            required: true
        }
    },
    methods: {
        removeNumber (tracking) {
            let index = this.numbers.indexOf(tracking)

            if (index > -1) {
                this.numbers.splice(index, 1);
            }
        }
    }
}
</script>

<style lang="sass">
.tag
    margin-right: 10px
    margin-top: 10px
</style>
