<template>
	<div>
		<input @input="onInput"/>
	</div>
</template>


<script>
	export default{
		name: 'SearchBar',
		methods: {
			onInput: function(event){
				this.$emit('termChange', event.target.value);

			}
		}
	};
</script>


<style scoped>
	input {
		width: 70%;
		border: 2px solid #D8DFD8;
		margin-top: 2%;
	}

	input:focus {
        outline: none;
	}

	div{
		text-align: center;
		margin: 20px;
	}
</style>