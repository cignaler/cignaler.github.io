<script lang="ts">
	import { Github, Activity, Terminal } from 'lucide-svelte';
</script>

<!-- Navigation Header -->
<header class="sticky top-0 z-50 w-full border-b border-gray-200/40 bg-white/80 backdrop-blur-md">
	<div class="container mx-auto px-4 md:px-6">
		<div class="flex h-16 items-center justify-between">
			<!-- Logo -->
			<div class="flex items-center gap-2">
				<div class="flex h-8 w-8 items-center justify-center rounded-lg bg-gray-900/10 text-gray-900">
					<Activity class="h-5 w-5" />
				</div>
				<span class="text-xl font-bold tracking-tight text-gray-900">Cignaler</span>
			</div>

			<!-- Navigation Links -->
			<nav class="hidden md:flex items-center gap-8 text-sm font-medium text-gray-600">
				<a href="#features" class="transition-colors hover:text-gray-900">Features</a>
				<a href="#how-it-works" class="transition-colors hover:text-gray-900">How it works</a>
				<a href="https://github.com/" target="_blank" rel="noopener noreferrer" class="transition-colors hover:text-gray-900">GitHub</a>
			</nav>

			<!-- CTA Button -->
			<div class="flex items-center gap-4">
				<button class="items-center justify-center whitespace-nowrap rounded-md font-medium transition-colors h-8 px-3 text-xs hidden sm:flex bg-gray-900 text-white hover:bg-gray-800 shadow-sm">
					Download App
				</button>
			</div>
		</div>
	</div>
</header>

