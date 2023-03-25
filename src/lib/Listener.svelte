<script lang="ts">
	import type { MqttClient } from 'mqtt'
	import { onMount } from 'svelte'

	export let client: MqttClient
	export let topic: string

	let messages = ''

	function listen() {
		client.on('connect', () => {
			console.log('Connected')
			client.subscribe(topic, () => {
				console.log(`Subscribed to topic '${topic}'`)
			})
		})
		client.on('message', (topic, payload) => {
			console.log('Received Message:', topic, payload.toString())
			let tstamp = new Date().toLocaleString().split(' ')[1]
			messages += tstamp + ' - ' + payload + '\n'
		})
	}

	onMount(listen)
</script>

<pre>
{messages}
</pre>
