<!-- template/src/routes/+layout.svelte -->
<script lang="ts">
	import ColorToggle from './../lib/components/app/ColorToggle.svelte';
	import '../app.css';
	import { ModeWatcher } from 'mode-watcher';
	import ResizeShell from '$lib/components/app/ResizeShell.svelte';
	let { children } = $props();
</script>

<ColorToggle />
<ModeWatcher />
<ResizeShell />

{@render children?.()}