<!-- Hero Section -->
<section class="relative overflow-hidden bg-white pt-32 pb-40 selection:bg-orange-500/20">
	<!-- Animated Background Pattern -->
	<div
		class="absolute inset-0 -z-10 h-full w-full bg-white bg-[radial-gradient(#e5e7eb_1px,transparent_1px)] [background-size:16px_16px] [mask-image:radial-gradient(ellipse_50%_50%_at_50%_50%,#000_70%,transparent_100%)]"
	></div>

	<!-- Animated Glow Blobs -->
	<div
		class="absolute top-0 left-1/2 -translate-x-1/2 w-[800px] h-[500px] bg-orange-500/5 rounded-full blur-[120px] -z-10"
		style="animation: var(--animate-pulse-slow)"
	></div>
	<div
		class="absolute bottom-0 right-0 w-[600px] h-[600px] bg-blue-500/5 rounded-full blur-[100px] -z-10"
	></div>

	<div class="container mx-auto px-4 md:px-6 relative z-10">
		<!-- Hero Content -->
		<div class="flex flex-col items-center text-center max-w-5xl mx-auto mb-20">
			<!-- Badge -->
			<div class="mb-8">
				<div
					class="inline-flex items-center gap-2 rounded-full border border-gray-200 bg-white/50 backdrop-blur-sm px-4 py-1.5 text-sm font-medium text-gray-900 shadow-sm hover:bg-white/80 transition-colors cursor-default"
				>
					<span class="relative flex h-2 w-2">
						<span
							class="animate-ping absolute inline-flex h-full w-full rounded-full bg-green-400 opacity-75"
						></span>
						<span class="relative inline-flex rounded-full h-2 w-2 bg-green-500"></span>
					</span>
					<span class="text-gray-600">v2.0 is live:</span>
					<span class="font-semibold bg-clip-text text-transparent bg-gradient-to-r from-orange-500 to-blue-600"
						>Intelligent Watchers</span
					>
				</div>
			</div>

			<!-- Main Heading -->
			<h1
				class="text-5xl md:text-7xl lg:text-8xl font-bold tracking-tight text-gray-900 mb-8 leading-[1.1]"
			>
				Stop staring at
				<br />
				<span
					class="relative inline-block text-transparent bg-clip-text bg-gradient-to-r from-gray-900 via-gray-700 to-gray-900 bg-[length:200%_auto] pb-2"
					style="animation: var(--animate-gradient-x)"
				>
					broken pipelines.
					<svg
						class="absolute w-full h-4 -bottom-1 left-0 text-orange-500 opacity-50"
						viewBox="0 0 100 10"
						preserveAspectRatio="none"
					>
						<path d="M0 5 Q 50 10 100 5" stroke="currentColor" stroke-width="4" fill="none" />
					</svg>
				</span>
			</h1>

			<!-- Subheading -->
			<p
				class="text-xl md:text-2xl text-gray-600 max-w-2xl mx-auto mb-10 leading-relaxed"
			>
				Cignaler filters the noise. Get notified only when the builds
				<span class="text-gray-900 font-semibold">you care about</span> actually break.
			</p>

			<!-- CTAs -->
			<div
				class="flex flex-col sm:flex-row items-center gap-4"
			>
				<button
					class="h-14 px-8 text-lg rounded-full bg-orange-500 text-white font-medium shadow-xl shadow-orange-500/20 hover:shadow-orange-500/30 transition-all hover:scale-105"
				>
					Get Started
				</button>
				<button
					class="h-14 px-8 text-lg rounded-full border-2 border-gray-300 bg-white text-gray-900 font-medium hover:bg-gray-50 transition-all flex items-center gap-2"
				>
					<Github class="h-5 w-5" />
					Star on GitHub
				</button>
			</div>

			<!-- Trust Indicators -->
			<div
				class="mt-6 flex items-center gap-6 text-sm text-gray-500"
			>
				<div class="flex items-center gap-2">
					<svg class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
					</svg>
					No credit card required
				</div>
				<div class="flex items-center gap-2">
					<svg class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
					</svg>
					14-day trial
				</div>
				<div class="flex items-center gap-2">
					<svg class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
					</svg>
					Cancel anytime
				</div>
			</div>
		</div>

		<!-- Product Screenshot with Animations -->
		<div class="relative max-w-6xl mx-auto">
			<div class="relative group">
				<!-- Glow Effect Behind Screenshot -->
				<div
					class="absolute inset-0 bg-gradient-to-tr from-orange-500/30 to-purple-500/30 blur-[80px] rounded-[3rem] opacity-40 group-hover:opacity-60 transition-opacity duration-700"
				></div>

				<!-- Main Screenshot Container -->
				<div
					class="relative bg-gray-950 rounded-2xl border border-gray-800/50 shadow-2xl overflow-hidden ring-1 ring-white/10"
				>
					<!-- Browser Chrome -->
					<div
						class="h-12 bg-gray-900/50 backdrop-blur-md border-b border-white/5 flex items-center px-6 justify-between"
					>
						<div class="flex gap-2">
							<div class="h-3 w-3 rounded-full bg-[#FF5F56] border border-[#E0443E]"></div>
							<div class="h-3 w-3 rounded-full bg-[#FFBD2E] border border-[#DEA123]"></div>
							<div class="h-3 w-3 rounded-full bg-[#27C93F] border border-[#1AAB29]"></div>
						</div>
						<div class="text-xs font-mono text-gray-500 flex items-center gap-2">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								width="24"
								height="24"
								viewBox="0 0 24 24"
								fill="none"
								stroke="currentColor"
								stroke-width="2"
								stroke-linecap="round"
								stroke-linejoin="round"
								class="h-3 w-3"
							>
								<polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"></polygon>
							</svg>
							cignaler-pro
						</div>
						<div class="w-16"></div>
					</div>

					<!-- Dashboard Content -->
					<div class="relative aspect-[16/10] bg-gray-900 w-full overflow-hidden">
						<div class="p-6">
							<div class="mb-4 flex items-center justify-between">
								<div class="flex items-center gap-3">
									<div class="rounded-lg bg-orange-500 px-3 py-1.5 text-sm font-medium text-white">
										All Pipelines
									</div>
									<div class="rounded-lg bg-white px-3 py-1.5 text-sm text-gray-600">Failed (3)</div>
								</div>
								<button class="rounded-lg bg-gray-900 px-4 py-2 text-sm text-white border border-gray-700">
									View all workflows
								</button>
							</div>

							<div class="space-y-3">
								<!-- Pipeline item 1 -->
								<div class="flex items-center gap-4 rounded-lg bg-white p-4 shadow-sm">
									<div class="flex h-2 w-2 rounded-full bg-red-500"></div>
									<div class="flex-1">
										<div class="mb-1 font-medium text-gray-900">Backend API</div>
										<div class="text-sm text-gray-500">main branch • 2 minutes ago</div>
									</div>
									<div class="text-sm text-gray-500">Deploy failed</div>
								</div>

								<!-- Pipeline item 2 -->
								<div class="flex items-center gap-4 rounded-lg bg-white p-4 shadow-sm">
									<div class="flex h-2 w-2 rounded-full bg-green-500"></div>
									<div class="flex-1">
										<div class="mb-1 font-medium text-gray-900">Frontend Build</div>
										<div class="text-sm text-gray-500">develop branch • 5 minutes ago</div>
									</div>
									<div class="text-sm text-gray-500">Success</div>
								</div>

								<!-- Pipeline item 3 -->
								<div class="flex items-center gap-4 rounded-lg bg-white p-4 shadow-sm">
									<div class="flex h-2 w-2 rounded-full bg-red-500"></div>
									<div class="flex-1">
										<div class="mb-1 font-medium text-gray-900">Tests</div>
										<div class="text-sm text-gray-500">feature/auth • 12 minutes ago</div>
									</div>
									<div class="text-sm text-gray-500">Tests failed</div>
								</div>
							</div>
						</div>

						<!-- Gradient Overlay -->
						<div
							class="absolute inset-0 bg-gradient-to-t from-gray-950/50 to-transparent pointer-events-none"
						></div>
					</div>
				</div>

				<!-- Floating Cards -->
				<!-- Success Card (Left) -->
				<div
					class="absolute -left-12 top-1/3 p-4 bg-white rounded-xl shadow-[0_8px_30px_rgb(0,0,0,0.12)] border border-gray-200 hidden lg:block"
					style="animation: var(--animate-float)"
				>
					<div class="flex items-center gap-3">
						<div class="h-10 w-10 bg-green-100 rounded-lg flex items-center justify-center">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								width="24"
								height="24"
								viewBox="0 0 24 24"
								fill="none"
								stroke="currentColor"
								stroke-width="2"
								stroke-linecap="round"
								stroke-linejoin="round"
								class="h-5 w-5 text-green-600"
							>
								<polyline points="4 17 10 11 4 5"></polyline>
								<line x1="12" x2="20" y1="19" y2="19"></line>
							</svg>
						</div>
						<div>
							<div class="text-xs text-gray-600 font-medium">Build Passed</div>
							<div class="text-sm font-bold text-gray-900">frontend/main</div>
						</div>
					</div>
				</div>

				<!-- Alert Card (Right) -->
				<div
					class="absolute -right-8 bottom-1/4 p-4 bg-gray-900 text-white rounded-xl shadow-[0_8px_30px_rgb(0,0,0,0.2)] border border-gray-700 hidden lg:block"
					style="animation: var(--animate-float-delayed)"
				>
					<div class="flex items-center gap-3">
						<div class="h-2 w-2 rounded-full bg-red-500 animate-pulse"></div>
						<div class="text-sm font-medium">
							1 failure ignored <span class="text-gray-400 text-xs ml-1">(noise)</span>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- Problems Section -->
