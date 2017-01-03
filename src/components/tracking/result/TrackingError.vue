<template>
    <article class="message is-danger">
        <div class="message-header">
            {{ trackingData.numero }}
        </div>
        <div class="message-body">
            {{ trackingData.erro }}
        </div>
    </article>
</template>

<script>

export default {
    props: {
        trackingData: {
            type: Object,
            required: true
        }
    }
}
</script>

<style>

</style>
