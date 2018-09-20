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

	components: {
		ToolBar: ToolBar,
		TimerHistory: TimerHistory
	},
	methods: {
		saveHistory(title, timer) {
			console.log(this.title)
			this.history.push({title: title, time: timer})
		}
	},
	data() {
		return {
			history: []
		}
	}
}

</script>


	