<section class="py-24 bg-gray-50/50 relative overflow-hidden">
	<div class="absolute top-0 left-0 w-full h-full overflow-hidden pointer-events-none">
		<div class="absolute top-[10%] left-[-5%] w-[30%] h-[30%] bg-red-500/5 rounded-full blur-3xl"></div>
		<div class="absolute bottom-[10%] right-[-5%] w-[30%] h-[30%] bg-blue-500/5 rounded-full blur-3xl"></div>
	</div>

	<div class="container mx-auto px-4 md:px-6 relative z-10">
		<div class="mx-auto max-w-3xl text-center mb-16">
			<h2 class="text-4xl md:text-5xl font-bold tracking-tight text-gray-900 mb-6">
				CI dashboards are <span class="text-red-600 relative inline-block">noisy
					<svg class="absolute w-full h-3 -bottom-1 left-0 text-red-600/20" viewBox="0 0 100 10" preserveAspectRatio="none">
						<path d="M0 5 Q 50 10 100 5" stroke="currentColor" stroke-width="3" fill="none" />
					</svg>
				</span>.
			</h2>
			<p class="text-xl text-gray-600 leading-relaxed">
				Most developer tools show you the world, when all you wanted was your own backyard. Stop scrolling through hundreds of pipelines you don't own.
			</p>
		</div>

		<div class="grid md:grid-cols-3 gap-6 max-w-6xl mx-auto">
			<!-- Alert Fatigue Card -->
			<div class="group relative overflow-hidden rounded-3xl bg-white border border-gray-200 p-6 shadow-sm hover:shadow-md transition-all">
				<div class="mb-6 h-40 bg-gray-50 rounded-xl border border-gray-200/50 overflow-hidden relative flex flex-col p-3 gap-2">
					<div class="absolute inset-0 bg-gradient-to-b from-transparent via-transparent to-white/80 z-10"></div>
					<div class="h-8 w-full rounded border flex items-center px-2 gap-2 bg-white border-gray-200/60 opacity-100">
						<div class="h-2 w-2 rounded-full bg-gray-200"></div>
						<div class="h-2 w-2/3 bg-gray-100 rounded"></div>
					</div>
					<div class="h-8 w-full rounded border flex items-center px-2 gap-2 bg-white border-gray-200/60 opacity-85">
						<div class="h-2 w-2 rounded-full bg-gray-200"></div>
						<div class="h-2 w-2/3 bg-gray-100 rounded"></div>
					</div>
					<div class="h-8 w-full rounded border flex items-center px-2 gap-2 bg-red-50 border-red-100 opacity-70">
						<div class="h-2 w-2 rounded-full bg-red-500"></div>
						<div class="h-2 w-2/3 bg-gray-100 rounded"></div>
					</div>
					<div class="absolute bottom-3 left-1/2 -translate-x-1/2 z-20 bg-white/90 backdrop-blur border border-gray-200 px-3 py-1 rounded-full text-[10px] font-medium text-gray-600 shadow-sm">
						+142 hidden
					</div>
				</div>
				<h3 class="text-xl font-bold mb-2">Alert Fatigue</h3>
				<p class="text-gray-600 text-sm">
					When 50 builds are failing, you stop checking. Relevant signals get lost in the noise of global failures.
				</p>
			</div>

			<!-- Silent Failures Card -->
			<div class="group relative overflow-hidden rounded-3xl bg-white border border-gray-200 p-6 shadow-sm hover:shadow-md transition-all">
				<div class="mb-6 h-40 bg-gray-50 rounded-xl border border-gray-200/50 overflow-hidden relative flex items-center justify-center">
					<div class="relative z-10 bg-white p-4 rounded-xl shadow-lg border border-gray-200 flex items-center gap-3">
						<div class="h-8 w-8 rounded-full bg-red-100 flex items-center justify-center">
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-5 w-5 text-red-600">
								<circle cx="12" cy="12" r="10"></circle>
								<path d="m15 9-6 6"></path>
								<path d="m9 9 6 6"></path>
							</svg>
						</div>
						<div class="text-xs">
							<div class="font-bold text-gray-900">Build Failed</div>
							<div class="text-gray-600">2 hours ago</div>
						</div>
					</div>
				</div>
				<h3 class="text-xl font-bold mb-2">Silent Failures</h3>
				<p class="text-gray-600 text-sm">
					Critical failures on your branch can sit unnoticed for hours while you assume everything is fine.
				</p>
			</div>

			<!-- Context Switching Card -->
			<div class="group relative overflow-hidden rounded-3xl bg-white border border-gray-200 p-6 shadow-sm hover:shadow-md transition-all">
				<div class="mb-6 h-40 bg-gray-50 rounded-xl border border-gray-200/50 overflow-hidden relative">
					<div class="mt-4 ml-4 bg-white rounded-tl-lg shadow-xl border-l border-t border-gray-200 h-full relative">
						<div class="flex items-center gap-1 p-2 border-b border-gray-200 bg-gray-50 rounded-tl-lg">
							<div class="h-2 w-2 rounded-full bg-red-400"></div>
							<div class="h-2 w-2 rounded-full bg-yellow-400"></div>
							<div class="h-2 w-2 rounded-full bg-green-400"></div>
						</div>
						<div class="p-3">
							<div class="h-2 w-1/3 bg-gray-100 rounded mb-2"></div>
							<div class="h-2 w-1/2 bg-gray-100 rounded"></div>
						</div>
						<div class="absolute -top-3 -right-4 bg-gray-800 text-white p-2 rounded-lg shadow-lg text-[10px] font-mono">
							Checking...
						</div>
					</div>
				</div>
				<h3 class="text-xl font-bold mb-2">Context Switching</h3>
				<p class="text-gray-600 text-sm">
					Constantly tabbing back to GitHub/GitLab breaks your flow. It takes 15 minutes to recover focus.
				</p>
			</div>
		</div>
	</div>
