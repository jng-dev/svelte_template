<script lang="ts">
	// Drop this entire file in place of your current component.
	import { onMount, onDestroy } from 'svelte';
	import * as Resizable from '$lib/components/ui/resizable/index.js';
	import MainFrameShell from './MainFrameShell.svelte';
	import SidebarShell from './SidebarShell.svelte';
	import * as Sidebar from '$lib/components/ui/sidebar/index.js';

	let paneOne: ReturnType<typeof Resizable.Pane>;

	function toggleFirstPane() {
		if (!paneOne) return;
		if (paneOne.isCollapsed?.()) paneOne.expand?.();
		else paneOne.collapse?.();
	}
</script>

<Resizable.PaneGroup direction="horizontal" class="h-full w-full overflow-hidden rounded-lg border">
	<Resizable.Pane
		defaultSize={25}
		class="min-h-0 min-w-0 overflow-hidden border-2"
		collapsedSize={0}
		collapsible={true}
		minSize={10}
		maxSize={30}
		bind:this={paneOne}><SidebarShell></SidebarShell></Resizable.Pane
	>

	<Resizable.Handle withHandle ontoggle={toggleFirstPane} />

	<Resizable.Pane defaultSize={75} class="min-h-0 min-w-0 overflow-hidden border-2">
		<Resizable.PaneGroup direction="vertical"></Resizable.PaneGroup></Resizable.Pane
	>
</Resizable.PaneGroup>
