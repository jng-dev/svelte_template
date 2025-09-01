<!-- template/src/routes/+layout.svelte -->
<script lang="ts">
	import '../app.css'
	import { ModeWatcher } from 'mode-watcher'

	let { children } = $props()
</script>

<ModeWatcher />

{@render children?.()}
