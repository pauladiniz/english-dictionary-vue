<template>
	<div class="definition-card">
		<img class="float-right p-2" :src='src'/>
		<p :definition="definition">
			• {{ definition }}
		</p>
	</div>
</template>

<script>
export default {
	props: {
		definition: {
			type: String
		},
		src: {
			type: String
		}
	}
}
</script>

<style lang="stylus">
	img
		width 110px
		border-radius 50%
</style>