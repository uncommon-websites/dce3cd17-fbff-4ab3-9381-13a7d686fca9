<!--
    @component
    Bold hero banner with eye-catching text and strong call-to-action. NEVER use title case.

    Usage:
    ```html
    <Hero
      title="Bold Claim"
      subtitle="Quick Value"
      imageSrc="https://www.unc.mn/image-placeholder.svg"
      callsToAction={[
        {
          href: "/start",
          label: "Go"
        },
        {
          href: "/learn",
          label: "More"
        }
      ]}
    />
    ```

    Props:
    - `title`: Main headline (string)
    - `subtitle`: Supporting text (string)
    - `imageSrc`: Hero image URL (string)
    - `callsToAction`: CTA buttons array (max two: primary, secondary)
-->

<script lang="ts">
	// Components
	import AnimateText from "$lib/components/animation/AnimateText.svelte";
	import Button from "$lib/components/ui/Button.svelte";

	// Constants
	import { cta } from "$lib/navigation";

	function handleImageError(e: Event) {
		const target = e.currentTarget as HTMLImageElement;
		target.src = "https://placehold.co/800x600/f8fafc/64748b?text=Hero+image";
	}

	// Types
	type Props = {
		centered?: boolean;
		title: string;
		subtitle: string;
		imageSrc?: string;
		callsToAction?: Array<{
			href: string;
			label: string;
		}>; // A maximum of two calls to action, with the first one being primary and the second one being secondary
		[key: string]: any;
	};

	let {
		title,
		subtitle,
		imageSrc,
		callsToAction = [cta],
		centered = false,
		...rest
	}: Props = $props();
</script>

<div class="relative overflow-hidden bg-gradient-to-br from-primary-50 via-white to-secondary-50" {...rest}>
	<!-- Tech Grid Background -->
	<div class="tech-grid absolute inset-0 opacity-30"></div>
	
	<!-- Gradient Orbs -->
	<div class="absolute top-0 right-1/4 h-96 w-96 rounded-full bg-primary-200/30 blur-3xl"></div>
	<div class="absolute bottom-0 left-1/4 h-96 w-96 rounded-full bg-secondary-200/30 blur-3xl"></div>

	<header
		class={[
			"section-px container relative z-10 mx-auto grid items-end gap-16 gap-y-9 py-12 pt-24 text-balance",
			centered ? "place-items-center text-center" : " xl:grid-cols-[1fr_auto]"
		]}
		data-enter-container
	>
		<div class="grid gap-6" class:max-w-prose={centered}>
			<h1 class="text-display w-full font-bold tracking-tight" data-enter>
				<span class="block text-gradient"><AnimateText text={title} /></span>
				{#if !centered}
					<span class="text-emphasis-medium block"><AnimateText text={subtitle} /></span>
				{/if}
			</h1>

			{#if centered}
				<p
					data-enter
					class={[
						"text-muted-foreground text-headline mx-auto block max-w-[45ch] transition duration-500 ease-out"
					]}
				>
					{subtitle}
				</p>
			{/if}
		</div>

		{#if callsToAction.length > 0}
			<div class="flex gap-4" data-enter>
				{#each callsToAction as cta, index}
					<Button
						href={cta.href}
						size="lg"
						variant={index % 2 === 0 ? "primary" : "secondary"}
						class="max-lg:hidden glow-primary">{cta.label}</Button
					>
					<Button
						href={cta.href}
						size="md"
						variant={index % 2 === 0 ? "primary" : "secondary"}
						class="lg:hidden glow-primary">{cta.label}</Button
					>
				{/each}
			</div>
		{/if}
	</header>

	{#if imageSrc}
		<div class="section-px container relative z-10 mx-auto pb-12" data-enter>
			<div class="glass relative overflow-hidden rounded-2xl p-2">
				<img
					src={imageSrc}
					alt="Customer"
					class="size-full rounded-xl object-cover"
					onerror={handleImageError}
				/>
			</div>
		</div>
	{/if}
</div>
