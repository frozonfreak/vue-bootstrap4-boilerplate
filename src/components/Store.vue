const Store = () => Promise.resolve({ 
	<template>
		<div class="foo">
			<h1>vuex Test</h1>
			Clicked: {{ getCount }} times
			<b-btn variant="info" class="m-1" @click="increment">+</b-btn>
			<b-btn variant="info" class="m-1" @click="decrement">-</b-btn>
		</div>
	</template>

	<script>
		import { mapGetters, mapActions } from 'vuex'

		export default {
		  computed: {
		    ...mapGetters([
		      'getCount'
		      // ...
		    ])
		  },
		  methods: {
		    ...mapActions([
		      'increment',
		      'decrement'
		    ])
		  }
		}
	</script>

	<!-- Add "scoped" attribute to limit CSS to this component only -->
	<style scoped>

	</style>

})
