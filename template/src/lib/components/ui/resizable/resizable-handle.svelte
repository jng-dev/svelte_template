<script lang="ts">
	// no createEventDispatcher — use callback props instead (Svelte 5)
	import GripVerticalIcon from '@lucide/svelte/icons/grip-vertical';
	import * as ResizablePrimitive from 'paneforge';
	import { cn, type WithoutChildrenOrChild } from '$lib/utils.js';

	let {
		ref = $bindable(null),
		class: className,
		withHandle = false,
		ontoggle, // <--- callback prop (optional)
		...restProps
	}: WithoutChildrenOrChild<ResizablePrimitive.PaneResizerProps> & {
		withHandle?: boolean;
		ontoggle?: () => void;
	} = $props();

	function handleDblClick() {
		ontoggle?.();
	}

	function handleKeyDown(e: KeyboardEvent) {
		if (e.key === 'Enter' || e.key === ' ') {
			e.preventDefault();
			ontoggle?.();
		}
	}
</script>

<ResizablePrimitive.PaneResizer
	bind:ref
	data-slot="resizable-handle"
	class={cn(
		'bg-border focus-visible:ring-ring focus-visible:outline-hidden relative flex w-px items-center justify-center after:absolute after:inset-y-0 after:left-1/2 after:w-1 after:-translate-x-1/2 focus-visible:ring-1 focus-visible:ring-offset-1 data-[direction=vertical]:h-px data-[direction=vertical]:w-full data-[direction=vertical]:after:left-0 data-[direction=vertical]:after:h-1 data-[direction=vertical]:after:w-full data-[direction=vertical]:after:-translate-y-1/2 data-[direction=vertical]:after:translate-x-0 [&[data-direction=vertical]>div]:rotate-90',
		className
	)}
	{...restProps}
>
	{#if withHandle}
		<!-- NOTE: use ondblclick / onkeydown (no colon) -->
		<div
			class="bg-border rounded-xs z-10 flex h-4 w-3 items-center justify-center border"
			ondblclick={handleDblClick}
			onkeydown={handleKeyDown}
			tabindex="0"
			role="button"
			aria-label="Toggle pane"
		>
			<GripVerticalIcon class="size-2.5" />
		</div>
	{/if}
</ResizablePrimitive.PaneResizer>