</section>

<!-- Solution Section -->
<section id="how-it-works" class="py-24 bg-gray-50/50">
	<div class="container mx-auto px-4 md:px-6">
		<div class="relative rounded-[2.5rem] bg-gray-900 border border-gray-800 overflow-hidden shadow-2xl">
			<div class="absolute top-0 right-0 w-[500px] h-[500px] bg-orange-500/10 rounded-full blur-[100px] pointer-events-none"></div>
			<div class="absolute bottom-0 left-0 w-[500px] h-[500px] bg-blue-500/10 rounded-full blur-[100px] pointer-events-none"></div>

			<div class="relative z-10 p-8 md:p-16">
		<div class="grid lg:grid-cols-2 gap-12 items-center">
			<div class="text-left">
				<div class="inline-flex items-center gap-2 rounded-full bg-white/10 border border-white/10 px-4 py-1.5 text-sm font-medium text-white mb-8 backdrop-blur-md">
					<span class="relative flex h-2 w-2">
						<span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-green-400 opacity-75"></span>
						<span class="relative inline-flex rounded-full h-2 w-2 bg-green-500"></span>
					</span>
					The Solution
				</div>
				<h2 class="text-3xl md:text-5xl font-bold tracking-tight text-white mb-6 leading-tight">
					Focus on <span class="text-transparent bg-clip-text bg-gradient-to-r from-orange-500 to-blue-400">your work</span>, not the dashboard.
				</h2>
				<p class="text-lg text-gray-400 mb-10 leading-relaxed">
					Cignaler filters out the noise. Configure regex watchers to only track the branches and PRs you care about. When something breaks, you'll know. Otherwise, silence is golden.
				</p>

				<div class="space-y-6">
					<div class="flex gap-4">
						<div class="mt-1 h-6 w-6 rounded-full bg-orange-500/20 flex items-center justify-center shrink-0 border border-orange-500/20">
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-3.5 w-3.5 text-orange-500">
								<path d="M20 6 9 17l-5-5"></path>
							</svg>
						</div>
						<div>
							<h4 class="text-base font-semibold text-white mb-1">Curated Watchers</h4>
							<p class="text-sm text-gray-400">Add only the specific pipelines, branches, or PRs you are personally responsible for.</p>
						</div>
					</div>
					<div class="flex gap-4">
						<div class="mt-1 h-6 w-6 rounded-full bg-orange-500/20 flex items-center justify-center shrink-0 border border-orange-500/20">
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-3.5 w-3.5 text-orange-500">
								<path d="M20 6 9 17l-5-5"></path>
							</svg>
						</div>
						<div>
							<h4 class="text-base font-semibold text-white mb-1">Passive Awareness</h4>
							<p class="text-sm text-gray-400">A tiny icon in your system tray tells you the global health of your watched pipelines.</p>
						</div>
					</div>
					<div class="flex gap-4">
						<div class="mt-1 h-6 w-6 rounded-full bg-orange-500/20 flex items-center justify-center shrink-0 border border-orange-500/20">
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-3.5 w-3.5 text-orange-500">
								<path d="M20 6 9 17l-5-5"></path>
							</svg>
						</div>
						<div>
							<h4 class="text-base font-semibold text-white mb-1">Multi-Provider</h4>
							<p class="text-sm text-gray-400">Monitor GitHub Actions, GitLab CI, and CircleCI all in one lightweight unified view.</p>
						</div>
					</div>
				</div>
			</div>

			<div class="flex justify-center lg:justify-end">
				<div class="relative">
					<div class="relative rounded-xl overflow-hidden shadow-2xl border border-white/10 bg-gray-950">
						<div class="h-8 bg-gray-900 border-b border-white/5 flex items-center px-4 gap-2">
							<div class="h-3 w-3 rounded-full bg-red-500/80"></div>
							<div class="h-3 w-3 rounded-full bg-yellow-500/80"></div>
							<div class="h-3 w-3 rounded-full bg-green-500/80"></div>
						</div>
						<div class="p-6 bg-gray-900">
							<div class="space-y-3">
								<div class="flex items-center gap-3 bg-gray-800 p-2 rounded-lg border border-gray-700">
									<div class="h-2 w-2 rounded-full bg-green-500 shadow-[0_0_8px_rgba(34,197,94,0.6)]"></div>
									<span class="text-xs text-gray-300 font-mono">master: passed</span>
								</div>
								<div class="flex items-center gap-3 bg-gray-800 p-2 rounded-lg border border-gray-700 opacity-60">
									<div class="h-2 w-2 rounded-full bg-blue-500 animate-pulse"></div>
									<span class="text-xs text-gray-300 font-mono">feat/ui: building</span>
								</div>
								<div class="flex items-center gap-3 bg-gray-800 p-2 rounded-lg border border-gray-700 opacity-40">
									<div class="h-2 w-2 rounded-full bg-red-500"></div>
									<span class="text-xs text-gray-300 font-mono">api: failed</span>
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
<section id="features" class="py-24 bg-gradient-to-b from-white to-gray-50">
	<div class="container mx-auto px-4 md:px-6">
		<div class="flex flex-col items-center text-center mb-20">
			<h2 class="text-4xl md:text-5xl font-bold tracking-tight text-gray-900 mb-6">
				Built for <span class="bg-clip-text text-transparent bg-gradient-to-r from-gray-900 to-blue-600">flow state</span>.
			</h2>
			<p class="text-xl text-gray-600 max-w-2xl mx-auto leading-relaxed">
				Cignaler gets out of your way until you need it. A tool designed for developers who value screen real estate and mental bandwidth.
			</p>
		</div>

		<div class="grid grid-cols-1 md:grid-cols-6 gap-6 max-w-7xl mx-auto">
			<!-- Intelligent Watchers Card - Large -->
			<div class="col-span-1 md:col-span-4 md:row-span-2 relative overflow-hidden rounded-3xl border border-gray-200 bg-white shadow-sm hover:shadow-md transition-all group">
				<div class="p-8 h-full flex flex-col justify-between relative z-10">
					<div class="max-w-md">
						<div class="w-12 h-12 rounded-2xl bg-gray-900/10 flex items-center justify-center mb-6 text-gray-900">
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-6 w-6">
								<path d="m12.83 2.18a2 2 0 0 0-1.66 0L2.6 6.08a1 1 0 0 0 0 1.83l8.58 3.91a2 2 0 0 0 1.66 0l8.58-3.9a1 1 0 0 0 0-1.83Z"></path>
								<path d="m22 17.65-9.17 4.16a2 2 0 0 1-1.66 0L2 17.65"></path>
								<path d="m22 12.65-9.17 4.16a2 2 0 0 1-1.66 0L2 12.65"></path>
							</svg>
						</div>
						<h3 class="text-2xl font-bold mb-3">Intelligent Watchers</h3>
						<p class="text-gray-600 text-lg">
							Don't watch everything. Define watchers using regex to track specific branches (e.g., <code class="text-xs bg-gray-100 px-1.5 py-0.5 rounded border border-gray-200">feat/.*</code>), PRs, or critical jobs.
						</p>
					</div>
					<div class="mt-8 bg-gray-950 rounded-xl p-4 shadow-xl border border-gray-800 transform group-hover:translate-y-[-5px] transition-transform duration-500">
						<div class="flex items-center gap-2 border-b border-gray-800 pb-3 mb-3">
							<div class="h-3 w-3 rounded-full bg-red-500/20 border border-red-500/50"></div>
							<div class="h-3 w-3 rounded-full bg-yellow-500/20 border border-yellow-500/50"></div>
							<div class="h-3 w-3 rounded-full bg-green-500/20 border border-green-500/50"></div>
							<span class="text-xs text-gray-500 ml-2 font-mono">cignaler.toml</span>
						</div>
						<div class="space-y-2 font-mono text-sm">
							<div class="flex"><span class="text-purple-400 mr-2">[[watchers]]</span></div>
							<div class="flex"><span class="text-blue-400 min-w-[80px]">name</span><span class="text-gray-400">=</span><span class="text-green-400 ml-2">"Frontend Feature"</span></div>
							<div class="flex"><span class="text-blue-400 min-w-[80px]">repo</span><span class="text-gray-400">=</span><span class="text-green-400 ml-2">"acme/webapp"</span></div>
							<div class="flex"><span class="text-blue-400 min-w-[80px]">branch</span><span class="text-gray-400">=</span><span class="text-yellow-400 ml-2">"feat/.*"</span><span class="text-gray-600 ml-4"># RegEx support</span></div>
						</div>
					</div>
				</div>
				<div class="absolute top-0 right-0 w-2/3 h-full bg-gradient-to-l from-gray-900/5 to-transparent pointer-events-none"></div>
			</div>

			<!-- Glanceable Status Card - Tall -->
			<div class="col-span-1 md:col-span-2 md:row-span-2 relative overflow-hidden rounded-3xl border border-gray-200 bg-white shadow-sm hover:shadow-md transition-all group">
				<div class="p-8 h-full flex flex-col relative z-10">
					<div class="w-12 h-12 rounded-2xl bg-amber-500/10 flex items-center justify-center mb-6 text-amber-600">
						<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-6 w-6">
							<polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"></polygon>
						</svg>
					</div>
					<h3 class="text-2xl font-bold mb-3">Glanceable Status</h3>
					<p class="text-gray-600 mb-8">
						Your CI health lives in your menu bar. Green means go, red means stop.
					</p>
					<div class="flex-1 flex flex-col justify-end">
						<div class="bg-gray-950 rounded-t-xl p-4 shadow-xl border-x border-t border-gray-800 transform translate-y-4 group-hover:translate-y-2 transition-transform duration-500">
							<div class="flex items-center justify-between border-b border-gray-800 pb-3 mb-4">
								<span class="text-xs text-gray-500 font-mono">Menu Bar</span>
								<div class="flex gap-2">
									<div class="h-2 w-2 rounded-full bg-gray-700"></div>
									<div class="h-2 w-2 rounded-full bg-gray-700"></div>
								</div>
							</div>
							<div class="flex items-center gap-3 bg-gray-900 p-2 rounded-lg border border-gray-800 mb-2">
								<div class="h-2 w-2 rounded-full bg-green-500 shadow-[0_0_8px_rgba(34,197,94,0.6)]"></div>
								<span class="text-xs text-gray-300 font-mono">master: passed</span>
							</div>
							<div class="flex items-center gap-3 bg-gray-900 p-2 rounded-lg border border-gray-800 mb-2 opacity-60">
								<div class="h-2 w-2 rounded-full bg-blue-500 animate-pulse"></div>
								<span class="text-xs text-gray-300 font-mono">feat/ui: building</span>
							</div>
							<div class="flex items-center gap-3 bg-gray-900 p-2 rounded-lg border border-gray-800 opacity-40">
								<div class="h-2 w-2 rounded-full bg-red-500"></div>
								<span class="text-xs text-gray-300 font-mono">api: failed</span>
							</div>
						</div>
					</div>
				</div>
				<div class="absolute top-0 right-0 w-2/3 h-full bg-gradient-to-l from-amber-500/5 to-transparent pointer-events-none"></div>
			</div>

			<!-- Multi-Provider Card -->
			<div class="col-span-1 md:col-span-2 relative overflow-hidden rounded-3xl border border-gray-200 bg-white shadow-sm hover:shadow-md transition-all group">
				<div class="p-8 h-full flex flex-col relative z-10">
					<div class="w-10 h-10 rounded-xl bg-blue-500/10 flex items-center justify-center mb-4 text-blue-600">
						<Terminal class="h-5 w-5" />
					</div>
					<h3 class="text-xl font-bold mb-2">Multi-Provider</h3>
					<p class="text-gray-600 text-sm mb-6">
						Support for GitHub Actions and GitLab CI.
					</p>
					<div class="bg-gray-950 rounded-xl p-4 shadow-lg border border-gray-800 transform group-hover:scale-105 transition-transform duration-500">
						<div class="space-y-3">
							<div class="flex items-center justify-between p-2 rounded bg-gray-900 border border-gray-800">
								<div class="flex items-center gap-2">
									<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-3 w-3 text-white">
										<line x1="6" x2="6" y1="3" y2="15"></line>
										<circle cx="18" cy="6" r="3"></circle>
										<circle cx="6" cy="18" r="3"></circle>
										<path d="M18 9a9 9 0 0 1-9 9"></path>
									</svg>
									<span class="text-xs text-gray-300 font-medium">GitHub</span>
								</div>
								<div class="h-1.5 w-1.5 rounded-full bg-green-500"></div>
							</div>
							<div class="flex items-center justify-between p-2 rounded bg-gray-900 border border-gray-800">
								<div class="flex items-center gap-2">
									<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="h-3 w-3 text-white">
										<circle cx="12" cy="12" r="10"></circle>
									</svg>
									<span class="text-xs text-gray-300 font-medium">GitLab</span>
								</div>
								<div class="h-1.5 w-1.5 rounded-full bg-green-500"></div>
							</div>
						</div>
					</div>
				</div>
			</div>

			<!-- Lightweight Card -->
			<div class="col-span-1 md:col-span-2 relative overflow-hidden rounded-3xl border border-gray-200 bg-white shadow-sm hover:shadow-md transition-all group">
				<div class="p-8 h-full flex flex-col relative z-10">
					<div class="w-10 h-10 rounded-xl bg-green-500/10 flex items-center justify-center mb-4 text-green-600">
						<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-5 w-5">
							<path d="M12 2v20M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6"></path>
						</svg>
					</div>
					<h3 class="text-xl font-bold mb-2">Lightweight</h3>
					<p class="text-gray-600 text-sm mb-6">
						Written in Rust. Fast, efficient, no bloat.
					</p>
					<div class="bg-gray-950 rounded-xl p-4 shadow-lg border border-gray-800">
						<div class="flex items-center justify-between">
							<span class="text-xs text-gray-400 font-mono">Binary size</span>
							<span class="text-sm font-bold text-green-400">~8MB</span>
						</div>
					</div>
				</div>
			</div>

			<!-- CLI First Card -->
			<div class="col-span-1 md:col-span-2 relative overflow-hidden rounded-3xl border border-gray-200 bg-white shadow-sm hover:shadow-md transition-all group">
				<div class="p-8 h-full flex flex-col relative z-10">
					<div class="w-10 h-10 rounded-xl bg-purple-500/10 flex items-center justify-center mb-4 text-purple-600">
						<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="h-5 w-5">
							<polyline points="16 18 22 12 16 6"></polyline>
							<polyline points="8 6 2 12 8 18"></polyline>
						</svg>
					</div>
					<h3 class="text-xl font-bold mb-2">CLI First</h3>
					<p class="text-gray-600 text-sm mb-6">
						Scriptable, automatable, composable.
					</p>
					<div class="bg-gray-950 rounded-xl p-4 shadow-lg border border-gray-800">
						<div class="font-mono text-sm space-y-1">
							<div class="flex items-center gap-2">
								<span class="text-gray-500">$</span>
								<span class="text-green-400">cignaler</span>
								<span class="text-blue-400">watch</span>
							</div>
							<div class="flex items-center gap-2">
								<span class="text-gray-500">$</span>
								<span class="text-green-400">cignaler</span>
								<span class="text-blue-400">status</span>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- Workflow Section -->
