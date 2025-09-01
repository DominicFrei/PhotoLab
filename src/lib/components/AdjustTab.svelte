<script lang="ts">
	type Props = {
		brightness: number;
		contrast: number;
		rotation: number;
		saturation: number;
		vibrance: number;
		exposure: number;
		highlights: number;
		shadows: number;
		whites: number;
		blacks: number;
		clarity: number;
		dehaze: number;
		onBrightnessChange: () => void;
		onContrastChange: () => void;
		onRotationChange: () => void;
		onSaturationChange: () => void;
		onVibranceChange: () => void;
		onExposureChange: () => void;
		onHighlightsChange: () => void;
		onShadowsChange: () => void;
		onWhitesChange: () => void;
		onBlacksChange: () => void;
		onClarityChange: () => void;
		onDehazeChange: () => void;
	};

	let {
		brightness = $bindable(),
		contrast = $bindable(),
		rotation = $bindable(),
		saturation = $bindable(),
		vibrance = $bindable(),
		exposure = $bindable(),
		highlights = $bindable(),
		shadows = $bindable(),
		whites = $bindable(),
		blacks = $bindable(),
		clarity = $bindable(),
		dehaze = $bindable(),
		onBrightnessChange,
		onContrastChange,
		onRotationChange,
		onSaturationChange,
		onVibranceChange,
		onExposureChange,
		onHighlightsChange,
		onShadowsChange,
		onWhitesChange,
		onBlacksChange,
		onClarityChange,
		onDehazeChange
	}: Props = $props();

	// Group expansion state
	let expandedGroups = $state({
		basic: false,
		tone: false,
		color: false,
		transform: false
	});

	function toggleGroup(groupName: keyof typeof expandedGroups) {
		expandedGroups[groupName] = !expandedGroups[groupName];
	}
</script>

