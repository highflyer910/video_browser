<template>
	<div class="container">
		<SearchBar @termChange="onTermChange"></SearchBar>
		<div class="row">
		<VideoDetail :video="selectedVideo"></VideoDetail>
		<VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
	    </div>
	</div>
</template>

<script>
	import axios from 'axios';
    import SearchBar from './components/SearchBar';
    import VideoList from './components/VideoList';
    import VideoDetail from './components/VideoDetail';
    const API_KEY = 'AIzaSyAekfRS0Hps1k4mCYSUHzv0V7dVVxKVqdg';

	export default{
		name: 'App',
		components: {
			SearchBar,
			VideoList,
			VideoDetail
		},
		data() {
          return {
             videos: [],
             selectedVideo: null
          };
		},
		methods: {
			onVideoSelect(video){
               this.selectedVideo = video;
			},
			onTermChange(searchTerm){
               axios.get('https://www.googleapis.com/youtube/v3/search', {
               	params: {
               		key: API_KEY,
               		maxResults: 25,
               		type: 'video',
               		part: 'snippet',
               		q: searchTerm
               	}
              }).then(response => {
              	this.videos = response.data.items;
              });
			}
		}

	};
</script>


<style>
	body {
		background: #abbaab;  /* fallback for old browsers */
        background: -webkit-linear-gradient(to right, #ffffff, #abbaab);  /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(to right, #ffffff, #abbaab); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

	}
</style>