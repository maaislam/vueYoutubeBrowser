<template>
  <div class="container">
    <SearchBar @termChange = "onTermChange"></SearchBar>
    <div class="content">
      <VideoDetail :video="selectedVideo"></VideoDetail>
      <VideoList 
        :videos= "videos"
        @videoSelect="onVideoSelect">
      </VideoList>
    </div>
  </div>
</template>

<script>

  import SearchBar from './components/SearchBar';
  import VideoList from './components/VideoList';
  import VideoDetail from './components/VideoDetail'
  import axios from 'axios'
  const API_KEY = 'AIzaSyBaJ0Vs3QObN0AcGO1WSv_kqEXiMEHiig0';

  export default {
    name: 'App',
    components: {
      SearchBar,
      VideoList,
      VideoDetail
    },
    data(){
      return{
        videos:[], selectedVideo:null
      };
    },
    methods:{
      onTermChange(searchTerm){
        axios.get('https://www.googleapis.com/youtube/v3/search',{
          params:{
            key:API_KEY,
            type:'video',
            part:'snippet',
            q:searchTerm
          }
        }).then(response => {

          this.videos = response.data.items;
         
        })
      },
      onVideoSelect(video){
        this.selectedVideo = video;
      }
    }
  }
</script>

<style scoped>
  .content{
    display: grid;
    grid-template-columns: 60% 40%;
    gap: 1rem;
  }
</style>
