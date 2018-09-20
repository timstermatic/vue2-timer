<template>
	<div class="container">
		<ToolBar :saveHistory="saveHistory"/>
		<TimerHistory :history="history" />
	</div>
</template>

<script>

import ToolBar from './ToolBar.vue'
import TimerHistory from './TimerHistory.vue'

export default {
	created() {
		this.loadHistory()
	},
	components: {
		ToolBar: ToolBar,
		TimerHistory: TimerHistory
	},
	methods: {
		saveHistory(title, timer) {
			this.history.unshift({title: title, time: timer})
			localStorage.setItem('history', JSON.stringify(this.history))
		},
		loadHistory: function() {
			this.history = JSON.parse(localStorage.history) || []
		}
	},
	data() {
		return {
			history: []
		}
	}
}

</script>

	

