<template>
    <v-ons-page>
      <AppToolbar />
      <div class="center">
        <app-search :query.sync="query"/>
      </div>
    </v-ons-page>
</template>
<script>
import AppToolbar from './components/AppToolbar'
import AppSearch from './components/AppSearch'
 
export default {
  components: {
    AppToolbar,
    AppSearch
  },

  data() {
    return {
      query: ''
    }
  },

  // watch: {
  //   query (newValue) {
  //     console.log(newValue)
  //   }
  // },

  methods: {
    
  }
};
</script>
