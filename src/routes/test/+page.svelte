<script lang="ts">
	import CategoriaPicker from '$lib/components/CategoriaPicker.svelte';
	import Input from '$lib/components/ui/input/input.svelte';
	import NumberInput from '$lib/components/ui/input/number_input.svelte';
	import Label from '$lib/components/ui/label/label.svelte';
	let form = {
		produto_base: 'Heineken',
		preco_custo: 5.99,

		variacoes: [
			{
				nome: 'Longneck',
				precos: [
					{
						tipo: 'atacado',
						preco: 3.5
					},
					{
						tipo: 'varejo',
						preco: 5.0
					}
				]
			},
			{
				nome: 'Lata',
				precos: [
					{
						tipo: 'atacado',
						preco: 2.5
					},
					{
						tipo: 'varejo',
						preco: 4.0
					}
				]
			},
			{
				nome: '600ml',
				precos: [
					{
						tipo: 'atacado',
						preco: 4.5
					},
					{
						tipo: 'varejo',
						preco: 6.0
					}
				]
			},
			{
				nome: 'Emporio',
				precos: [
					{
						tipo: 'atacado',
						preco: 5.5
					},
					{
						tipo: 'varejo',
						preco: 7.0
					}
				]
			}
		]
	};
</script>

<main class="container flex items-center justify-center">
	<form action="">
		<div class="flex items-center justify-center">
			<Input bind:value={form.produto_base} />
		</div>

		<table>
			<tr class="bg-primary text-primary-foreground">
				<th>Categoria</th>
				<th>Atacado</th>
				<th>Varejo</th>
			</tr>
			{#each form.variacoes as variant}
				<tr>
					<td>
						<CategoriaPicker
							categorias={[
								{ value: 'Longneck', label: 'Longneck' },
								{ value: 'Lada', label: 'Lata' },
								{ value: '600ml', label: '600ml' },
								{ value: 'Emporio', label: 'Emporio' }
							]}
							value={variant.nome}
						/>
					</td>
					{#each variant.precos as pre}
						<td>
							<Input bind:value={pre.preco} />
						</td>
					{/each}
				</tr>
			{/each}
		</table>
	</form>
</main>
