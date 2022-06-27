<!-- This example requires Tailwind CSS v2.0+ -->
<template>
	<Listbox as="div" v-model="selected">
		<ListboxLabel class="sr-only"> Change language </ListboxLabel>
		<div class="relative">
			<div class="flex rounded-md divide-x justify-center">
				<ListboxOption
					as="template"
					v-for="option in publishingOptions"
					:key="option.title"
					:value="option"
					v-slot="{ active, selected }"
				>
					<div
						:class="[
							active
								? 'text-white bg-indigo-500'
								: 'text-gray-900',
							'cursor-default select-none p-4 text-sm w-full',
						]"
					>
						<div class="flex flex-col">
							<div class="flex pr-5">
								<p
									:class="
										selected
											? 'font-semibold'
											: 'font-normal'
									"
								>
									{{ option.title }}
								</p>
								<span
									v-if="selected"
									:class="
										active
											? 'text-white'
											: 'text-indigo-500'
									"
								>
									<CheckIcon
										class="h-5 w-5 ml-2"
										aria-hidden="true"
									/>
								</span>
							</div>
						</div>
					</div>
				</ListboxOption>
			</div>
		</div>
	</Listbox>
</template>

<script setup>
	import { ref } from 'vue';
	import {
		Listbox,
		ListboxButton,
		ListboxLabel,
		ListboxOption,
		ListboxOptions,
	} from '@headlessui/vue';
	import { CheckIcon, ChevronDownIcon } from '@heroicons/vue/solid';

	const publishingOptions = [
		{
			title: 'Čeština',
			current: true,
		},
		{
			title: 'English',
			current: false,
		},
		{
			title: 'Deutsch',
			current: false,
		},
	];

	const selected = ref(publishingOptions[0]);
</script>
