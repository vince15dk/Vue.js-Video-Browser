<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList :videos="listVideos"></Videolist>
    
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar'
import {apiKey} from '../config/config.js'
import VideoList from './components/VideoList'

const API_KEY = apiKey
export default {
  name: 'App',
  components: {
      SearchBar,
      VideoList
  },
  data () {
      return { listVideos: []};
  },
  methods: {
      onTermChange(searchTerm){
          axios.get('https://www.googleapis.com/youtube/v3/search', {
              params: {
                  key: API_KEY,
                  type: 'video',
                  part: 'snippet',
                  q: searchTerm
              }
          }).then(response => {
              this.listVideos = response.data.items;
          });
      }
  }
};
</script>