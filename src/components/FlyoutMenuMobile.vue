<!-- This example requires Tailwind CSS v2.0+ -->
<template>
	<nav class="flex-1 px-2 space-y-1 bg-white" aria-label="Sidebar">
		<template v-for="item in navigation" :key="item.name">
			<div v-if="!item.children">
				<a
					:href="item.href"
					:class="[
						item.current
							? 'bg-white text-gray-900'
							: 'text-gray-900 hover:bg-gray-50 hover:text-gray-900',
						'flex rounded-md py-3 px-3 text-base font-medium',
					]"
				>
					{{ item.name }}
				</a>
			</div>
			<Disclosure as="div" v-else class="space-y-1" v-slot="{ open }">
				<DisclosureButton
					:class="[
						item.current
							? 'bg-white text-gray-900'
							: 'text-gray-900 hover:bg-gray-50 hover:text-gray-900',
						'flex items-center rounded-md py-3 px-3 text-base font-medium',
					]"
				>
					<svg
						:class="[
							open ? 'text-gray-400 rotate-90' : 'text-gray-300',
							'mr-2 flex-shrink-0 h-5 w-5 transform group-hover:text-gray-400 transition-colors ease-in-out duration-150',
						]"
						viewBox="0 0 20 20"
						aria-hidden="true"
					>
						<path d="M6 6L14 10L6 14V6Z" fill="currentColor" />
					</svg>
					{{ item.name }}
				</DisclosureButton>
				<DisclosurePanel class="space-y-1">
					<DisclosureButton
						v-for="subItem in item.children"
						:key="subItem.name"
						as="a"
						:href="subItem.href"
						class="group w-full flex items-center pl-10 pr-2 py-3 text-sm font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50"
					>
						{{ subItem.name }}
					</DisclosureButton>
				</DisclosurePanel>
			</Disclosure>
		</template>
	</nav>
</template>

<script setup>
	import {
		Disclosure,
		DisclosureButton,
		DisclosurePanel,
	} from '@headlessui/vue';

	const navigation = [
		{
			name: 'Solutions',
			href: '#',
			current: true,
			children: [
				{ name: 'Blog', href: '#' },
				{ name: 'Help center', href: '#' },
				{ name: 'Guides', href: '#' },
				{ name: 'Events', href: '#' },
				{ name: 'Security', href: '#' },
			],
		},
		{ name: 'Dashboard', href: '#', current: true },
		{ name: 'Team', href: '#', current: true },
		{ name: 'Projects', href: '#', current: true },
		{ name: 'Calendar', href: '#', current: true },
	];
</script>
