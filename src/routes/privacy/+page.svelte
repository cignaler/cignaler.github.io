<svelte:head>
	<title>Privacy Policy — Cignaler Chrome Extension</title>
	<meta name="description" content="Privacy policy for the Cignaler Chrome Extension. This extension does not collect, transmit, or store any personal data." />
</svelte:head>

<div class="min-h-screen bg-warm-50">
	<!-- Header -->
	<header class="bg-warm-50 border-b border-warm-200">
		<div class="container mx-auto px-4 md:px-6 py-6 flex items-center gap-3">
			<a href="/" class="flex items-center gap-2 hover:opacity-80 transition-opacity">
				<img src="/cignaler_icon.png" alt="Cignaler" class="h-8 w-8 rounded-lg" />
				<span class="font-display text-xl font-bold tracking-tight text-warm-900">Cignaler</span>
			</a>
		</div>
	</header>

	<!-- Content -->
	<main class="container mx-auto px-4 md:px-6 py-12 md:py-16">
		<div class="max-w-2xl mx-auto">
			<h1 class="font-display text-3xl md:text-4xl font-bold text-warm-900 mb-2">Privacy Policy</h1>
			<p class="text-warm-500 text-lg mb-8 pb-8 border-b border-warm-200">
				Cignaler — GitLab Pipeline Watcher (Chrome Extension)
			</p>

			<!-- Summary -->
			<div class="bg-green-50 border-l-4 border-green-500 rounded-r-lg p-5 mb-10">
				<p class="text-warm-800 text-sm leading-relaxed">
					<strong>Summary:</strong> This extension does not collect, transmit, or store any personal data. All communication happens locally between your browser and the Cignaler desktop app installed on your computer.
				</p>
			</div>

			<div class="prose prose-warm max-w-none">
				<h2>What This Extension Does</h2>
				<p>
					Cignaler detects when you are browsing a GitLab project and lets you add a pipeline watcher to your locally installed Cignaler desktop application with one click. It reads the current page URL to extract the project path and branch name, then sends that information to the desktop app.
				</p>

				<h2>Data Collection</h2>
				<p>This extension does <strong>not</strong> collect any personal data. Specifically:</p>
				<ul>
					<li>No analytics or telemetry of any kind</li>
					<li>No cookies, tracking pixels, or fingerprinting</li>
					<li>No browsing history is recorded or transmitted</li>
					<li>No user accounts or authentication</li>
					<li>No data is sent to any external server</li>
				</ul>

				<h2>Data Storage</h2>
				<p>
					The extension stores a small amount of configuration using Chrome's built-in <code>chrome.storage.sync</code> API:
				</p>
				<ul>
					<li><strong>CI server name</strong> — the name of your CI server as configured in the Cignaler desktop app</li>
					<li><strong>Custom GitLab hostnames</strong> — any self-hosted GitLab URLs you add so the extension can recognize them</li>
				</ul>
				<p>
					This data is stored locally in your browser profile (and synced across your Chrome instances if you are signed in to Chrome). It is never sent to any third party.
				</p>

				<h2>Network Communication</h2>
				<p>
					The extension communicates <strong>only</strong> with the Cignaler desktop application installed on your computer, using Chrome's <a href="https://developer.chrome.com/docs/extensions/develop/concepts/native-messaging" target="_blank" rel="noopener noreferrer">Native Messaging</a> protocol. This is a local IPC mechanism — no network requests are made.
				</p>
				<p>
					The extension reads the content of GitLab pages you visit (to extract the project path and branch/tag), but this information is only used locally and is never transmitted over the network.
				</p>

				<h2>Permissions Explained</h2>
				<ul>
					<li><strong>activeTab</strong> — allows the extension to read the current tab's URL and page content when you click the extension icon, so it can detect GitLab project information</li>
					<li><strong>storage</strong> — allows saving your settings (CI server name, custom hostnames) locally in Chrome</li>
					<li><strong>nativeMessaging</strong> — allows communication with the Cignaler desktop app on your computer</li>
					<li><strong>Host permissions (optional)</strong> — requested only for self-hosted GitLab instances you configure, so the extension can detect projects on those domains</li>
				</ul>

				<h2>Third-Party Services</h2>
				<p>
					This extension does not use any third-party services, SDKs, libraries, or APIs. It has no external dependencies.
				</p>

				<h2>Changes to This Policy</h2>
				<p>
					If this privacy policy is updated, the changes will be reflected on this page. The extension's core design principle — all data stays local — will not change.
				</p>
			</div>

			<footer class="mt-10 pt-8 border-t border-warm-200 flex items-center justify-between">
				<p class="text-sm text-warm-400">Last updated: February 2026</p>
				<a href="/" class="text-sm text-warm-500 hover:text-warm-900 transition-colors">&larr; Back to homepage</a>
			</footer>
		</div>
	</main>
</div>
