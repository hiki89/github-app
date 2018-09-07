<template>
    <v-ons-page>
      <AppToolbar />
      <div class="center">
        <app-search :query.sync="query"/>
        <v-ons-list>
          <v-ons-list-header>{{`Repositories of ${this.query}`}}</v-ons-list-header>
          <div v-if="this.loadingRepos">
          <v-ons-progress-circular indeterminate></v-ons-progress-circular>
          </div>
          <v-ons-list-item v-for="repo in repos" :key="repo.id">
            <div class="left">
              <img class="list-item__thumbnail" :src="repo.owner.avatar_url">
            </div>
            <div class="center">
              <span class="list-item__title">{{repo.name}}</span>
              <span class="list-item__subtitle">{{repo.description}}</span>
            </div>
          </v-ons-list-item>
        </v-ons-list>
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
      repos: [],
      loadingRepos: false
    }
  },

  watch: {
    query: debounce (function (newValue) {
      this.loadingRepos = true
      gitHub.getRepos(newValue)
      .then((response) => {
        this.repos = response.data
        console.log(this.repos)
      })
      .finally(() => {
        this.loadingRepos = false
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

<style>

</style>

