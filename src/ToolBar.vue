<template>
	<section class="card">
		<div class="card-body">
			<div class="card-title"><h2>Vue Timer</h2></div>
			<hr>
			<div class="row">
				<div class="col">
					<input type="text" v-model="title" placeholder="Project / Task Title" class="form-control" />
				</div>
				<div class="col">
					<button @click="toggleTimer()" class="btn btn-dark">{{ timerRunning?'Pause':'Start'}}</button>
					<button @click="endTimer" v-if="timer > 0 && !timerRunning" class="btn btn-default">End</button>
				</div>
				<div class="col">
					<h3>{{timerHumanReadable}}</h3>
				</div>	
			</div>
		</div>
	</section>
</template>

<script>

import Moment from 'moment'

export default {
	components: {
		Moment: Moment
	},
	props: ['saveHistory'],
	data() {
		return {
			timer: 0,
			timerHumanReadable: '00:00:00',
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
					vm.timerHumanReadable = Moment("2015-01-01").startOf('day').seconds(vm.timer)
    .format('HH:mm:ss');
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