<template>
	<tr>
		<td>{{row.title}}</td><td>{{humanReadableTime}}</td>
	</tr>
</template>

<script>
import Moment from 'moment'
export default {
	components: {
		Moment: Moment
	},
	props: ['row'],
  computed: {
    // a computed getter
    humanReadableTime: function () {
      // `this` points to the vm instance
      return Moment("2015-01-01").startOf('day').seconds(this.row.time).format('HH:mm:ss');
    }
  }
}
</script>
