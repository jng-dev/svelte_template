<script lang="ts">
	// Drop this entire file in place of your current component.
	import * as Resizable from '$lib/components/ui/resizable/index.js'
	import SidebarShell from './SidebarShell.svelte'
	import ExampleChart from '../chart/ExampleChart.svelte'
	let paneOne: ReturnType<typeof Resizable.Pane>

	function toggleFirstPane() {
		if (!paneOne) return
		if (paneOne.isCollapsed?.())
			paneOne.expand?.()
		else paneOne.collapse?.()
	}
</script>

<Resizable.PaneGroup
	direction="horizontal"
	class="h-full w-full border">
	<Resizable.Pane
		defaultSize={15}
		class="border-1 min-h-0 min-w-0 shadow-[0_0_15px_rgba(255,255,255,0.1)]"
		collapsedSize={0}
		collapsible={true}
		minSize={10}
		maxSize={30}
		bind:this={paneOne}
		><SidebarShell></SidebarShell
		></Resizable.Pane>

	<Resizable.Handle
		withHandle
		ontoggle={toggleFirstPane} />

	<Resizable.Pane
		defaultSize={85}
		class="border-1 flex min-h-0 min-w-0 flex-col justify-center p-5 shadow-[0_0_15px_rgba(255,255,255,0.1)]">
		<ExampleChart /></Resizable.Pane>
</Resizable.PaneGroup>
