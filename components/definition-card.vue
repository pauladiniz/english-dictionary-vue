<template>
  <div class="definition-card">
		<p :definition="definition">
			{{ definition }}
		</p>
  </div>
</template>

<script>
export default {
  props: {
		definition: String
	}
}
</script>