<section class="py-24 bg-white">
	<div class="container mx-auto px-4 md:px-6">
		<div class="flex flex-col items-center text-center mb-20">
			<h2 class="text-4xl md:text-5xl font-bold tracking-tight text-gray-900 mb-6">
				Set up in <span class="text-transparent bg-clip-text bg-gradient-to-r from-orange-500 to-blue-600">under 60 seconds</span>.
			</h2>
			<p class="text-xl text-gray-600 max-w-2xl mx-auto leading-relaxed">
				Three simple steps to regain your focus and stop context switching.
			</p>
		</div>

		<div class="max-w-4xl mx-auto">
			<div class="grid md:grid-cols-3 gap-8">
				<!-- Step 1 -->
				<div class="relative">
					<div class="flex flex-col items-center text-center">
						<div class="w-16 h-16 rounded-2xl bg-orange-500 text-white flex items-center justify-center text-2xl font-bold mb-6 shadow-lg shadow-orange-500/20">
							1
						</div>
						<h3 class="text-xl font-bold mb-3 text-gray-900">Install CLI</h3>
						<p class="text-gray-600 mb-6">
							Quick install via Homebrew, npm, or download the binary directly.
						</p>
						<div class="w-full bg-gray-950 rounded-xl p-4 shadow-xl border border-gray-800">
							<div class="font-mono text-sm text-left">
								<div class="flex items-center gap-2">
									<span class="text-gray-500">$</span>
									<span class="text-blue-400">brew install</span>
									<span class="text-gray-300">cignaler</span>
								</div>
							</div>
						</div>
					</div>
					<!-- Connector Line -->
					<div class="hidden md:block absolute top-8 left-full w-full h-0.5 bg-gradient-to-r from-orange-500 to-blue-600 opacity-20 -z-10"></div>
				</div>

				<!-- Step 2 -->
				<div class="relative">
					<div class="flex flex-col items-center text-center">
						<div class="w-16 h-16 rounded-2xl bg-blue-600 text-white flex items-center justify-center text-2xl font-bold mb-6 shadow-lg shadow-blue-600/20">
							2
						</div>
						<h3 class="text-xl font-bold mb-3 text-gray-900">Configure Watchers</h3>
						<p class="text-gray-600 mb-6">
							Define which pipelines, branches, or PRs you want to monitor.
						</p>
						<div class="w-full bg-gray-950 rounded-xl p-4 shadow-xl border border-gray-800">
							<div class="font-mono text-sm text-left">
								<div class="flex items-center gap-2">
									<span class="text-gray-500">$</span>
									<span class="text-green-400">cignaler</span>
									<span class="text-blue-400">add</span>
								</div>
							</div>
						</div>
					</div>
					<!-- Connector Line -->
					<div class="hidden md:block absolute top-8 left-full w-full h-0.5 bg-gradient-to-r from-blue-600 to-purple-600 opacity-20 -z-10"></div>
				</div>

				<!-- Step 3 -->
				<div class="relative">
					<div class="flex flex-col items-center text-center">
						<div class="w-16 h-16 rounded-2xl bg-purple-600 text-white flex items-center justify-center text-2xl font-bold mb-6 shadow-lg shadow-purple-600/20">
							3
						</div>
						<h3 class="text-xl font-bold mb-3 text-gray-900">Stay Focused</h3>
						<p class="text-gray-600 mb-6">
							Get notified only when something you care about breaks.
						</p>
						<div class="w-full bg-gray-950 rounded-xl p-4 shadow-xl border border-gray-800 flex items-center justify-center">
							<div class="flex items-center gap-2">
								<div class="h-3 w-3 rounded-full bg-green-500 shadow-[0_0_8px_rgba(34,197,94,0.6)]"></div>
								<span class="text-xs text-gray-300 font-mono">All systems green</span>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- Bottom CTA Section -->
