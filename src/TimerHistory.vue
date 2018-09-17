<template>
	<div>
		<TimerHistoryRow v-for="row in history" :row="row"/>
	</div>
</template>

<script>

import TimerHistoryRow from './TimerHistoryRow.vue'

export default {
	components: {
		TimerHistoryRow: TimerHistoryRow
	},
	props: ['history']

}
</script>
