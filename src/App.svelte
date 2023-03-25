<script lang="ts">
	// Import this as a workaround for a Vite/MQTT incompatibility. See https://github.com/mqttjs/MQTT.js/issues/1269
	import * as mqtt from 'mqtt/dist/mqtt.min'

	import Listener from './lib/Listener.svelte'
	import Poster from './lib/Poster.svelte'

	const connectUrl = `wss://test.mosquitto.org:8081`
	const topic = '/luis/test'

	function connect() {
		console.log('Trying to connect to ' + connectUrl)
		return mqtt.connect(connectUrl)
	}

	let client = connect()
</script>

<main>
	<h1>MQTT Test</h1>

	<Listener {client} {topic} />
	<hr style="margin: 2em 1ex" />
	<Poster {client} {topic} />
</main>