<section class="py-24 bg-white">
	<div class="container mx-auto px-4 md:px-6">
		<div class="relative rounded-[2.5rem] bg-gradient-to-br from-gray-900 via-gray-800 to-gray-900 overflow-hidden shadow-2xl">
			<!-- Background Effects -->
			<div class="absolute inset-0 bg-[radial-gradient(circle_at_30%_50%,rgba(249,115,22,0.1),transparent_50%)]"></div>
			<div class="absolute inset-0 bg-[radial-gradient(circle_at_70%_50%,rgba(59,130,246,0.1),transparent_50%)]"></div>

			<div class="relative z-10 py-24 px-8 md:px-16">
		<div class="max-w-4xl mx-auto text-center">
			<div class="inline-flex items-center gap-2 rounded-full bg-white/10 border border-white/10 px-4 py-1.5 text-sm font-medium text-white mb-8 backdrop-blur-md">
				<span class="relative flex h-2 w-2">
					<span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-orange-400 opacity-75"></span>
					<span class="relative inline-flex rounded-full h-2 w-2 bg-orange-500"></span>
				</span>
				Free forever for personal use
			</div>

			<h2 class="text-4xl md:text-6xl lg:text-7xl font-bold tracking-tight text-white mb-8 leading-[1.1]">
				Stop watching.
				<br />
				<span class="text-transparent bg-clip-text bg-gradient-to-r from-orange-500 to-blue-500">
					Start building.
				</span>
			</h2>

			<p class="text-xl md:text-2xl text-gray-300 max-w-2xl mx-auto mb-12 leading-relaxed">
				Join thousands of developers who've reclaimed their focus and stopped staring at CI dashboards.
			</p>

			<div class="flex flex-col sm:flex-row items-center justify-center gap-4 mb-12">
				<button class="inline-flex items-center justify-center h-14 px-8 text-lg rounded-full bg-orange-500 text-white font-medium shadow-xl shadow-orange-500/20 hover:shadow-orange-500/30 transition-all hover:scale-105">
					<Terminal class="mr-2 h-5 w-5" />
					Install CLI
				</button>
				<button class="inline-flex items-center justify-center h-14 px-8 text-lg rounded-full border-2 border-white/20 bg-white/10 backdrop-blur-sm text-white font-medium hover:bg-white/20 transition-all">
					<Github class="mr-2 h-5 w-5" />
					View on GitHub
				</button>
			</div>

			<!-- Stats -->
			<div class="grid grid-cols-3 gap-8 max-w-2xl mx-auto pt-12 border-t border-white/10">
				<div>
					<div class="text-3xl md:text-4xl font-bold text-white mb-2">10k+</div>
					<div class="text-sm text-gray-400">Active Users</div>
				</div>
				<div>
					<div class="text-3xl md:text-4xl font-bold text-white mb-2">50k+</div>
					<div class="text-sm text-gray-400">Pipelines Monitored</div>
				</div>
				<div>
					<div class="text-3xl md:text-4xl font-bold text-white mb-2">99.9%</div>
					<div class="text-sm text-gray-400">Uptime</div>
				</div>
			</div>
		</div>
			</div>
		</div>
	</div>
