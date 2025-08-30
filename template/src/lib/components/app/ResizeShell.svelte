<!-- template\src\lib\components\app\ResizeShell.svelte -->
<script lang="ts">
	import * as Resizable from '$lib/components/ui/resizable/index.js';
	import MainFrameShell from './MainFrameShell.svelte';
	import SidebarShell from './SidebarShell.svelte';
</script>

<Resizable.PaneGroup direction="horizontal" class="h-full rounded-lg border">
	<Resizable.Pane defaultSize={25}>
		<div class="m-28 h-full w-full border-2"></div>
	</Resizable.Pane>
	<Resizable.Handle withHandle />
	<Resizable.Pane defaultSize={75}></Resizable.Pane>
</Resizable.PaneGroup>
