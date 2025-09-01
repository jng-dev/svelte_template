<script>
	import RadialDemo from '$lib/components/chart/demo/RadialDemo.svelte'
</script>

<div class="p-30 flex h-full flex-col">
	<h1
		class="text-foreground mb-5 text-xl font-bold">
		Showcasing component
	</h1>

	<div
		class="bg-muted-foreground/10
           flex flex-1 items-center justify-center
           rounded-lg p-10
           shadow-[0_0_10px_rgba(0,0,0,0.5),0_0_20px_rgba(255,255,255,0.05)]
           ring-1 ring-black/50">
		<RadialDemo />
	</div>
</div>
