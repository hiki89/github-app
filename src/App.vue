<template>
    <v-ons-page>
      <AppToolbar />
      <div class="center">
        <app-search :query.sync="query"/>
      </div>
    </v-ons-page>
</template>
<script>
import debounce from 'lodash/debounce'

import AppToolbar from './components/AppToolbar'
import AppSearch from './components/AppSearch'
import {gitHub} from './services/GitHub'
 
export default {
  components: {
    AppToolbar,
    AppSearch
  },

  data() {
    return {
      query: '',
      repos: []
    }
  },

  watch: {
    query: debounce (function (newValue) {
      gitHub.getRepos(newValue)
      .then((response) => {
        this.repos = response.data
        console.log(this.repos)
      })
    }, 500)
  },



  methods: {
    // repo(username) {
    //   GitHub.getRepos(username)
    //   .then(response => {
    //     next(repos => {
    //       this.repos = response.data
    //       console.log(this.repos)
    //     })
        
    //   })
      
    // }
  }
};
</script>
