<script>
	import yaml from 'js-yaml';
	let erryaml = '';
	let errjson;
	let erri18n = '';
	function handleClick() {
		try {
			errjson = yaml.load(erryaml, 'utf8');
			for (const value of Object.entries(errjson.errors)) {
				erri18n += `"${value[1].code}": "${value[1].message}",\n`;
			}
		} catch (e) {
			erri18n = e;
		}
	}
</script>

<main>
	<h1>Generates a locale JSON file for error codes translation</h1>
	<textarea bind:value={erryaml}></textarea>
	<button on:click={handleClick}>Gen</button>
	<textarea bind:value={erri18n}></textarea>
</main>

<style>
	textarea { width: 100%; height: 200px; }
</style>