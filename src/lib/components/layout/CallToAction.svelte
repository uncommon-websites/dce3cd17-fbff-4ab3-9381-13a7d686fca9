<!--
    @component
    A call-to-action component that attracts attention and encourages user engagement.

    Usage:
    ```html
    <CallToAction
      title="Get started today"
      subtitle="Join now"
      description="Ready to experience the difference? Join our community of satisfied customers and see how our solution can transform your workflow."
      image="https://www.unc.mn/image-placeholder.svg"
      callsToAction={[
        {
          href: "/get-started",
          label: "Get Started",
          variant: "primary"
        },
        {
          href: "/contact",
          label: "Talk to Sales",
          variant: "secondary"
        }
      ]}
    />
    ```

    Props:
    - `title`: The main heading text (string)
    - `subtitle`: Secondary heading text (string)
    - `description`: Detailed information about the offer (string)
    - `callsToAction`: Array of CTA objects with href, label, and optional variant properties (CTA[])
    - `imageSrc`: portrait of the company's customer smiling at the camera.
-->

<script lang="ts">
	// Types
	import type { ComponentProps } from "svelte";

	// Components
	import Button from "../ui/Button.svelte";
	import AnimateText from "../animation/AnimateText.svelte";
	import { cta } from "$lib/navigation";

	// Types
	type CTA = {
		href: string;
		label: string;
		variant?: ComponentProps<typeof Button>["variant"];
	};

	// Props
	const {
		title = "Get started today",
		subtitle = "Join now",
		description = "Ready to experience the difference? Join our community of satisfied customers and see how our solution can transform your workflow. ",
		imageSrc = "https://www.unc.mn/image-placeholder.svg",
		callsToAction = [cta],
		...rest
	}: {
		title?: string;
		subtitle?: string;
		description?: string;
		imageSrc?: string;
		callsToAction?: CTA[];
		[key: string]: any;
	} = $props();
</script>

<div class="relative overflow-hidden" {...rest}>
	<!-- Background gradient -->
	<div class="absolute inset-0 bg-gradient-to-br from-primary-50 via-white to-secondary-50"></div>
	<div class="absolute top-1/4 right-1/3 h-96 w-96 rounded-full bg-primary-200/20 blur-3xl"></div>
	
	<section class="section-px section-py container relative z-10 mx-auto">
		<div
			class="glass relative grid content-start items-center justify-between gap-(--gap) overflow-hidden rounded-2xl p-(--gap) text-balance [--gap:--spacing(8)] [--inner-radius:calc(var(--radius)-var(--gap))] [--radius:var(--radius-xl)] lg:grid-cols-[2fr_1fr]"
		>
			<!-- Subtle gradient overlay -->
			<div class="absolute inset-0 -z-10 bg-gradient-to-br from-white/80 to-primary-50/30"></div>
			
			<div class="items-between grid h-full content-between gap-16">
				<h2 class="text-title1 mb-3 flex flex-col font-bold tracking-tight">
					<span class="text-gradient"><AnimateText text={title} /></span>
					<span class="text-emphasis-medium"><AnimateText text={subtitle} /></span>
				</h2>
				<div class="flex flex-col items-start justify-start gap-7">
					<p class="text-headline text-muted-foreground leading-relaxed">
						{description}
					</p>
					<div class="flex w-full flex-col gap-3 md:flex-row md:flex-wrap">
						{#each callsToAction as cta}
							<Button class="glow-primary w-full md:w-auto" href={cta.href} variant={cta.variant || "primary"}
								>{cta.label}</Button
							>
						{/each}
					</div>
				</div>
			</div>
			<div class="glass hidden overflow-hidden rounded-xl lg:block">
				<img
					src={imageSrc}
					alt="Visual comparison showing product benefits"
					class="aspect-[4/5] size-full max-h-full w-full object-cover"
				/>
			</div>
		</div>
	</section>
</div>
