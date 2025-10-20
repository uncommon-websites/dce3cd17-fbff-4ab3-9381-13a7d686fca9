<script lang="ts">
	// Components
	import Summary from "$lib/components/layout/Summary.svelte";
	import Features from "$lib/components/layout/Features.svelte";
	import Testimonials from "$lib/components/layout/Testimonials.svelte";
	import CallToAction from "$lib/components/layout/CallToAction.svelte";
	import AboutTeaser from "$lib/components/layout/AboutTeaser.svelte";
	import LogoScroller from "$lib/components/layout/LogoScroller.svelte";
	import Hero from "$lib/components/layout/hero-sections/Hero.svelte";

	// Icons
	import IconFlask from "~icons/lucide/flask-conical";
	import IconCalendarClock from "~icons/lucide/calendar-clock";
	import IconTestTube from "~icons/lucide/test-tube";
	import IconSparkles from "~icons/lucide/sparkles";
	import IconShieldCheck from "~icons/lucide/shield-check";
	import IconHeartHandshake from "~icons/lucide/heart-handshake";
</script>

<Hero
	title="Balanced hormones, reclaimed energy"
	subtitle="Bioidentical prescriptions and cycle-synced care designed to relieve your symptoms and restore your wellbeing."
	imageSrc="/generated/image-a-professional-woman-standing-outdoors-e.webp"
	centered={false}
	callsToAction={[
		{
			href: "/start",
			label: "Start your journey"
		},
		{
			href: "/how-it-works",
			label: "How it works"
		}
	]}
/>
<LogoScroller
	label="Trusted by women's health leaders"
	logoUrls={[
		'https://cdn.brandfetch.io/oura.com/w/400/h/400/logo',
		'https://cdn.brandfetch.io/notion.so/w/400/h/400/logo',
		'https://cdn.brandfetch.io/calm.com/w/400/h/400/logo',
		'https://cdn.brandfetch.io/ritual.com/w/400/h/400/logo'
	]}
/>

<Summary
	title="Hormone care, simplified"
	text="Cycles brings together bioidentical prescriptions, targeted supplements, and lifestyle guidance in one integrated platform. We serve women experiencing hormonal symptoms who deserve precision care without juggling multiple providers.

Instead of navigating fragmented appointments and conflicting advice, you receive personalized treatment synchronized with your natural cycle—backed by at-home lab testing and continuous optimization."
/>

<Testimonials
	testimonials={[
		{
			name: "Elena Rodriguez",
			position: "Marketing Director",
			company: "San Francisco",
			quote:
				"I spent eighteen months bouncing between three different doctors trying to manage my perimenopause symptoms. With Cycles, I had a personalized treatment plan within two weeks and felt noticeably better by week four. The time I've saved not coordinating between multiple providers has been life-changing.",
			image: "/generated/image-a-professional-woman-in-her-30s-smiling-.webp"
		},
		{
			name: "Maya Patel",
			position: "Senior Consultant",
			company: "Chicago",
			quote:
				"After a bad experience with synthetic hormones, I was terrified to try anything else. Cycles gave me confidence through comprehensive lab testing and bioidentical prescriptions tailored to my exact hormone levels. No more guessing or trial-and-error with my health at stake.",
			image: "/generated/image-a-confident-professional-woman-in-her-40.webp"
		},
		{
			name: "Nora Chen",
			position: "Finance Manager",
			company: "Austin",
			quote:
				"I was paying separately for my doctor visits, lab work, supplements, and prescription refills from four different places. Cycles integrated everything into one monthly membership that costs less than what I was spending before, and the care is far more coordinated and effective.",
			image: "/generated/image-a-professional-woman-in-her-mid-30s-radi.webp"
		}
	]}
/>

<Features
	title="Hormone care designed for you"
	subtitle="Everything you need to optimize your hormones and reclaim your energy in one integrated platform"
	features={[
		{
			title: "Bioidentical prescriptions",
			description:
				"Get hormone therapy that works with your body, not against it. Our bioidentical prescriptions mirror your natural hormones to deliver relief without the risks of synthetic alternatives.",
			icon: IconFlask
		},
		{
			title: "Cycle-synced care",
			description:
				"Your hormones change throughout your cycle—your care should too. We synchronize your prescriptions, supplements, and lifestyle programs to match your body's natural rhythm.",
			icon: IconCalendarClock
		},
		{
			title: "At-home lab testing",
			description:
				"Skip the clinic and get precise hormone insights from home. Our comprehensive testing reveals exactly what your body needs for personalized, data-driven care.",
			icon: IconTestTube
		},
		{
			title: "Integrated ecosystem",
			description:
				"No more juggling multiple providers and conflicting advice. Cycles combines prescriptions, supplements, and lifestyle programs in one seamless platform.",
			icon: IconSparkles
		},
		{
			title: "FDA-compliant care",
			description:
				"Get the quality and safety you deserve without the hassle. Our prescriptions meet rigorous FDA standards while remaining accessible and stigma-free.",
			icon: IconShieldCheck
		},
		{
			title: "Expert guidance",
			description:
				"Never navigate hormone care alone again. Our specialized care team provides personalized support every step of your journey to hormonal balance.",
			icon: IconHeartHandshake
		}
	]}
/>
<AboutTeaser />
<CallToAction
	title="Start feeling like yourself again"
	subtitle="Your first month of care begins in minutes"
	description="Take the at-home hormone test, receive your personalized bioidentical prescription, and join thousands of women who've reclaimed their energy. No more fragmented care or synthetic hormones you don't trust."
	imageSrc="/generated/image-a-woman-in-casual-comfortable-clothing-e.webp"
	callsToAction={[
		{
			href: "/start",
			label: "Begin your assessment",
			variant: "primary"
		},
		{
			href: "/how-it-works",
			label: "See how it works",
			variant: "secondary"
		}
	]}
/>
