<script lang="ts">
	import ColorToggle from './../lib/components/app/ColorToggle.svelte';
	import '../app.css';
	import { ModeWatcher } from 'mode-watcher';
	let { children } = $props();
</script>

<ColorToggle />
<ModeWatcher />
{@render children?.()}
