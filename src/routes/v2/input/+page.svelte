<script lang="ts">
	import {
		InputV2 as Input,
		FlexV2 as Flex,
		TitleV2 as Title,
		CodeBlock,
		ButtonV2 as Button,
		GridV2 as Grid
	} from '$lib';

	type Color =
		| 'transparent'
		| 'white'
		| 'black'
		| 'slate'
		| 'zinc'
		| 'gray'
		| 'neutral'
		| 'stone'
		| 'red'
		| 'orange'
		| 'amber'
		| 'yellow'
		| 'lime'
		| 'green'
		| 'emerald'
		| 'teal'
		| 'cyan'
		| 'sky'
		| 'blue'
		| 'indigo'
		| 'violet'
		| 'purple'
		| 'fuchsia'
		| 'pink'
		| 'rose';

	let colors: Color[] = $state([
		'transparent',
		'white',
		'black',
		'slate',
		'zinc',
		'gray',
		'neutral',
		'stone',
		'red',
		'orange',
		'amber',
		'yellow',
		'lime',
		'green',
		'emerald',
		'teal',
		'cyan',
		'sky',
		'blue',
		'indigo',
		'violet',
		'purple',
		'fuchsia',
		'pink',
		'rose'
	]);

	type Size = 'sm' | 'md' | 'lg' | 'xl';

	let dark: boolean = $state(false);
</script>

<div class="h-[100vh] overflow-auto p-8">
	<Flex s={{ direction: 'col', gap: 4 }}>
		<Title s={{ color: 'white', size: 'lg' }}>Input</Title>
		<CodeBlock lang="ts" code={'import { Input } from "sveltekev";'} radius="lg" />
		<Title s={{ color: 'white', size: 'lg' }}>Colors</Title>
		<Flex s={{ gap: 4, items: 'center' }} class="p-0">
			<Title s={{ color: 'white' }}>Color levels</Title>
			<Button oc={() => (dark = !dark)} s={{ color: 'white', size: 'sm' }}>Toggle theme</Button>
		</Flex>
		<Grid s={{ gap: 4, color: dark ? 'black' : 'white' }}>
			{#each colors as color, i}
				{#each [1, 2, 3, 4, 5, 6] as colorLevel}
					<Grid item sz={4} class="p-0">
						<Input
							c={{ label: color, placeholder: 'Escribir...' }}
							s={{ color, colorLevel: colorLevel as 1 | 2 | 3 | 4 | 5 | 6 }}
							class="w-full"
						/>
					</Grid>
				{/each}
			{/each}
		</Grid>
	</Flex>
</div>
