<!--
  This example requires Tailwind CSS v2.0+ 
  
  This example requires some changes to your config:
  
  ```
  // tailwind.config.js
  module.exports = {
    // ...
    plugins: [
      // ...
      require('@tailwindcss/forms'),
    ],
  }
  ```
-->
<template>
	<Disclosure as="header" class="bg-white shadow" v-slot="{ open }">
		<div
			class="max-w-7xl mx-auto px-2 sm:px-4 lg:divide-y lg:divide-gray-200 lg:px-8"
		>
			<div class="relative h-16 flex justify-between">
				<div class="relative z-10 px-2 flex lg:px-0">
					<div class="flex-shrink-0 flex items-center">
						<img
							class="block h-8 w-auto"
							src="https://tailwindui.com/img/logos/workflow-mark-indigo-600.svg"
							alt="Workflow"
						/>
					</div>
				</div>
				<div
					class="relative z-0 flex-1 px-2 flex items-center justify-center sm:absolute sm:inset-0"
				>
					<div class="w-full sm:max-w-xs">
						<label for="search" class="sr-only">Search</label>
						<div class="relative">
							<div
								class="pointer-events-none absolute inset-y-0 left-0 pl-3 flex items-center"
							>
								<SearchIcon
									class="h-5 w-5 text-gray-400"
									aria-hidden="true"
								/>
							</div>
							<input
								id="search"
								name="search"
								class="block w-full bg-white border border-gray-300 rounded-md py-2 pl-10 pr-3 text-sm placeholder-gray-500 focus:outline-none focus:text-gray-900 focus:placeholder-gray-400 focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
								placeholder="Search"
								type="search"
							/>
						</div>
					</div>
				</div>
				<div class="relative z-10 flex items-center lg:hidden">
					<!-- Mobile menu button -->
					<DisclosureButton
						class="rounded-md p-2 inline-flex items-center justify-center text-gray-400 hover:bg-gray-100 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-500"
					>
						<span class="sr-only">Open menu</span>
						<MenuIcon
							v-if="!open"
							class="block h-6 w-6"
							aria-hidden="true"
						/>
						<XIcon
							v-else
							class="block h-6 w-6"
							aria-hidden="true"
						/>
					</DisclosureButton>
				</div>
				<div
					class="hidden lg:relative lg:z-10 lg:ml-4 lg:flex lg:items-center"
				>
					<!-- Language selector -->
					<LanguageSelector />
				</div>
			</div>
			<div class="flex justify-between">
				<nav
					class="hidden lg:py-2 lg:flex lg:space-x-8"
					aria-label="Global"
				>
					<FlyoutMenu />
					<a
						v-for="item in navigation"
						:key="item.name"
						:href="item.href"
						:class="[
							item.current
								? 'bg-gray-100 text-gray-900'
								: 'text-gray-900 hover:bg-gray-50 hover:text-gray-900',
							'rounded-md py-2 px-3 inline-flex items-center text-sm font-medium',
						]"
						:aria-current="item.current ? 'page' : undefined"
					>
						{{ item.name }}
					</a>
				</nav>
				<div class="hidden lg:py-2 lg:flex lg:space-x-6">
					<button
						type="button"
						class="inline-flex items-center px-3 py-2 border border-transparent shadow-sm text-sm leading-4 font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
					>
						Do action
					</button>
					<button
						type="button"
						class="inline-flex items-center px-3 py-2 shadow-sm text-sm leading-4 font-medium rounded-md text-indigo-600 bg-white border-indigo-600 border-2 hover:bg-indigo-100 hover:border-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
					>
						See more
					</button>
				</div>
			</div>
		</div>

		<DisclosurePanel as="nav" class="lg:hidden" aria-label="Global">
			<div class="pt-2 pb-3 px-2 space-y-1">
				<FlyoutMenuMobile />
			</div>
			<div class="border-y border-gray-200 pt-4 pb-3">
				<!-- Language selector mobile -->
				<LanguageSelectorMobile />
			</div>
			<div class="pt-4 pb-3 px-2 flex gap-x-5">
				<button
					type="button"
					class="inline-flex items-center px-3 py-2 border-transparent shadow-sm text-sm leading-4 font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
				>
					Do action
				</button>
				<button
					type="button"
					class="inline-flex items-center px-3 py-2 shadow-sm text-sm leading-4 font-medium rounded-md text-indigo-600 bg-white border-indigo-600 border-2 hover:bg-indigo-100 hover:border-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
				>
					See more
				</button>
			</div>
		</DisclosurePanel>
	</Disclosure>
</template>

<script setup>
	import {
		Disclosure,
		DisclosureButton,
		DisclosurePanel,
		Menu,
		MenuButton,
		MenuItem,
		MenuItems,
	} from '@headlessui/vue';
	import { SearchIcon } from '@heroicons/vue/solid';
	import { BellIcon, MenuIcon, XIcon } from '@heroicons/vue/outline';
	import LanguageSelector from './components/LanguageSelector.vue';
	import LanguageSelectorMobile from './components/LanguageSelectorMobile.vue';
	import FlyoutMenu from './components/FlyoutMenu.vue';
	import FlyoutMenuMobile from './components/FlyoutMenuMobile.vue';

	const navigation = [
		{ name: 'Dashboard', href: '#', current: false },
		{ name: 'Team', href: '#', current: false },
		{ name: 'Projects', href: '#', current: false },
		{ name: 'Calendar', href: '#', current: false },
	];
</script>
