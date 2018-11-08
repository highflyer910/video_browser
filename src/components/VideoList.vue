<template>
	<ul>
		{{ videos.length }}
	</ul>
	
</template>


<script>
	import VideoListItem from './VideoListItem';
	export default {
        name: 'VideoList',
        components: {
          VideoListItem
        },
        props: ['videos']
	};
</script>


<style>
	
</style>