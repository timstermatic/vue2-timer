<template>
	<table class="table" v-if="history.length">
		<thead>
			<tr>
				<th>Task</th>
				<th>Time Spent</th>
			</tr>
		</thead>

		<TimerHistoryRow v-for="(row, key) in history" :row="row" :key="key"/>

	</table>
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
