<script lang="ts">
	import type { Component } from "svelte";

	interface Props {
		title?: string;
		description?: string;
		icon?: Component;
		iconClass?: string;
		imageSrc?: string;
		imageAspect?: "16/9" | "9/16";
		class?: string;
	}

	let {
		title = "",
		description = "",
		icon,
		iconClass = "size-5 text-primary",
		imageSrc,
		imageAspect = "16/9",
		class: customClass = ""
	}: Props = $props();
</script>

<article
	class="card-modern group relative flex flex-col overflow-hidden p-6 text-pretty lg:p-8 {customClass}"
>
	<!-- Gradient overlay on hover -->
	<div class="absolute inset-0 -z-10 bg-gradient-to-br from-primary-50/50 to-secondary-50/50 opacity-0 transition-opacity duration-300 group-hover:opacity-100"></div>
	
	{#if icon || imageSrc}
		<div class="mb-6">
			{#if icon && imageSrc}
				{@const Icon = icon}
				<div class="relative">
					<img
						src={imageSrc}
						alt={title}
						class="w-full rounded-lg object-cover {imageAspect === '9/16' ? 'aspect-[9/16]' : 'aspect-[16/9]'}"
					/>
					<div
						class="glass absolute top-3 left-3 rounded-md p-2"
					>
						<Icon
							class="size-5 text-primary"
						/>
					</div>
				</div>
			{:else if icon}
				{@const Icon = icon}
				<div class="inline-flex rounded-lg bg-gradient-to-br from-primary-100 to-secondary-100 p-3">
					<Icon class="size-6 text-primary-700" />
				</div>
			{:else if imageSrc}
				<img
					src={imageSrc}
					alt={title}
					class="w-full rounded-lg object-cover {imageAspect === '9/16' ? 'aspect-[9/16]' : 'aspect-[16/9]'}"
				/>
			{/if}
		</div>
	{/if}

	<div class:mt-auto={icon || imageSrc}>
		<h3 class="text-title3 mb-3 font-semibold tracking-tight">
			{title}
		</h3>
		<p class="text-body text-muted-foreground max-w-prose leading-relaxed">{description}</p>
	</div>
</article>
