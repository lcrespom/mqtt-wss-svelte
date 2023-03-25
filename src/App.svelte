<script lang="ts">
	import * as mqtt from 'mqtt'

	import Listener from './lib/Listener.svelte'
	import Poster from './lib/Poster.svelte'

	const connectUrl = `mqtt://test.mosquitto.org`
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
	<Poster {client} {topic} />
</main>
