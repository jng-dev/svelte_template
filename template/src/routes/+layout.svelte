<!-- template/src/routes/+layout.svelte -->
<script lang="ts">
	import '../app.css'
	import { ModeWatcher } from 'mode-watcher'
	import ResizeShell from '$lib/components/app/ResizeShell.svelte'
	let { children } = $props()
</script>

<ModeWatcher />
<ResizeShell />

{@render children?.()}
