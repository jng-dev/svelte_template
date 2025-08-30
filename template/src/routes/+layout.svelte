<!-- template/src/routes/+layout.svelte -->
<script lang="ts">
	import '../app.css';
	import { ModeWatcher } from 'mode-watcher';
	import ResizeShell from '$lib/components/app/ResizeShell.svelte';
	let { children } = $props();
</script>

<!-- 👇 anchor to viewport height -->
<div class="flex h-dvh w-full flex-col">
	<ModeWatcher />
	<!-- 👇 let shell consume remaining space -->
	<div class="min-h-0 flex-1">
		<ResizeShell />
	</div>
	{@render children?.()}
</div>
