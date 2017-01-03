<template>
    <article
        class="message is-info"
        :class=" { 'is-success': isFinished } ">
        <div class="message-header">
            {{ trackingData.numero }}
        </div>
        <div class="message-body is-paddingless">
            <table class="table is-bordered is-striped is-marginless" v-if="trackingData.evento">
                <tbody v-for="trackEvent in trackingData.evento">
                    <tr>
                        <td class="is-icon is-large" rowspan="2"><i class="fa fa-address-book"></i></td>
                        <td colspan="2">{{trackEvent.descricao}}</td>
                    </tr>
                    <tr>
                        <td :colspan="trackEvent.destino ? 1 : 2">De: {{trackEvent.local}}</td>
                        <td v-if="trackEvent.destino">Para: {{ trackEvent.destino.local }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </article>
</template>

<script>
import some from 'lodash.some'

export default {
    props: {
        trackingData: {
            type: Object,
            required: true
        }
    },
    computed: {
        isFinished () {
            return some(this.trackingData.evento, event => {
                console.log(event)
                return ['BDE', 'BDI', 'BDR'].indexOf(event.tipo) > -1 && parseInt(event.status) < 2
            })
        }
    }
}
</script>

<style>
</style>
