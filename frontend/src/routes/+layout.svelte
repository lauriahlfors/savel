<script lang="ts">
	import '../app.css';
	// Tabler Icon imports
	import PlayerPlayFilled from '@tabler/icons-svelte/icons/player-play-filled';
	import PlayerSkipBackFilled from '@tabler/icons-svelte/icons/player-skip-back-filled';
	import PlayerSkipForwardFilled from '@tabler/icons-svelte/icons/player-skip-forward-filled';
	import DiscFilled from '@tabler/icons-svelte/icons/disc-filled';
	import UserFilled from '@tabler/icons-svelte/icons/user-filled';
	import Volume from '@tabler/icons-svelte/icons/volume';

	// Shadcn Svelte imports
	import { Slider } from '$lib/components/ui/slider';

	const { children } = $props();
</script>

<main>
	{@render children()}
	{@render PlayerNav()}
</main>

{#snippet PlayerNav()}
	<nav class="fixed bottom-0 grid w-full grid-cols-3 bg-neutral-950 px-3 py-2">
		<!-- Current track info -->
		<div class="flex h-full items-center gap-3 bg-neutral-950">
			<div class="size-12 rounded-xs bg-neutral-500"></div>
			<div class="flex h-full flex-col items-start justify-center">
				<span class="leading-6 tracking-tight text-neutral-200">Out In Myself</span>
				<div class="flex gap-1">
					<div class="flex h-4 items-center gap-0.5">
						<UserFilled class="size-3 fill-neutral-400" />
						<span class="text-xs leading-4 tracking-tight text-neutral-400">
							Men I Trust
						</span>
					</div>
					<div class="flex h-4 items-center gap-0.5 border-blue-600 hover:border-b">
						<DiscFilled class="size-3 fill-neutral-400" />
						<span class="text-xs leading-4 tracking-tight text-neutral-400"
							>Headroom</span
						>
					</div>
				</div>
			</div>
		</div>
		<!-- Player controls -->
		<div class="flex h-full flex-col items-center justify-center bg-neutral-950">
			<div class="flex h-8 items-center">
				<!-- Skip back -->
				<button class="flex w-8 items-center justify-center" title="">
					<PlayerSkipBackFilled class="size-5 fill-neutral-400" />
				</button>
				<!-- Toggle playback -->
				<button class="flex w-10 items-center justify-center" title="">
					<PlayerPlayFilled class="size-7 fill-neutral-200" />
				</button>
				<!-- Skip forward -->
				<button class="flex w-8 items-center justify-center" title="">
					<PlayerSkipForwardFilled class="size-5 fill-neutral-400" />
				</button>
			</div>
			<div class="flex h-6 w-full items-center gap-2 bg-neutral-950">
				<span class="ml-auto text-sm text-neutral-400 tabular-nums">0:00</span>
				<Slider
					class=" **:data-[slot=slider-range]:bg-neutral-200 **:data-[slot=slider-thumb]:size-3 **:data-[slot=slider-thumb]:bg-neutral-200 **:data-[slot=slider-track]:h-1 **:data-[slot=slider-track]:bg-neutral-800"
					type="single"
					max={100}
					value={0}
					step={0.1}
				/>
				<span class="ml-auto text-sm font-medium text-neutral-400 tabular-nums">
					3:00
				</span>
			</div>
		</div>
		<!-- Volume control -->
		<div class="flex items-center justify-end gap-2 bg-neutral-950">
			<Volume class="size-7 fill-neutral-400" />
			<Slider
				class="w-24 **:data-[slot=slider-range]:bg-blue-600 **:data-[slot=slider-thumb]:bg-neutral-200 **:data-[slot=slider-track]:h-1 **:data-[slot=slider-track]:bg-neutral-800"
				type="single"
				max={100}
				value={50}
				step={0.1}
			/>
		</div>
	</nav>
{/snippet}
