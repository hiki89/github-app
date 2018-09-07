<template>
    <v-ons-navigator :page-stack="pageStack" @next-page="pushPage"></v-ons-navigator>
</template>
<script>
import Repositories from './components/Repositories'
 
export default {
  data() {
    return {
      pageStack: [ Repositories ]
    }
  },

  methods: {
    pushPage(page) {
      this.pageStack.push(page)
    }
  }

};
</script>

<style>

</style>

