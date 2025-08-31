<script lang="ts">
	import * as Tooltip from '$lib/components/ui/tooltip/index.js'
	import {
		cn,
		type WithElementRef
	} from '$lib/utils.js'
	import type { HTMLAttributes } from 'svelte/elements'
	import {
		SIDEBAR_COOKIE_MAX_AGE,
		SIDEBAR_COOKIE_NAME
	} from './constants.js'
	import { setSidebar } from './context.svelte.js'

	let {
		ref = $bindable(null),
		open = $bindable(true),
		onOpenChange = () => {},
		class: className,
		style,
		children,
		...restProps
	}: WithElementRef<
		HTMLAttributes<HTMLDivElement>
	> & {
		open?: boolean
		onOpenChange?: (open: boolean) => void
	} = $props()

	const sidebar = setSidebar({
		open: () => open,
		setOpen: (value: boolean) => {
			open = value
			onOpenChange(value)
			document.cookie = `${SIDEBAR_COOKIE_NAME}=${open}; path=/; max-age=${SIDEBAR_COOKIE_MAX_AGE}`
		}
	})
</script>

<svelte:window
	onkeydown={sidebar.handleShortcutKeydown} />

<Tooltip.Provider delayDuration={0}>
	<div
		data-slot="sidebar-wrapper"
		style="--sidebar-width: 100%; --sidebar-width-icon: 100%; {style}"
		class={cn(
			'group/sidebar-wrapper has-data-[variant=inset]:bg-sidebar relative h-full w-full',
			className
		)}
		bind:this={ref}
		{...restProps}>
		{@render children?.()}
	</div>
</Tooltip.Provider>
