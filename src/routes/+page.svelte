<script lang="ts">
	import { Github, Download, Menu, X } from 'lucide-svelte';

	let mobileMenuOpen = $state(false);

	// Intersection Observer action for scroll-triggered animations
	function reveal(node: HTMLElement, options: { delay?: number; threshold?: number } = {}) {
		const { delay = 0, threshold = 0.15 } = options;

		node.style.opacity = '0';
		node.style.transform = 'translateY(24px)';
		node.style.transition = `opacity 0.7s cubic-bezier(0.16, 1, 0.3, 1) ${delay}ms, transform 0.7s cubic-bezier(0.16, 1, 0.3, 1) ${delay}ms`;

		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						node.style.opacity = '1';
						node.style.transform = 'translateY(0)';
						observer.unobserve(node);
					}
				});
			},
			{ threshold }
		);

		observer.observe(node);

		return {
			destroy() {
				observer.disconnect();
			}
		};
	}
</script>

<svelte:head>
	<title>Cignaler — Desktop CI Pipeline Monitor for GitLab</title>
	{@html `<script type="application/ld+json">${JSON.stringify({
		"@context": "https://schema.org",
		"@graph": [
			{
				"@type": "SoftwareApplication",
				"name": "Cignaler",
				"description": "Cignaler is a free, open-source desktop application that monitors GitLab CI/CD pipelines from your system tray. Built with Tauri 2 and Rust, it polls your pipelines and sends native notifications when builds fail.",
				"applicationCategory": "DeveloperApplication",
				"operatingSystem": "macOS",
				"offers": { "@type": "Offer", "price": "0", "priceCurrency": "USD" },
				"downloadUrl": "https://github.com/cignaler/cignaler/releases/latest/download/Cignaler.dmg",
				"url": "https://cignaler.github.io",
				"softwareVersion": "0.0.1",
				"author": { "@type": "Organization", "name": "Cignaler", "url": "https://cignaler.github.io" }
			},
			{
				"@type": "Organization",
				"name": "Cignaler",
				"url": "https://cignaler.github.io",
				"logo": "https://cignaler.github.io/cignaler_icon.png",
				"sameAs": ["https://github.com/cignaler/cignaler"]
			},
			{
				"@type": "WebPage",
				"name": "Cignaler — Desktop CI Pipeline Monitor for GitLab",
				"description": "Cignaler is a free, open-source desktop application that monitors GitLab CI/CD pipelines from your system tray.",
				"url": "https://cignaler.github.io"
			},
			{
				"@type": "FAQPage",
				"mainEntity": [
					{
						"@type": "Question",
						"name": "What is Cignaler?",
						"acceptedAnswer": { "@type": "Answer", "text": "Cignaler is a free, open-source desktop application that monitors GitLab CI/CD pipelines from your system tray. Built with Tauri 2 and Rust, it polls your pipelines every 60 seconds and sends native notifications when builds fail — so you never have to keep a CI dashboard tab open." }
					},
					{
						"@type": "Question",
						"name": "What CI platforms does Cignaler support?",
						"acceptedAnswer": { "@type": "Answer", "text": "Cignaler currently supports GitLab CI/CD. Support for GitHub Actions and Jenkins is planned." }
					},
					{
						"@type": "Question",
						"name": "Is Cignaler free?",
						"acceptedAnswer": { "@type": "Answer", "text": "Yes, Cignaler is completely free and open source." }
					},
					{
						"@type": "Question",
						"name": "What platforms does Cignaler run on?",
						"acceptedAnswer": { "@type": "Answer", "text": "Cignaler is currently available for macOS. Windows and Linux support is coming soon." }
					},
					{
						"@type": "Question",
						"name": "How does Cignaler work?",
						"acceptedAnswer": { "@type": "Answer", "text": "Cignaler runs as a system tray application. You create watchers for specific GitLab projects and branches. It polls your pipelines every 60 seconds and sends native desktop notifications when a build fails. Results are cached locally in SQLite." }
					},
					{
						"@type": "Question",
						"name": "Does Cignaler collect any data?",
						"acceptedAnswer": { "@type": "Answer", "text": "No. Cignaler is fully local — all data stays on your machine. There is no telemetry, analytics, or external data collection of any kind." }
					}
				]
			}
		]
	})}</script>`}
</svelte:head>