<div class="space-y-4">
	<h3 class="text-lg font-medium text-gray-900">Image Adjustments</h3>

	<!-- Basic Adjustments Group -->
	<div class="rounded-lg border border-gray-200 bg-white">
		<button
			class="flex w-full items-center justify-between p-4 text-left hover:bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:outline-none focus:ring-inset"
			onclick={() => toggleGroup('basic')}
			type="button"
		>
			<span class="text-sm font-medium text-gray-900">Basic Adjustments</span>
			<svg
				class="h-5 w-5 text-gray-500 transition-transform duration-200 {expandedGroups.basic
					? 'rotate-180'
					: ''}"
				fill="none"
				stroke="currentColor"
				viewBox="0 0 24 24"
			>
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
			</svg>
		</button>
		{#if expandedGroups.basic}
			<div class="border-t border-gray-200 p-4">
				<div class="grid gap-4 sm:grid-cols-2 lg:grid-cols-3">
					<!-- Exposure -->
					<div class="space-y-2">
						<label for="exposure-slider" class="block text-sm font-medium text-gray-700"
							>Exposure</label
						>
						<div class="space-y-2">
							<input
								id="exposure-slider"
								type="range"
								min="-200"
								max="200"
								bind:value={exposure}
								oninput={onExposureChange}
								class="slider h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
							/>
							<div class="flex justify-between text-xs text-gray-500">
								<span>-200</span>
								<span class="font-medium text-gray-900">{exposure}</span>
								<span>+200</span>
							</div>
						</div>
					</div>

					<!-- Brightness -->
					<div class="space-y-2">
						<label for="brightness-slider" class="block text-sm font-medium text-gray-700"
							>Brightness</label
						>
						<div class="space-y-2">
							<input
								id="brightness-slider"
								type="range"
								min="-100"
								max="100"
								bind:value={brightness}
								oninput={onBrightnessChange}
								class="slider h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
							/>
							<div class="flex justify-between text-xs text-gray-500">
								<span>-100</span>
								<span class="font-medium text-gray-900">{brightness}</span>
								<span>+100</span>
							</div>
						</div>
					</div>

					<!-- Contrast -->
					<div class="space-y-2">
						<label for="contrast-slider" class="block text-sm font-medium text-gray-700"
							>Contrast</label
						>
						<div class="space-y-2">
							<input
								id="contrast-slider"
								type="range"
								min="-100"
								max="100"
								bind:value={contrast}
								oninput={onContrastChange}
								class="slider h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
							/>
							<div class="flex justify-between text-xs text-gray-500">
								<span>-100</span>
								<span class="font-medium text-gray-900">{contrast}</span>
								<span>+100</span>
							</div>
						</div>
					</div>
				</div>
			</div>
		{/if}
	</div>

	<!-- Tone Adjustments Group -->
	<div class="rounded-lg border border-gray-200 bg-white">
		<button
			class="flex w-full items-center justify-between p-4 text-left hover:bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:outline-none focus:ring-inset"
			onclick={() => toggleGroup('tone')}
			type="button"
		>
			<span class="text-sm font-medium text-gray-900">Tone Adjustments</span>
			<svg
				class="h-5 w-5 text-gray-500 transition-transform duration-200 {expandedGroups.tone
					? 'rotate-180'
					: ''}"
				fill="none"
				stroke="currentColor"
				viewBox="0 0 24 24"
			>
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
			</svg>
		</button>
		{#if expandedGroups.tone}
			<div class="border-t border-gray-200 p-4">
				<div class="grid gap-4 sm:grid-cols-2 lg:grid-cols-4">
					<!-- Highlights -->
					<div class="space-y-2">
						<label for="highlights-slider" class="block text-sm font-medium text-gray-700"
							>Highlights</label
						>
						<div class="space-y-2">
							<input
								id="highlights-slider"
								type="range"
								min="-100"
								max="100"
								bind:value={highlights}
								oninput={onHighlightsChange}
								class="slider h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
							/>
							<div class="flex justify-between text-xs text-gray-500">
								<span>-100</span>
								<span class="font-medium text-gray-900">{highlights}</span>
								<span>+100</span>
							</div>
						</div>
					</div>

					<!-- Shadows -->
					<div class="space-y-2">
						<label for="shadows-slider" class="block text-sm font-medium text-gray-700"
							>Shadows</label
						>
						<div class="space-y-2">
							<input
								id="shadows-slider"
								type="range"
								min="-100"
								max="100"
								bind:value={shadows}
								oninput={onShadowsChange}
								class="slider h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
							/>
							<div class="flex justify-between text-xs text-gray-500">
								<span>-100</span>
								<span class="font-medium text-gray-900">{shadows}</span>
								<span>+100</span>
							</div>
						</div>
					</div>

					<!-- Whites -->
					<div class="space-y-2">
						<label for="whites-slider" class="block text-sm font-medium text-gray-700">Whites</label
						>
						<div class="space-y-2">
							<input
								id="whites-slider"
								type="range"
								min="-100"
								max="100"
								bind:value={whites}
								oninput={onWhitesChange}
								class="slider h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
							/>
							<div class="flex justify-between text-xs text-gray-500">
								<span>-100</span>
								<span class="font-medium text-gray-900">{whites}</span>
								<span>+100</span>
							</div>
						</div>
					</div>

					<!-- Blacks -->
					<div class="space-y-2">
						<label for="blacks-slider" class="block text-sm font-medium text-gray-700">Blacks</label
						>
						<div class="space-y-2">
							<input
								id="blacks-slider"
								type="range"
								min="-100"
								max="100"
								bind:value={blacks}
								oninput={onBlacksChange}
								class="slider h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
							/>
							<div class="flex justify-between text-xs text-gray-500">
								<span>-100</span>
								<span class="font-medium text-gray-900">{blacks}</span>
								<span>+100</span>
							</div>
						</div>
					</div>
				</div>
			</div>
		{/if}
	</div>

	<!-- Color Adjustments Group -->
	<div class="rounded-lg border border-gray-200 bg-white">
		<button
			class="flex w-full items-center justify-between p-4 text-left hover:bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:outline-none focus:ring-inset"
			onclick={() => toggleGroup('color')}
			type="button"
		>
			<span class="text-sm font-medium text-gray-900">Color Adjustments</span>
			<svg
				class="h-5 w-5 text-gray-500 transition-transform duration-200 {expandedGroups.color
					? 'rotate-180'
					: ''}"
				fill="none"
				stroke="currentColor"
				viewBox="0 0 24 24"
			>
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
			</svg>
		</button>
		{#if expandedGroups.color}
			<div class="border-t border-gray-200 p-4">
				<div class="grid gap-4 sm:grid-cols-2 lg:grid-cols-4">
					<!-- Saturation -->
					<div class="space-y-2">
						<label for="saturation-slider" class="block text-sm font-medium text-gray-700"
							>Saturation</label
						>
						<div class="space-y-2">
							<input
								id="saturation-slider"
								type="range"
								min="-100"
								max="100"
								bind:value={saturation}
								oninput={onSaturationChange}
								class="slider h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
							/>
							<div class="flex justify-between text-xs text-gray-500">
								<span>-100</span>
								<span class="font-medium text-gray-900">{saturation}</span>
								<span>+100</span>
							</div>
						</div>
					</div>

					<!-- Vibrance -->
					<div class="space-y-2">
						<label for="vibrance-slider" class="block text-sm font-medium text-gray-700"
							>Vibrance</label
						>
						<div class="space-y-2">
							<input
								id="vibrance-slider"
								type="range"
								min="-100"
								max="100"
								bind:value={vibrance}
								oninput={onVibranceChange}
								class="slider h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
							/>
							<div class="flex justify-between text-xs text-gray-500">
								<span>-100</span>
								<span class="font-medium text-gray-900">{vibrance}</span>
								<span>+100</span>
							</div>
						</div>
					</div>

					<!-- Clarity -->
					<div class="space-y-2">
						<label for="clarity-slider" class="block text-sm font-medium text-gray-700"
							>Clarity</label
						>
						<div class="space-y-2">
							<input
								id="clarity-slider"
								type="range"
								min="-100"
								max="100"
								bind:value={clarity}
								oninput={onClarityChange}
								class="slider h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
							/>
							<div class="flex justify-between text-xs text-gray-500">
								<span>-100</span>
								<span class="font-medium text-gray-900">{clarity}</span>
								<span>+100</span>
							</div>
						</div>
					</div>

					<!-- Dehaze -->
					<div class="space-y-2">
						<label for="dehaze-slider" class="block text-sm font-medium text-gray-700">Dehaze</label
						>
						<div class="space-y-2">
							<input
								id="dehaze-slider"
								type="range"
								min="-100"
								max="100"
								bind:value={dehaze}
								oninput={onDehazeChange}
								class="slider h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
							/>
							<div class="flex justify-between text-xs text-gray-500">
								<span>-100</span>
								<span class="font-medium text-gray-900">{dehaze}</span>
								<span>+100</span>
							</div>
						</div>
					</div>
				</div>
			</div>
		{/if}
	</div>

	<!-- Transform Group -->
	<div class="rounded-lg border border-gray-200 bg-white">
		<button
			class="flex w-full items-center justify-between p-4 text-left hover:bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:outline-none focus:ring-inset"
			onclick={() => toggleGroup('transform')}
			type="button"
		>
			<span class="text-sm font-medium text-gray-900">Transform</span>
			<svg
				class="h-5 w-5 text-gray-500 transition-transform duration-200 {expandedGroups.transform
					? 'rotate-180'
					: ''}"
				fill="none"
				stroke="currentColor"
				viewBox="0 0 24 24"
			>
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
			</svg>
		</button>
		{#if expandedGroups.transform}
			<div class="border-t border-gray-200 p-4">
				<div class="max-w-sm">
					<!-- Rotation -->
					<div class="space-y-2">
						<label for="rotation-slider" class="block text-sm font-medium text-gray-700"
							>Rotation</label
						>
						<div class="space-y-2">
							<input
								id="rotation-slider"
								type="range"
								min="0"
								max="360"
								bind:value={rotation}
								oninput={onRotationChange}
								class="slider h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
							/>
							<div class="flex justify-between text-xs text-gray-500">
								<span>0°</span>
								<span class="font-medium text-gray-900">{rotation}°</span>
								<span>360°</span>
							</div>
						</div>
					</div>
				</div>
			</div>
		{/if}
	</div>

	<!-- Reset All Button -->
	<div class="flex justify-center border-t border-gray-200 pt-4">
		<button
			class="rounded-md border border-gray-300 bg-white px-4 py-2 text-sm font-medium text-gray-700 hover:bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:outline-none"
			onclick={() => {
				exposure = 0;
				brightness = 0;
				contrast = 0;
				highlights = 0;
				shadows = 0;
				whites = 0;
				blacks = 0;
				saturation = 0;
				vibrance = 0;
				clarity = 0;
				dehaze = 0;
				rotation = 0;

				// Trigger updates for all adjustments
				onExposureChange();
				onBrightnessChange();
				onContrastChange();
				onHighlightsChange();
				onShadowsChange();
				onWhitesChange();
				onBlacksChange();
				onSaturationChange();
				onVibranceChange();
				onClarityChange();
				onDehazeChange();
				onRotationChange();
			}}
		>
			Reset All Adjustments
		</button>
	</div>
</div>

<style>
	.slider::-webkit-slider-thumb {
		appearance: none;
		height: 20px;
		width: 20px;
		border-radius: 50%;
		background: #2563eb;
		cursor: pointer;
		border: 2px solid white;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
	}

	.slider::-moz-range-thumb {
		height: 20px;
		width: 20px;
		border-radius: 50%;
		background: #2563eb;
		cursor: pointer;
		border: 2px solid white;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
	}
</style>
