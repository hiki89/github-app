<template>
    <v-ons-card>
        <img src="https://pbs.twimg.com/media/Bt5MoW0CIAE9Fda.jpg" style="width: 320px">
        <div class="content">
            <p>{{`There are no ${plural} here`}}</p>
        </div>
    </v-ons-card>
</template>

<script>
import pluralize from 'pluralize'

export default {
    props: {
        type: String
    },

    computed: {
        plural() {
            return pluralize(this.type)
        }
    }
}
</script>