<!-- Navigation Header -->
<header class="sticky top-0 z-50 w-full border-b border-warm-200/60 bg-white/80 backdrop-blur-md">
	<div class="container mx-auto px-4 md:px-6">
		<div class="flex h-16 items-center justify-between">
			<!-- Logo -->
			<div class="flex items-center gap-2">
				<img src="/cignaler_icon.png" alt="Cignaler" class="h-8 w-8 rounded-lg" />
				<span class="font-display text-xl font-bold tracking-tight text-warm-900">Cignaler</span>
			</div>

			<!-- Navigation Links (Desktop) -->
			<nav class="hidden md:flex items-center gap-8 text-sm font-medium text-warm-500">
				<a href="#features" class="transition-colors hover:text-warm-900">Features</a>
				<a href="#how-it-works" class="transition-colors hover:text-warm-900">How it works</a>
				<a href="https://github.com/cignaler/cignaler" target="_blank" rel="noopener noreferrer" class="transition-colors hover:text-warm-900">GitHub</a>
			</nav>

			<!-- CTA + Mobile Toggle -->
			<div class="flex items-center gap-3">
				<a href="https://github.com/cignaler/cignaler/releases/latest/download/Cignaler.dmg" class="hidden sm:flex items-center justify-center whitespace-nowrap rounded-lg font-display font-semibold transition-colors h-9 px-4 text-sm bg-warm-900 text-white hover:bg-warm-800 shadow-sm">
					Download Cignaler
				</a>
				<button
					class="flex md:hidden items-center justify-center h-9 w-9 rounded-lg text-warm-600 hover:bg-warm-100 transition-colors"
					onclick={() => (mobileMenuOpen = !mobileMenuOpen)}
					aria-label="Toggle menu"
				>
					{#if mobileMenuOpen}
						<X class="h-5 w-5" />
					{:else}
						<Menu class="h-5 w-5" />
					{/if}
				</button>
			</div>
		</div>

		<!-- Mobile Menu -->
		{#if mobileMenuOpen}
			<nav class="md:hidden border-t border-warm-200/60 py-4 space-y-1">
				<a href="#features" class="block px-2 py-2 text-sm font-medium text-warm-600 hover:text-warm-900 rounded-lg hover:bg-warm-50 transition-colors" onclick={() => (mobileMenuOpen = false)}>Features</a>
				<a href="#how-it-works" class="block px-2 py-2 text-sm font-medium text-warm-600 hover:text-warm-900 rounded-lg hover:bg-warm-50 transition-colors" onclick={() => (mobileMenuOpen = false)}>How it works</a>
				<a href="https://github.com/cignaler/cignaler" target="_blank" rel="noopener noreferrer" class="block px-2 py-2 text-sm font-medium text-warm-600 hover:text-warm-900 rounded-lg hover:bg-warm-50 transition-colors">GitHub</a>
				<div class="pt-2">
					<a href="https://github.com/cignaler/cignaler/releases/latest/download/Cignaler.dmg" class="w-full flex items-center justify-center rounded-lg font-display font-semibold h-10 text-sm bg-warm-900 text-white hover:bg-warm-800">
						Download Cignaler
					</a>
				</div>
			</nav>
		{/if}
	</div>
</header>

<main>

<!-- Hero Section -->
<section class="relative overflow-hidden bg-white pt-24 md:pt-32 pb-32 md:pb-40 selection:bg-brand-500/20">
	<!-- Dot grid background only (removed glow blobs) -->
	<div
		class="absolute inset-0 -z-10 h-full w-full bg-white bg-[radial-gradient(#e8e6e1_1px,transparent_1px)] [background-size:20px_20px] [mask-image:radial-gradient(ellipse_60%_50%_at_50%_40%,#000_70%,transparent_100%)]"
	></div>

	<div class="container mx-auto px-4 md:px-6 relative z-10">
		<!-- Hero Content -->
		<div class="flex flex-col items-center text-center max-w-5xl mx-auto mb-24">
			<!-- Badge -->
			<div class="mb-8" use:reveal>
				<div
					class="inline-flex items-center gap-2 rounded-full border border-warm-200 bg-white/60 backdrop-blur-sm px-4 py-1.5 text-sm font-medium text-warm-900 shadow-sm"
				>
					<span class="relative flex h-2 w-2">
						<span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-accent-400 opacity-75"></span>
						<span class="relative inline-flex rounded-full h-2 w-2 bg-accent-500"></span>
					</span>
					<span class="text-warm-500">Early Access</span>
					<span class="font-semibold text-brand-600">Desktop CI Monitor</span>
				</div>
			</div>

			<!-- Main Heading -->
			<h1
				class="font-display text-5xl md:text-7xl lg:text-8xl font-bold tracking-tight text-warm-900 mb-8 leading-[1.05]"
				use:reveal={{ delay: 100 }}
			>
				Stop staring at
				<br />
				<span class="relative inline-block text-brand-600 pb-2">
					broken pipelines.
					<svg
						class="absolute w-full h-4 -bottom-1 left-0 text-brand-500/30"
						viewBox="0 0 100 10"
						preserveAspectRatio="none"
					>
						<path d="M0 5 Q 50 10 100 5" stroke="currentColor" stroke-width="3" fill="none" />
					</svg>
				</span>
			</h1>

			<!-- Subheading -->
			<p
				class="text-xl md:text-2xl text-warm-500 max-w-2xl mx-auto mb-10 leading-relaxed"
				use:reveal={{ delay: 200 }}
			>
				Cignaler filters the noise. Get notified only when the builds
				<span class="text-warm-900 font-semibold">you care about</span> actually break.
			</p>

			<!-- CTAs -->
			<div class="flex flex-col sm:flex-row items-center gap-4" use:reveal={{ delay: 300 }}>
				<a
					href="https://github.com/cignaler/cignaler/releases/latest/download/Cignaler.dmg"
					class="h-14 px-8 text-lg rounded-full bg-brand-500 text-white font-display font-semibold shadow-xl shadow-brand-500/20 hover:shadow-brand-500/30 hover:bg-brand-600 transition-all hover:scale-[1.03] flex items-center gap-2"
				>
					<Download class="h-5 w-5" />
					Download Cignaler
				</a>
				<a
					href="https://github.com/cignaler/cignaler"
					target="_blank"
					rel="noopener noreferrer"
					class="h-14 px-8 text-lg rounded-full border-2 border-warm-300 bg-white text-warm-900 font-display font-semibold hover:bg-warm-50 transition-all flex items-center gap-2"
				>
					<Github class="h-5 w-5" />
					Star on GitHub
				</a>
			</div>

			<!-- Platform availability -->
			<div class="mt-6" use:reveal={{ delay: 400 }}>
				<p class="text-sm text-warm-400">Available for macOS · Windows & Linux coming soon</p>
			</div>

			<!-- What is Cignaler (GEO: factual entity description for AI search engines) -->
			<p class="mt-8 text-sm text-warm-500 max-w-2xl mx-auto leading-relaxed" use:reveal={{ delay: 500 }}>
				Cignaler is a free, open-source desktop application that monitors GitLab CI/CD pipelines from your system tray. Built with Tauri 2 and Rust, it polls your pipelines and sends native notifications when builds fail — so you never have to keep a CI dashboard tab open. Unlike browser-based CI dashboards, Cignaler runs natively on your desktop with minimal resource usage.
			</p>
		</div>

		<!-- Product Screenshot -->
		<div class="relative max-w-5xl mx-auto" use:reveal={{ delay: 200 }}>
			<div class="relative group">
				<!-- Glow Effect Behind Screenshot -->
				<div
					class="absolute inset-0 bg-gradient-to-tr from-brand-500/20 to-accent-500/20 blur-[80px] rounded-[3rem] opacity-40 group-hover:opacity-60 transition-opacity duration-700"
				></div>

				<!-- Main Screenshot Container -->
				<div
					class="relative bg-white rounded-2xl border border-warm-200/50 shadow-2xl overflow-hidden ring-1 ring-black/5"
				>
					<!-- Window Chrome -->
					<div class="h-12 bg-warm-100/80 backdrop-blur-md border-b border-warm-200/60 flex items-center px-6 justify-between">
						<div class="flex gap-2">
							<div class="h-3 w-3 rounded-full bg-[#FF5F56] border border-[#E0443E]"></div>
							<div class="h-3 w-3 rounded-full bg-[#FFBD2E] border border-[#DEA123]"></div>
							<div class="h-3 w-3 rounded-full bg-[#27C93F] border border-[#1AAB29]"></div>
						</div>
						<div class="text-xs font-mono text-warm-500">cignaler</div>
						<div class="w-16"></div>
					</div>

					<!-- Dashboard Content -->
					<div class="relative aspect-[16/10] bg-white w-full overflow-hidden">
						<div class="flex h-full">
							<!-- Sidebar -->
							<div class="w-52 border-r border-warm-200 bg-warm-50 hidden sm:flex flex-col">
								<div class="p-4 flex items-center gap-2.5">
									<img src="/cignaler_icon.png" alt="" class="h-8 w-8 rounded-lg" />
									<div>
										<div class="text-sm font-bold text-warm-900 leading-tight">Cignaler</div>
										<div class="text-[10px] text-warm-400 font-semibold tracking-widest uppercase">Pipelines</div>
									</div>
								</div>
								<div class="px-4 mb-3">
									<div class="w-full py-2 rounded-lg bg-brand-500 text-white text-xs font-semibold text-center">+ Add New Watcher</div>
								</div>
								<div class="px-4 mb-2">
									<div class="text-[10px] text-warm-400 font-semibold tracking-wider uppercase">Watchers <span class="ml-1 inline-flex items-center justify-center h-4 w-4 rounded bg-warm-200 text-warm-500 text-[9px] font-bold">2</span></div>
								</div>
								<div class="px-3 space-y-1">
									<div class="flex items-center gap-2.5 px-2 py-2 rounded-lg">
										<div class="h-2 w-2 rounded-full bg-green-500 shrink-0"></div>
										<div class="min-w-0">
											<div class="text-xs text-warm-900 font-medium truncate">fix-pipeline-caching</div>
											<div class="text-[10px] text-warm-400">Monitoring</div>
										</div>
									</div>
									<div class="flex items-center gap-2.5 px-2 py-2 rounded-lg">
										<div class="h-2 w-2 rounded-full bg-green-500 shrink-0"></div>
										<div class="min-w-0">
											<div class="text-xs text-warm-900 font-medium truncate">improve-ui-performance</div>
											<div class="text-[10px] text-warm-400">Monitoring</div>
										</div>
									</div>
								</div>
								<div class="mt-auto p-4">
									<div class="text-[10px] text-warm-300">v0.0.1</div>
								</div>
							</div>

							<!-- Main content -->
							<div class="flex-1 flex flex-col min-w-0">
								<!-- Header -->
								<div class="p-5 pb-3 border-b border-warm-100">
									<div class="flex items-center justify-between mb-1">
										<div class="flex items-center gap-3">
											<div class="text-lg font-bold text-warm-900">fix-pipeline-caching</div>
											<span class="inline-flex items-center gap-1 rounded-full bg-green-100 px-2.5 py-0.5 text-[10px] font-semibold text-green-700"><span class="h-1.5 w-1.5 rounded-full bg-green-500"></span> Active</span>
										</div>
										<div class="text-[10px] text-warm-400 hidden md:block">Last sync: 07/02/2026, 00:07:54</div>
									</div>
									<div class="text-xs text-warm-400">acmecorp/acme @ cig-3222-fix-pipeline-caching</div>
								</div>

								<!-- Pipeline list -->
								<div class="flex-1 overflow-hidden">
									<div class="divide-y divide-warm-100">
										<!-- Row 1 - Success -->
										<div class="flex items-center px-5 py-3 gap-4">
											<div class="w-1 self-stretch rounded-full bg-green-400"></div>
											<span class="inline-flex items-center gap-1 rounded-md bg-green-100 px-2 py-0.5 text-[10px] font-semibold text-green-700 shrink-0"><span class="text-green-500">&#10003;</span> SUCCESS</span>
											<div class="flex-1 min-w-0">
												<div class="text-xs font-medium text-warm-800 truncate">refs/merge-requests/16883/train</div>
												<div class="text-[10px] text-warm-400 truncate">merge_request_event &middot; 3bc39d4 &middot; 3h ago</div>
											</div>
											<div class="text-[10px] text-warm-400 shrink-0 hidden md:block">Jan 29</div>
											<div class="text-[10px] text-brand-500 font-medium shrink-0 hidden md:block">Details</div>
										</div>
										<!-- Row 2 - Cancelled -->
										<div class="flex items-center px-5 py-3 gap-4">
											<div class="w-1 self-stretch rounded-full bg-green-400"></div>
											<span class="inline-flex items-center gap-1 rounded-md bg-warm-100 px-2 py-0.5 text-[10px] font-semibold text-warm-500 shrink-0"><span class="text-warm-400">&bull;</span> CANCELLED</span>
											<div class="flex-1 min-w-0">
												<div class="text-xs font-medium text-warm-800 truncate">refs/merge-requests/16883/train</div>
												<div class="text-[10px] text-warm-400 truncate">merge_request_event &middot; fbc3c34 &middot; 3h ago</div>
											</div>
											<div class="text-[10px] text-warm-400 shrink-0 hidden md:block">Jan 29</div>
											<div class="text-[10px] text-brand-500 font-medium shrink-0 hidden md:block">Details</div>
										</div>
										<!-- Row 3 - Failed -->
										<div class="flex items-center px-5 py-3 gap-4 bg-red-50/50">
											<div class="w-1 self-stretch rounded-full bg-green-400"></div>
											<span class="inline-flex items-center gap-1 rounded-md bg-red-100 px-2 py-0.5 text-[10px] font-semibold text-red-600 shrink-0"><span class="text-red-500">&bull;</span> FAILED</span>
											<div class="flex-1 min-w-0">
												<div class="text-xs font-medium text-warm-800 truncate">refs/merge-requests/16883/train</div>
												<div class="text-[10px] text-warm-400 truncate">merge_request_event &middot; 2899439 &middot; 3h ago</div>
											</div>
											<div class="text-[10px] text-warm-400 shrink-0 hidden md:block">Jan 29</div>
											<div class="text-[10px] text-brand-500 font-medium shrink-0 hidden md:block">Details</div>
										</div>
										<!-- Row 4 - Cancelled -->
										<div class="flex items-center px-5 py-3 gap-4">
											<div class="w-1 self-stretch rounded-full bg-green-400"></div>
											<span class="inline-flex items-center gap-1 rounded-md bg-warm-100 px-2 py-0.5 text-[10px] font-semibold text-warm-500 shrink-0"><span class="text-warm-400">&bull;</span> CANCELLED</span>
											<div class="flex-1 min-w-0">
												<div class="text-xs font-medium text-warm-800 truncate">refs/merge-requests/16883/train</div>
												<div class="text-[10px] text-warm-400 truncate">merge_request_event &middot; 938165d &middot; 4h ago</div>
											</div>
											<div class="text-[10px] text-warm-400 shrink-0 hidden md:block">Jan 29</div>
											<div class="text-[10px] text-brand-500 font-medium shrink-0 hidden md:block">Details</div>
										</div>
										<!-- Row 5 - Success -->
										<div class="flex items-center px-5 py-3 gap-4">
											<div class="w-1 self-stretch rounded-full bg-green-400"></div>
											<span class="inline-flex items-center gap-1 rounded-md bg-green-100 px-2 py-0.5 text-[10px] font-semibold text-green-700 shrink-0"><span class="text-green-500">&#10003;</span> SUCCESS</span>
											<div class="flex-1 min-w-0">
												<div class="text-xs font-medium text-warm-800 truncate">eng-3222-fix-known-channel-admin-api</div>
												<div class="text-[10px] text-warm-400 truncate">external &middot; ed6df69 &middot; 36d ago</div>
											</div>
											<div class="text-[10px] text-warm-400 shrink-0 hidden md:block">Jan 29</div>
											<div class="text-[10px] text-brand-500 font-medium shrink-0 hidden md:block">Details</div>
										</div>
									</div>
								</div>
							</div>
						</div>
						<!-- Gradient Overlay -->
						<div class="absolute inset-0 bg-gradient-to-t from-white/60 to-transparent pointer-events-none"></div>
					</div>
				</div>

				<!-- Single Floating Card (simplified from two) -->
				<div
					class="absolute -left-8 top-1/3 p-4 bg-white rounded-xl shadow-[0_8px_30px_rgb(0,0,0,0.08)] border border-warm-200 hidden lg:block"
					style="animation: var(--animate-float)"
				>
					<div class="flex items-center gap-3">
						<div class="h-10 w-10 bg-green-100 rounded-lg flex items-center justify-center">
							<img src="/tray-success.svg" alt="" class="h-5 w-5" />
						</div>
						<div>
							<div class="text-xs text-warm-500 font-medium">Pipeline Passed</div>
							<div class="text-sm font-bold text-warm-900">fix-pipeline-caching</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- Social Proof / Works With Section -->
<section class="py-16 bg-warm-50 border-y border-warm-200/60">
	<div class="container mx-auto px-4 md:px-6">
		<div class="flex flex-col items-center text-center" use:reveal>
			<p class="text-sm font-medium text-warm-400 uppercase tracking-wider mb-8">Works with your CI stack</p>
			<div class="flex flex-wrap items-center justify-center gap-x-12 gap-y-6">
				<!-- GitLab CI -->
				<div class="flex items-center gap-3 text-warm-600 transition-colors relative">
					<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" class="h-6 w-6"><path d="m22 13.29-3.33-10a.42.42 0 0 0-.14-.18.38.38 0 0 0-.22-.11.39.39 0 0 0-.23.07.42.42 0 0 0-.14.18l-2.26 6.67H8.32L6.1 3.26a.42.42 0 0 0-.1-.18.38.38 0 0 0-.26-.08.39.39 0 0 0-.23.07.42.42 0 0 0-.14.18L2 13.29a.74.74 0 0 0 .27.83L12 21l9.69-6.88a.71.71 0 0 0 .31-.83Z"/></svg>
					<span class="font-display font-semibold text-lg">GitLab CI</span>
					<span class="inline-flex items-center rounded-full bg-green-100 px-2 py-0.5 text-[10px] font-semibold text-green-700">Supported</span>
				</div>
				<!-- GitHub Actions -->
				<div class="flex items-center gap-3 text-warm-400 opacity-40 transition-colors relative">
					<Github class="h-6 w-6" />
					<span class="font-display font-semibold text-lg">GitHub Actions</span>
					<span class="inline-flex items-center rounded-full bg-warm-200 px-2 py-0.5 text-[10px] font-semibold text-warm-500">Coming Soon</span>
				</div>
				<!-- Jenkins -->
				<div class="flex items-center gap-3 text-warm-400 opacity-40 transition-colors relative">
					<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" class="h-6 w-6"><rect x="3" y="3" width="18" height="18" rx="2"/><path d="M9 12h6"/><path d="M12 9v6"/></svg>
					<span class="font-display font-semibold text-lg">Jenkins</span>
					<span class="inline-flex items-center rounded-full bg-warm-200 px-2 py-0.5 text-[10px] font-semibold text-warm-500">Coming Soon</span>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- Problems Section -->
<section class="py-20 bg-white relative overflow-hidden">
	<div class="container mx-auto px-4 md:px-6 relative z-10">
		<div class="mx-auto max-w-3xl text-center mb-16" use:reveal>
			<h2 class="font-display text-4xl md:text-5xl font-bold tracking-tight text-warm-900 mb-6">
				CI dashboards are <span class="text-red-600 relative inline-block">noisy
					<svg class="absolute w-full h-3 -bottom-1 left-0 text-red-600/20" viewBox="0 0 100 10" preserveAspectRatio="none">
						<path d="M0 5 Q 50 10 100 5" stroke="currentColor" stroke-width="3" fill="none" />
					</svg>
				</span>.
			</h2>
			<p class="text-xl text-warm-500 leading-relaxed">
				Most developer tools show you the world, when all you wanted was your own backyard. Stop scrolling through hundreds of pipelines you don't own.
			</p>
		</div>

		<!-- Editorial-style problem cards (no borders, large type, illustration-forward) -->
		<div class="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
			<!-- Alert Fatigue -->
			<div class="group" use:reveal={{ delay: 0 }}>
				<div class="mb-6 h-44 bg-warm-50 rounded-2xl overflow-hidden relative flex flex-col p-4 gap-2">
					<div class="absolute inset-0 bg-gradient-to-b from-transparent via-transparent to-white/90 z-10"></div>
					<div class="h-8 w-full rounded-lg flex items-center px-3 gap-2 bg-white border border-warm-200/60">
						<div class="h-2 w-2 rounded-full bg-warm-200"></div>
						<div class="h-2 w-2/3 bg-warm-100 rounded"></div>
					</div>
					<div class="h-8 w-full rounded-lg flex items-center px-3 gap-2 bg-white border border-warm-200/60 opacity-80">
						<div class="h-2 w-2 rounded-full bg-warm-200"></div>
						<div class="h-2 w-2/3 bg-warm-100 rounded"></div>
					</div>
					<div class="h-8 w-full rounded-lg flex items-center px-3 gap-2 bg-red-50 border border-red-100 opacity-60">
						<div class="h-2 w-2 rounded-full bg-red-500"></div>
						<div class="h-2 w-2/3 bg-warm-100 rounded"></div>
					</div>
					<div class="absolute bottom-4 left-1/2 -translate-x-1/2 z-20 bg-white/90 backdrop-blur border border-warm-200 px-3 py-1 rounded-full text-[10px] font-medium text-warm-500 shadow-sm">
						+142 hidden
					</div>
				</div>
				<h3 class="font-display text-xl font-bold mb-2 text-warm-900">Alert Fatigue</h3>
				<p class="text-warm-500 text-sm leading-relaxed">
					When 50 builds are failing, you stop checking. Relevant signals get lost in the noise of global failures.
				</p>
			</div>

			<!-- Silent Failures -->
			<div class="group" use:reveal={{ delay: 100 }}>
				<div class="mb-6 h-44 bg-warm-50 rounded-2xl overflow-hidden relative flex items-center justify-center">
					<div class="relative z-10 bg-white p-4 rounded-xl shadow-lg border border-warm-200 flex items-center gap-3">
						<div class="h-8 w-8 rounded-full bg-red-100 flex items-center justify-center">
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-5 w-5 text-red-600"><circle cx="12" cy="12" r="10"></circle><path d="m15 9-6 6"></path><path d="m9 9 6 6"></path></svg>
						</div>
						<div class="text-xs">
							<div class="font-bold text-warm-900">Build Failed</div>
							<div class="text-warm-500">2 hours ago</div>
						</div>
					</div>
				</div>
				<h3 class="font-display text-xl font-bold mb-2 text-warm-900">Silent Failures</h3>
				<p class="text-warm-500 text-sm leading-relaxed">
					Critical failures on your branch can sit unnoticed for hours while you assume everything is fine.
				</p>
			</div>

			<!-- Context Switching -->
			<div class="group" use:reveal={{ delay: 200 }}>
				<div class="mb-6 h-44 bg-warm-50 rounded-2xl overflow-hidden relative">
					<div class="mt-4 ml-4 bg-white rounded-tl-lg shadow-xl border-l border-t border-warm-200 h-full relative">
						<div class="flex items-center gap-1 p-2 border-b border-warm-200 bg-warm-50 rounded-tl-lg">
							<div class="h-2 w-2 rounded-full bg-red-400"></div>
							<div class="h-2 w-2 rounded-full bg-yellow-400"></div>
							<div class="h-2 w-2 rounded-full bg-green-400"></div>
						</div>
						<div class="p-3">
							<div class="h-2 w-1/3 bg-warm-100 rounded mb-2"></div>
							<div class="h-2 w-1/2 bg-warm-100 rounded"></div>
						</div>
						<div class="absolute -top-3 -right-4 bg-warm-800 text-white p-2 rounded-lg shadow-lg text-[10px] font-mono">
							Checking...
						</div>
					</div>
				</div>
				<h3 class="font-display text-xl font-bold mb-2 text-warm-900">Context Switching</h3>
				<p class="text-warm-500 text-sm leading-relaxed">
					Constantly tabbing back to GitHub/GitLab breaks your flow. It takes 15 minutes to recover focus.
				</p>
			</div>
		</div>
	</div>
</section>

<!-- Solution Section -->
<section id="how-it-works" class="py-20 bg-warm-50/50">
	<div class="container mx-auto px-4 md:px-6">
		<div class="relative rounded-[2rem] bg-warm-900 border border-warm-800 overflow-hidden shadow-2xl">
			<div class="absolute top-0 right-0 w-[500px] h-[500px] bg-brand-500/10 rounded-full blur-[100px] pointer-events-none"></div>
			<div class="absolute bottom-0 left-0 w-[500px] h-[500px] bg-accent-500/10 rounded-full blur-[100px] pointer-events-none"></div>

			<div class="relative z-10 p-8 md:p-16">
				<div class="grid lg:grid-cols-2 gap-12 items-center">
					<div class="text-left">
						<div class="inline-flex items-center gap-2 rounded-full bg-white/10 border border-white/10 px-4 py-1.5 text-sm font-medium text-white mb-8 backdrop-blur-md" use:reveal>
							<span class="relative flex h-2 w-2">
								<span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-accent-400 opacity-75"></span>
								<span class="relative inline-flex rounded-full h-2 w-2 bg-accent-500"></span>
							</span>
							The Solution
						</div>
						<h2 class="font-display text-3xl md:text-5xl font-bold tracking-tight text-white mb-6 leading-tight" use:reveal={{ delay: 100 }}>
							Focus on <span class="text-transparent bg-clip-text bg-gradient-to-r from-brand-400 to-accent-400">your work</span>, not the dashboard.
						</h2>
						<p class="text-lg text-warm-400 mb-10 leading-relaxed" use:reveal={{ delay: 200 }}>
							Cignaler filters out the noise. Create watchers to track specific projects and branches you care about. When something breaks, you'll know. Otherwise, silence is golden.
						</p>

						<div class="space-y-6">
							<div class="flex gap-4" use:reveal={{ delay: 250 }}>
								<div class="mt-1 h-6 w-6 rounded-full bg-brand-500/20 flex items-center justify-center shrink-0 border border-brand-500/20">
									<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-3.5 w-3.5 text-brand-400"><path d="M20 6 9 17l-5-5"></path></svg>
								</div>
								<div>
									<h4 class="text-base font-semibold text-white mb-1">Curated Watchers</h4>
									<p class="text-sm text-warm-400">Select a CI server, pick a project, choose a branch &mdash; only see pipelines that matter.</p>
								</div>
							</div>
							<div class="flex gap-4" use:reveal={{ delay: 300 }}>
								<div class="mt-1 h-6 w-6 rounded-full bg-brand-500/20 flex items-center justify-center shrink-0 border border-brand-500/20">
									<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-3.5 w-3.5 text-brand-400"><path d="M20 6 9 17l-5-5"></path></svg>
								</div>
								<div>
									<h4 class="text-base font-semibold text-white mb-1">Passive Awareness</h4>
									<p class="text-sm text-warm-400">A tiny icon in your system tray tells you the global health of your watched pipelines.</p>
								</div>
							</div>
							<div class="flex gap-4" use:reveal={{ delay: 350 }}>
								<div class="mt-1 h-6 w-6 rounded-full bg-brand-500/20 flex items-center justify-center shrink-0 border border-brand-500/20">
									<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-3.5 w-3.5 text-brand-400"><path d="M20 6 9 17l-5-5"></path></svg>
								</div>
								<div>
									<h4 class="text-base font-semibold text-white mb-1">Chrome Extension</h4>
									<p class="text-sm text-warm-400">Add watchers directly from your browser with the companion Chrome extension.</p>
								</div>
							</div>
						</div>
					</div>

					<div class="flex justify-center lg:justify-end" use:reveal={{ delay: 200 }}>
						<div class="relative rounded-xl overflow-hidden shadow-2xl border border-white/10 bg-warm-950 w-full max-w-sm">
							<!-- Window chrome -->
							<div class="h-10 bg-warm-900 border-b border-white/5 flex items-center px-4 gap-2">
								<div class="flex gap-1.5">
									<div class="h-2.5 w-2.5 rounded-full bg-[#FF5F56]"></div>
									<div class="h-2.5 w-2.5 rounded-full bg-[#FFBD2E]"></div>
									<div class="h-2.5 w-2.5 rounded-full bg-[#27C93F]"></div>
								</div>
								<img src="/cignaler_icon.png" alt="" class="h-3.5 w-3.5 rounded-sm ml-2" />
								<span class="text-xs text-warm-500 font-mono">Cignaler</span>
							</div>
							<div class="p-5 bg-warm-900">
								<div class="text-xs text-warm-500 font-mono uppercase tracking-wider mb-3">Watched Pipelines</div>
								<div class="space-y-3">
									<div class="flex items-center gap-3 bg-warm-800 p-3 rounded-lg border border-warm-700">
										<img src="/tray-success.svg" alt="" class="h-3 w-3" />
										<div class="flex-1 min-w-0">
											<span class="text-xs text-warm-200 font-mono block truncate">acme/frontend &middot; main</span>
											<span class="text-[10px] text-warm-500">passed &middot; 3m 42s</span>
										</div>
									</div>
									<div class="flex items-center gap-3 bg-warm-800 p-3 rounded-lg border border-red-500/30">
										<img src="/tray-failed.svg" alt="" class="h-3 w-3" />
										<div class="flex-1 min-w-0">
											<span class="text-xs text-warm-200 font-mono block truncate">acme/api &middot; main</span>
											<span class="text-[10px] text-warm-500">failed &middot; 1m 18s</span>
										</div>
									</div>
									<div class="flex items-center gap-3 bg-warm-800 p-3 rounded-lg border border-warm-700 opacity-60">
										<img src="/tray-pending.svg" alt="" class="h-3 w-3" />
										<div class="flex-1 min-w-0">
											<span class="text-xs text-warm-200 font-mono block truncate">acme/docs &middot; develop</span>
											<span class="text-[10px] text-warm-500">running &middot; 28s</span>
										</div>
									</div>
								</div>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- Features Section -->
<section id="features" class="py-24 bg-white">
	<div class="container mx-auto px-4 md:px-6">
		<div class="flex flex-col items-center text-center mb-20" use:reveal>
			<h2 class="font-display text-4xl md:text-5xl font-bold tracking-tight text-warm-900 mb-6">
				Built for <span class="text-transparent bg-clip-text bg-gradient-to-r from-warm-900 to-accent-600">flow state</span>.
			</h2>
			<p class="text-xl text-warm-500 max-w-2xl mx-auto leading-relaxed">
				Cignaler gets out of your way until you need it. A tool designed for developers who value screen real estate and mental bandwidth.
			</p>
		</div>

		<div class="grid grid-cols-1 md:grid-cols-6 gap-6 max-w-7xl mx-auto">
			<!-- Pipeline Watchers Card - Large, dark themed for dominance -->
			<div class="col-span-1 md:col-span-4 md:row-span-2 relative overflow-hidden rounded-3xl border border-warm-800 bg-warm-900 shadow-lg hover:shadow-xl transition-all group" use:reveal>
				<div class="p-8 h-full flex flex-col justify-between relative z-10">
					<div class="max-w-md">
						<div class="w-12 h-12 rounded-2xl bg-brand-500/20 flex items-center justify-center mb-6 text-brand-400">
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-6 w-6">
								<path d="m12.83 2.18a2 2 0 0 0-1.66 0L2.6 6.08a1 1 0 0 0 0 1.83l8.58 3.91a2 2 0 0 0 1.66 0l8.58-3.9a1 1 0 0 0 0-1.83Z"></path>
								<path d="m22 17.65-9.17 4.16a2 2 0 0 1-1.66 0L2 17.65"></path>
								<path d="m22 12.65-9.17 4.16a2 2 0 0 1-1.66 0L2 12.65"></path>
							</svg>
						</div>
						<h3 class="font-display text-2xl font-bold mb-3 text-white">Pipeline Watchers</h3>
						<p class="text-warm-400 text-lg">
							Create watchers through a simple form &mdash; pick your CI server, select a project, choose a branch. Done.
						</p>
					</div>
					<div class="mt-8 bg-warm-950 rounded-xl p-5 shadow-xl border border-warm-800 transform group-hover:translate-y-[-4px] transition-transform duration-500">
						<div class="flex items-center gap-2 border-b border-warm-800 pb-3 mb-4">
							<span class="text-xs text-warm-500 font-medium">Add Watcher</span>
						</div>
						<div class="space-y-3">
							<div class="flex items-center gap-3">
								<span class="text-xs text-warm-500 min-w-[56px]">Server</span>
								<div class="flex-1 flex items-center justify-between bg-warm-800 rounded-lg px-3 py-2 border border-warm-700">
									<span class="text-xs text-warm-200">GitLab Production</span>
									<svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-warm-500"><path d="m6 9 6 6 6-6"/></svg>
								</div>
							</div>
							<div class="flex items-center gap-3">
								<span class="text-xs text-warm-500 min-w-[56px]">Project</span>
								<div class="flex-1 flex items-center bg-warm-800 rounded-lg px-3 py-2 border border-warm-700">
									<span class="text-xs text-warm-200">acme/frontend</span>
								</div>
							</div>
							<div class="flex items-center gap-3">
								<span class="text-xs text-warm-500 min-w-[56px]">Branch</span>
								<div class="flex-1 flex items-center justify-between bg-warm-800 rounded-lg px-3 py-2 border border-warm-700">
									<span class="text-xs text-warm-200">main</span>
									<svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-warm-500"><path d="m6 9 6 6 6-6"/></svg>
								</div>
							</div>
						</div>
					</div>
				</div>
				<div class="absolute top-0 right-0 w-2/3 h-full bg-gradient-to-l from-brand-500/5 to-transparent pointer-events-none"></div>
			</div>

			<!-- Glanceable Status Card -->
			<div class="col-span-1 md:col-span-2 md:row-span-2 relative overflow-hidden rounded-3xl border border-warm-200 bg-white shadow-sm hover:shadow-md transition-all group" use:reveal={{ delay: 100 }}>
				<div class="p-8 h-full flex flex-col relative z-10">
					<div class="w-12 h-12 rounded-2xl bg-brand-50 flex items-center justify-center mb-6 text-brand-500">
						<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-6 w-6"><polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"></polygon></svg>
					</div>
					<h3 class="font-display text-2xl font-bold mb-3 text-warm-900">Glanceable Status</h3>
					<p class="text-warm-500 mb-8">
						Your CI health lives in your system tray. Green means go, red means stop.
					</p>
					<div class="flex-1 flex flex-col justify-end">
						<div class="bg-warm-950 rounded-t-xl p-4 shadow-xl border-x border-t border-warm-800 transform translate-y-4 group-hover:translate-y-2 transition-transform duration-500">
							<div class="flex items-center justify-between border-b border-warm-800 pb-3 mb-4">
								<span class="text-xs text-warm-500 font-mono">System Tray</span>
							</div>
							<div class="flex items-center gap-3 bg-warm-900 p-2 rounded-lg border border-warm-800 mb-2">
								<img src="/tray-success.svg" alt="" class="h-3 w-3" />
								<span class="text-xs text-warm-300 font-mono">acme/frontend main: passed</span>
							</div>
							<div class="flex items-center gap-3 bg-warm-900 p-2 rounded-lg border border-warm-800 mb-2 opacity-60">
								<img src="/tray-pending.svg" alt="" class="h-3 w-3" />
								<span class="text-xs text-warm-300 font-mono">acme/api develop: running</span>
							</div>
							<div class="flex items-center gap-3 bg-warm-900 p-2 rounded-lg border border-warm-800 opacity-40">
								<img src="/tray-failed.svg" alt="" class="h-3 w-3" />
								<span class="text-xs text-warm-300 font-mono">acme/docs main: failed</span>
							</div>
						</div>
					</div>
				</div>
			</div>

			<!-- Chrome Extension Card -->
			<div class="col-span-1 md:col-span-2 relative overflow-hidden rounded-3xl border border-warm-200 bg-white shadow-sm hover:shadow-md transition-all group" use:reveal={{ delay: 200 }}>
				<div class="p-8 h-full flex flex-col relative z-10">
					<div class="w-10 h-10 rounded-xl bg-accent-500/10 flex items-center justify-center mb-4 text-accent-600">
						<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-5 w-5"><circle cx="12" cy="12" r="10"></circle><circle cx="12" cy="12" r="4"></circle><line x1="21.17" x2="12" y1="8" y2="8"></line><line x1="3.95" x2="8.54" y1="6.06" y2="14"></line><line x1="10.88" x2="15.46" y1="21.94" y2="14"></line></svg>
					</div>
					<h3 class="font-display text-xl font-bold mb-2 text-warm-900">Chrome Extension</h3>
					<p class="text-warm-500 text-sm mb-6">
						Add watchers straight from your browser with the companion Chrome extension.
					</p>
					<div class="p-3 rounded-xl bg-warm-50 border border-warm-200">
						<div class="flex items-center justify-between mb-2">
							<span class="text-xs text-warm-500 font-medium">Add to Cignaler</span>
						</div>
						<div class="flex items-center gap-2 px-3 py-2 rounded-lg bg-white border border-warm-200">
							<svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-warm-400"><path d="m22 13.29-3.33-10a.42.42 0 0 0-.14-.18.38.38 0 0 0-.22-.11.39.39 0 0 0-.23.07.42.42 0 0 0-.14.18l-2.26 6.67H8.32L6.1 3.26a.42.42 0 0 0-.1-.18.38.38 0 0 0-.26-.08.39.39 0 0 0-.23.07.42.42 0 0 0-.14.18L2 13.29a.74.74 0 0 0 .27.83L12 21l9.69-6.88a.71.71 0 0 0 .31-.83Z"/></svg>
							<span class="text-xs text-warm-700 font-mono">acme/frontend &middot; main</span>
						</div>
						<button class="mt-2 w-full text-center text-xs font-semibold text-white bg-brand-500 rounded-lg py-1.5">Watch this project</button>
					</div>
				</div>
			</div>

			<!-- Native & Lightweight Card -->
			<div class="col-span-1 md:col-span-2 relative overflow-hidden rounded-3xl border border-warm-200 bg-white shadow-sm hover:shadow-md transition-all group" use:reveal={{ delay: 250 }}>
				<div class="p-8 h-full flex flex-col relative z-10">
					<div class="w-10 h-10 rounded-xl bg-green-500/10 flex items-center justify-center mb-4 text-green-600">
						<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-5 w-5"><path d="M13 2 3 14h9l-1 8 10-12h-9l1-8z"/></svg>
					</div>
					<h3 class="font-display text-xl font-bold mb-2 text-warm-900">Native & Lightweight</h3>
					<p class="text-warm-500 text-sm mb-6">
						Built with Tauri 2 and Rust. Native performance, minimal resource usage.
					</p>
					<div class="flex items-center justify-between p-3 rounded-xl bg-warm-50 border border-warm-200">
						<span class="text-xs text-warm-400 font-mono">Framework</span>
						<span class="text-sm font-bold text-green-600 font-mono">Tauri 2 + Rust</span>
					</div>
				</div>
			</div>

			<!-- Always Monitoring Card -->
			<div class="col-span-1 md:col-span-2 relative overflow-hidden rounded-3xl border border-warm-200 bg-white shadow-sm hover:shadow-md transition-all group" use:reveal={{ delay: 300 }}>
				<div class="p-8 h-full flex flex-col relative z-10">
					<div class="w-10 h-10 rounded-xl bg-purple-500/10 flex items-center justify-center mb-4 text-purple-600">
						<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-5 w-5"><path d="M21 12a9 9 0 1 1-6.219-8.56"/><path d="M12 7v5l3 3"/></svg>
					</div>
					<h3 class="font-display text-xl font-bold mb-2 text-warm-900">Always Monitoring</h3>
					<p class="text-warm-500 text-sm mb-6">
						Polls your pipelines every 60 seconds. Results cached locally so your data is always ready.
					</p>
					<div class="p-3 rounded-xl bg-warm-50 border border-warm-200 space-y-2">
						<div class="flex items-center justify-between">
							<span class="text-xs text-warm-400 font-mono">Polling every</span>
							<span class="text-sm font-bold text-purple-600 font-mono">60s</span>
						</div>
						<div class="flex items-center justify-between">
							<span class="text-xs text-warm-400 font-mono">Last synced</span>
							<span class="text-xs text-warm-500 font-mono">12s ago</span>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- Workflow / Steps Section (Timeline style instead of cards) -->
<section class="py-20 bg-warm-50/50">
	<div class="container mx-auto px-4 md:px-6">
		<div class="flex flex-col items-center text-center mb-16" use:reveal>
			<h2 class="font-display text-4xl md:text-5xl font-bold tracking-tight text-warm-900 mb-6">
				Set up in <span class="text-transparent bg-clip-text bg-gradient-to-r from-brand-500 to-accent-500">under 60 seconds</span>.
			</h2>
			<p class="text-xl text-warm-500 max-w-2xl mx-auto leading-relaxed">
				Three simple steps to regain your focus and stop context switching.
			</p>
		</div>

		<div class="max-w-4xl mx-auto">
			<!-- Timeline layout -->
			<div class="relative">
				<!-- Vertical connector line (hidden on mobile) -->
				<div class="hidden md:block absolute top-12 left-1/2 -translate-x-1/2 w-0.5 h-[calc(100%-96px)] bg-gradient-to-b from-brand-500 via-accent-500 to-purple-500 opacity-20"></div>

				<div class="space-y-12 md:space-y-16">
					<!-- Step 1 -->
					<div class="flex flex-col md:flex-row md:items-start gap-6 md:gap-12" use:reveal>
						<div class="flex-1 md:text-right order-2 md:order-1">
							<h3 class="font-display text-xl font-bold mb-2 text-warm-900">Download the App</h3>
							<p class="text-warm-500 mb-4">
								Download Cignaler for macOS. A lightweight desktop app that lives in your system tray. Windows & Linux coming soon.
							</p>
							<div class="inline-flex items-center gap-2 bg-brand-500 rounded-xl px-5 py-3 shadow-lg text-sm text-white font-semibold">
								<Download class="h-4 w-4" />
								Download for macOS
							</div>
						</div>
						<div class="flex items-center justify-center order-1 md:order-2 shrink-0">
							<div class="w-14 h-14 rounded-2xl bg-brand-500 text-white flex items-center justify-center text-xl font-display font-bold shadow-lg shadow-brand-500/20">1</div>
						</div>
						<div class="flex-1 order-3 hidden md:block"></div>
					</div>

					<!-- Step 2 -->
					<div class="flex flex-col md:flex-row md:items-start gap-6 md:gap-12" use:reveal={{ delay: 100 }}>
						<div class="flex-1 order-2 md:order-1 hidden md:block"></div>
						<div class="flex items-center justify-center order-1 md:order-2 shrink-0">
							<div class="w-14 h-14 rounded-2xl bg-accent-500 text-white flex items-center justify-center text-xl font-display font-bold shadow-lg shadow-accent-500/20">2</div>
						</div>
						<div class="flex-1 order-3 md:order-3">
							<h3 class="font-display text-xl font-bold mb-2 text-warm-900">Add Your CI Server</h3>
							<p class="text-warm-500 mb-4">
								Open Preferences, add your GitLab server URL and API token. Then create a watcher for any project and branch.
							</p>
							<div class="inline-block bg-warm-900 rounded-xl px-5 py-3 shadow-lg text-sm text-left space-y-1.5">
								<div class="flex items-center gap-2">
									<span class="text-warm-500 text-xs min-w-[48px]">Server</span>
									<span class="text-warm-200 text-xs font-mono">gitlab.company.com</span>
								</div>
								<div class="flex items-center gap-2">
									<span class="text-warm-500 text-xs min-w-[48px]">Project</span>
									<span class="text-warm-200 text-xs font-mono">acme/frontend</span>
								</div>
							</div>
						</div>
					</div>

					<!-- Step 3 -->
					<div class="flex flex-col md:flex-row md:items-start gap-6 md:gap-12" use:reveal={{ delay: 200 }}>
						<div class="flex-1 md:text-right order-2 md:order-1">
							<h3 class="font-display text-xl font-bold mb-2 text-warm-900">Stay Focused</h3>
							<p class="text-warm-500 mb-4">
								Cignaler polls in the background and updates your tray icon. Green means all clear, red means something needs attention.
							</p>
							<div class="inline-flex items-center gap-3 bg-warm-900 rounded-xl px-5 py-3 shadow-lg">
								<img src="/tray-success.svg" alt="" class="h-3.5 w-3.5" />
								<span class="text-sm text-warm-300 font-mono">All systems green</span>
							</div>
						</div>
						<div class="flex items-center justify-center order-1 md:order-2 shrink-0">
							<div class="w-14 h-14 rounded-2xl bg-purple-600 text-white flex items-center justify-center text-xl font-display font-bold shadow-lg shadow-purple-600/20">3</div>
						</div>
						<div class="flex-1 order-3 hidden md:block"></div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- Testimonial / Quote Section -->
<section class="py-16 bg-white">
	<div class="container mx-auto px-4 md:px-6">
		<div class="max-w-3xl mx-auto text-center" use:reveal>
			<blockquote class="font-display text-2xl md:text-3xl font-semibold text-warm-900 leading-relaxed mb-8">
				"Your CI pipelines, watched. Your focus, protected. Cignaler sits quietly in your system tray and only speaks up when something breaks."
			</blockquote>
		</div>
	</div>
</section>

<!-- Bottom CTA Section -->
<section class="py-24 bg-warm-50/50">
	<div class="container mx-auto px-4 md:px-6">
		<div class="relative rounded-[2rem] bg-gradient-to-br from-warm-900 via-warm-800 to-warm-900 overflow-hidden shadow-2xl">
			<div class="absolute inset-0 bg-[radial-gradient(circle_at_30%_50%,rgba(232,98,44,0.1),transparent_50%)]"></div>
			<div class="absolute inset-0 bg-[radial-gradient(circle_at_70%_50%,rgba(20,184,166,0.1),transparent_50%)]"></div>

			<div class="relative z-10 py-20 md:py-24 px-8 md:px-16">
				<div class="max-w-4xl mx-auto text-center">
					<h2 class="font-display text-4xl md:text-6xl lg:text-7xl font-bold tracking-tight text-white mb-8 leading-[1.1]" use:reveal>
						Stop watching.
						<br />
						<span class="text-transparent bg-clip-text bg-gradient-to-r from-brand-400 to-accent-400">
							Start building.
						</span>
					</h2>

					<p class="text-xl md:text-2xl text-warm-400 max-w-2xl mx-auto mb-12 leading-relaxed" use:reveal={{ delay: 100 }}>
						Reclaim your focus. Stop staring at CI dashboards and let Cignaler watch your pipelines for you.
					</p>

					<div class="flex flex-col sm:flex-row items-center justify-center gap-4 mb-8" use:reveal={{ delay: 200 }}>
						<a href="https://github.com/cignaler/cignaler/releases/latest/download/Cignaler.dmg" class="inline-flex items-center justify-center h-14 px-8 text-lg rounded-full bg-brand-500 text-white font-display font-semibold shadow-xl shadow-brand-500/20 hover:shadow-brand-500/30 hover:bg-brand-600 transition-all hover:scale-[1.03]">
							<Download class="mr-2 h-5 w-5" />
							Download Cignaler
						</a>
						<a href="https://github.com/cignaler/cignaler" target="_blank" rel="noopener noreferrer" class="inline-flex items-center justify-center h-14 px-8 text-lg rounded-full border-2 border-white/20 bg-white/10 backdrop-blur-sm text-white font-display font-semibold hover:bg-white/20 transition-all">
							<Github class="mr-2 h-5 w-5" />
							View on GitHub
						</a>
					</div>

					<!-- Stats -->
					<div class="grid grid-cols-3 gap-8 max-w-2xl mx-auto pt-12 mt-12 border-t border-white/10" use:reveal={{ delay: 400 }}>
						<div>
							<div class="font-display text-3xl md:text-4xl font-bold text-white mb-2">60s</div>
							<div class="text-sm text-warm-400">Polling Interval</div>
						</div>
						<div>
							<div class="font-display text-3xl md:text-4xl font-bold text-white mb-2">Tauri 2</div>
							<div class="text-sm text-warm-400">Native Framework</div>
						</div>
						<div>
							<div class="font-display text-3xl md:text-4xl font-bold text-white mb-2">SQLite</div>
							<div class="text-sm text-warm-400">Local Cache</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>


<!-- FAQ Section (GEO: structured answers for AI search engines) -->
<section id="faq" class="py-20 bg-white">
	<div class="container mx-auto px-4 md:px-6">
		<div class="max-w-3xl mx-auto">
			<h2 class="font-display text-4xl md:text-5xl font-bold tracking-tight text-warm-900 mb-12 text-center" use:reveal>
				Frequently Asked Questions
			</h2>
			<div class="divide-y divide-warm-200" use:reveal={{ delay: 100 }}>
				<div class="py-6">
					<h3 class="font-display text-lg font-bold text-warm-900 mb-2">What is Cignaler?</h3>
					<p class="text-warm-500 leading-relaxed">Cignaler is a free, open-source desktop application that monitors GitLab CI/CD pipelines from your system tray. Built with Tauri 2 and Rust, it polls your pipelines every 60 seconds and sends native notifications when builds fail — so you never have to keep a CI dashboard tab open.</p>
				</div>
				<div class="py-6">
					<h3 class="font-display text-lg font-bold text-warm-900 mb-2">What CI platforms does Cignaler support?</h3>
					<p class="text-warm-500 leading-relaxed">Cignaler currently supports GitLab CI/CD. Support for GitHub Actions and Jenkins is planned.</p>
				</div>
				<div class="py-6">
					<h3 class="font-display text-lg font-bold text-warm-900 mb-2">Is Cignaler free?</h3>
					<p class="text-warm-500 leading-relaxed">Yes, Cignaler is completely free and open source. You can view the source code and contribute on <a href="https://github.com/cignaler/cignaler" target="_blank" rel="noopener noreferrer" class="text-brand-600 hover:text-brand-700 underline">GitHub</a>.</p>
				</div>
				<div class="py-6">
					<h3 class="font-display text-lg font-bold text-warm-900 mb-2">What platforms does Cignaler run on?</h3>
					<p class="text-warm-500 leading-relaxed">Cignaler is currently available for macOS. Windows and Linux support is coming soon.</p>
				</div>
				<div class="py-6">
					<h3 class="font-display text-lg font-bold text-warm-900 mb-2">How does Cignaler work?</h3>
					<p class="text-warm-500 leading-relaxed">Cignaler runs as a system tray application. You create watchers for specific GitLab projects and branches. It polls your pipelines every 60 seconds and sends native desktop notifications when a build fails. Results are cached locally in SQLite so your data is always ready.</p>
				</div>
				<div class="py-6">
					<h3 class="font-display text-lg font-bold text-warm-900 mb-2">Does Cignaler collect any data?</h3>
					<p class="text-warm-500 leading-relaxed">No. Cignaler is fully local — all data stays on your machine. There is no telemetry, analytics, or external data collection of any kind. Read our <a href="/privacy" class="text-brand-600 hover:text-brand-700 underline">privacy policy</a> for details.</p>
				</div>
			</div>
		</div>
	</div>
</section>

</main>

<!-- Footer -->
<footer class="bg-warm-50 border-t border-warm-200">
	<div class="container mx-auto px-4 md:px-6 py-12">
		<div class="flex flex-col md:flex-row justify-between items-start gap-8 mb-8">
			<!-- Brand -->
			<div class="max-w-xs">
				<div class="flex items-center gap-2 mb-4">
					<img src="/cignaler_icon.png" alt="Cignaler" class="h-8 w-8 rounded-lg" />
					<span class="font-display text-xl font-bold tracking-tight text-warm-900">Cignaler</span>
				</div>
				<p class="text-sm text-warm-500 leading-relaxed">
					Stop staring at broken pipelines. Get notified only when it matters.
				</p>
			</div>

			<!-- Links -->
			<div class="flex flex-wrap gap-x-12 gap-y-6">
				<div>
					<h3 class="font-display font-semibold text-warm-900 mb-3 text-sm">Product</h3>
					<ul class="space-y-2 text-sm">
						<li><a href="#features" class="text-warm-500 hover:text-warm-900 transition-colors">Features</a></li>
						<li><a href="#how-it-works" class="text-warm-500 hover:text-warm-900 transition-colors">How it works</a></li>
						<li><a href="#faq" class="text-warm-500 hover:text-warm-900 transition-colors">FAQ</a></li>
					</ul>
				</div>
				<div>
					<h3 class="font-display font-semibold text-warm-900 mb-3 text-sm">Resources</h3>
					<ul class="space-y-2 text-sm">
						<li><a href="https://github.com/cignaler/cignaler" target="_blank" rel="noopener noreferrer" class="text-warm-500 hover:text-warm-900 transition-colors">GitHub</a></li>
						<li><a href="https://github.com/cignaler/cignaler#readme" target="_blank" rel="noopener noreferrer" class="text-warm-500 hover:text-warm-900 transition-colors">Documentation</a></li>
					</ul>
				</div>
			</div>
		</div>

		<!-- Bottom Bar -->
		<div class="pt-8 border-t border-warm-200 flex flex-col md:flex-row justify-between items-center gap-4">
			<p class="text-sm text-warm-400">
				&copy; 2026 Cignaler. All rights reserved.
			</p>
			<div class="flex items-center gap-6 text-sm text-warm-400">
				<a href="/privacy" class="hover:text-warm-900 transition-colors">Privacy Policy</a>
				<a href="https://github.com/cignaler/cignaler" target="_blank" rel="noopener noreferrer" class="hover:text-warm-900 transition-colors flex items-center gap-1.5">
					<Github class="h-4 w-4" />
					GitHub
				</a>
			</div>
		</div>
	</div>
</footer>