</section>

<!-- Footer -->
<footer class="bg-gray-50 border-t border-gray-200">
	<div class="container mx-auto px-4 md:px-6 py-12">
		<div class="grid grid-cols-1 md:grid-cols-4 gap-8 mb-8">
			<!-- Brand Column -->
			<div class="md:col-span-1">
				<div class="flex items-center gap-2 mb-4">
					<div class="flex h-8 w-8 items-center justify-center rounded-lg bg-gray-900/10 text-gray-900">
						<Activity class="h-5 w-5" />
					</div>
					<span class="text-xl font-bold tracking-tight text-gray-900">Cignaler</span>
				</div>
				<p class="text-sm text-gray-600">
					Stop staring at broken pipelines. Get notified only when it matters.
				</p>
			</div>

			<!-- Product Column -->
			<div>
				<h3 class="font-semibold text-gray-900 mb-4">Product</h3>
				<ul class="space-y-3 text-sm">
					<li><a href="#features" class="text-gray-600 hover:text-gray-900 transition-colors">Features</a></li>
					<li><a href="#how-it-works" class="text-gray-600 hover:text-gray-900 transition-colors">How it works</a></li>
					<li><a href="#" class="text-gray-600 hover:text-gray-900 transition-colors">Pricing</a></li>
					<li><a href="#" class="text-gray-600 hover:text-gray-900 transition-colors">Documentation</a></li>
				</ul>
			</div>

			<!-- Company Column -->
			<div>
				<h3 class="font-semibold text-gray-900 mb-4">Company</h3>
				<ul class="space-y-3 text-sm">
					<li><a href="#" class="text-gray-600 hover:text-gray-900 transition-colors">About</a></li>
					<li><a href="#" class="text-gray-600 hover:text-gray-900 transition-colors">Blog</a></li>
					<li><a href="#" class="text-gray-600 hover:text-gray-900 transition-colors">Careers</a></li>
					<li><a href="#" class="text-gray-600 hover:text-gray-900 transition-colors">Contact</a></li>
				</ul>
			</div>

			<!-- Resources Column -->
			<div>
				<h3 class="font-semibold text-gray-900 mb-4">Resources</h3>
				<ul class="space-y-3 text-sm">
					<li><a href="https://github.com/" target="_blank" rel="noopener noreferrer" class="text-gray-600 hover:text-gray-900 transition-colors">GitHub</a></li>
					<li><a href="#" class="text-gray-600 hover:text-gray-900 transition-colors">Community</a></li>
					<li><a href="#" class="text-gray-600 hover:text-gray-900 transition-colors">Support</a></li>
					<li><a href="#" class="text-gray-600 hover:text-gray-900 transition-colors">Status</a></li>
				</ul>
			</div>
		</div>

		<!-- Bottom Bar -->
		<div class="pt-8 border-t border-gray-200 flex flex-col md:flex-row justify-between items-center gap-4">
			<p class="text-sm text-gray-600">
				© 2024 Cignaler. All rights reserved.
			</p>
			<div class="flex items-center gap-6 text-sm text-gray-600">
				<a href="#" class="hover:text-gray-900 transition-colors">Privacy Policy</a>
				<a href="#" class="hover:text-gray-900 transition-colors">Terms of Service</a>
				<a href="#" class="hover:text-gray-900 transition-colors">Cookie Policy</a>
			</div>
		</div>
	</div>
</footer>

<style>
	@keyframes fadeIn {
		from {
			opacity: 0;
			transform: translateY(20px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}
</style>
