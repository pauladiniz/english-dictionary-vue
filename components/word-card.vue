<template>
	<div class="word-card">
		<h2 :title="title">{{ title }}</h2>
		<span :pronunciation="pronunciation">/{{ pronunciation }}/</span>
		<p :definition="definition">{{ definition }}</p>
	</div>
</template>

<script>
import definitionCard from './definition-card.vue'

export default {
components: { definitionCard },
props: {
	title: {
		type: String,
		required: true,
	},
	pronunciation: String,
	required: true
},
definition: String,
required: true
}
</script>

<style lang="stylus" scoped>
.word-card
	font-family 'Roboto Mono'
	h2 
		font-weight bold
		font-size 1.3rem
		color #575757
		background-color #bae9e8
	span
		font-style italic
</style>