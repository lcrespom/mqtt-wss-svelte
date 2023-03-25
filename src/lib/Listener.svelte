<script lang="ts">
	import type { MqttClient } from 'mqtt'
	import { onMount } from 'svelte'

	export let client: MqttClient
	export let topic: string

	function listen() {
		client.on('connect', () => {
			console.log('Connected')
			client.subscribe(topic, () => {
				console.log(`Subscribed to topic '${topic}'`)
			})
		})
		client.on('message', (topic, payload) => {
			console.log('Received Message:', topic, payload.toString())
		})
	}

	onMount(listen)
</script>

<div>ToDo: listener</div>
