<script lang="ts">
	import type { MqttClient } from 'mqtt'

	export let client: MqttClient
	export let topic: string

	let message = ''

	function postMessage() {
		client.publish(topic, message, error => {
			if (error) console.error(error)
			else console.log('Message posted')
		})
	}
</script>

<label>
	Message:
	<input type="text" bind:value={message} />
</label>
<button type="button" on:click={postMessage}>Post</button>
