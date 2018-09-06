<template>
    <v-ons-page>
        <v-ons-toolbar>
            <div class="left">

            </div>
            <div class="center">
                {{title}}
            </div>
            <div class="right">

            </div>
        </v-ons-toolbar>
    </v-ons-page>
</template>

<script>
export default {
    props: {
        title: {
            type: String,
            default: 'Github'
        }
    }
}
</script>

