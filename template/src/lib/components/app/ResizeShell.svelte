<script lang="ts">
	import AppInnerShell from './AppInnerShell.svelte'

	// Drop this entire file in place of your current component.
	import AppActivityBar from './AppActivityBar.svelte'
	import * as Resizable from '$lib/components/ui/resizable/index.js'
</script>

<Resizable.PaneGroup
	direction="vertical"
	class="h-full w-full overflow-visible ">
	<Resizable.Pane
		defaultSize={5}
		minSize={5}
		maxSize={5}
		class="bg-primary-foreground shadow-[0_0_15px_rgba(255,255,255,0.1)]">
		<AppActivityBar></AppActivityBar>
	</Resizable.Pane>
	<Resizable.Pane
		defaultSize={95}
		minSize={5}
		maxSize={95}
		class="shadow-[0_0_15px_rgba(255,255,255,0.1)]">
		<AppInnerShell></AppInnerShell>
	</Resizable.Pane>
</Resizable.PaneGroup>
