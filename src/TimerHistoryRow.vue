<template>
	<div>
		{{row.title}} took {{row.time}} seconds
	</div>
</template>

<script>
export default {
	props: ['row']
}
</script>
