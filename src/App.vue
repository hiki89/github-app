<template>
    <v-ons-navigator :page-stack="pageStack"></v-ons-navigator>
</template>
<script>
import Repositories from './components/Repositories'
 
export default {
  data() {
    return {
      pageStack: [ Repositories ]
    }
  },

};
</script>

<style>

</style>

