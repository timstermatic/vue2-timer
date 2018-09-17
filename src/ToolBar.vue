<template>
	<div>
		<input type="text" v-model="title" placeholder="Project / Task Title" />
		<button @click="toggleTimer()">{{ timerRunning?'Pause':'Start'}}</button>
		<button @click="endTimer" v-if="timer > 0 && !timerRunning">End</button>
		<span>{{timer}}</span>

	</div>
</template>

<script>
export default {
	props: ['saveHistory'],
	data() {
		return {
			timer: 0,
			timerRunning: false,
			title: ''
		}
	},
	methods: { 
		toggleTimer() {
			const vm = this
			if(vm.timerRunning) {
				vm.timerRunning = false
				clearInterval(vm.timerFunc)
			} else {
				vm.timerRunning = true
				vm.timerFunc = setInterval(function () {
					vm.timer += 1
				}, 1000)
			}
		},
		endTimer() {
			this.saveHistory(this.title, this.timer)
			this.timerRunning = false
			clearInterval(this.timerFunc)
			this.title = ''
			this.timer = 0
		}
	}


}
</script>
