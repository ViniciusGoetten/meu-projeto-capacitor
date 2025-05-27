<script>
	let tamanho = 12,
		qnt = 1;
	let maius = true,
		minus = true,
		num = true,
		simb = true;
	let senhas = [];

	const chars = {
		maius: 'ABCDEFGHIJKLMNOPQRSTUVWXYZ',
		minus: 'abcdefghijklmnopqrstuvwxyz',
		num: '0123456789',
		simb: '!@#$%&*'
	};

	function gerar() {
		let pool = '';
		if (maius) pool += chars.maius;
		if (minus) pool += chars.minus;
		if (num) pool += chars.num;
		if (simb) pool += chars.simb;
		if (!pool) return (senhas = []);

		senhas = Array.from({ length: qnt }, () =>
			Array.from({ length: tamanho }, () => pool[Math.floor(Math.random() * pool.length)]).join('')
		);
	}

	const copiar = (s) => navigator.clipboard.writeText(s).then(() => alert('Senha copiada!'));
</script>

<div class="box">
	<h1>Gerador de Senhas</h1>

	<label>Tamanho: {tamanho}</label>
	<input type="range" min="5" max="30" bind:value={tamanho} />

	<label>Quantidade de Senha: {qnt}</label>
	<input type="number" min="1" max="10" bind:value={qnt} />

	<div class="checks">
		<label><input type="checkbox" bind:checked={maius} /> Maiúsculas</label>
		<label><input type="checkbox" bind:checked={minus} /> Minúsculas</label>
		<label><input type="checkbox" bind:checked={num} /> Números</label>
		<label><input type="checkbox" bind:checked={simb} /> Símbolos</label>
	</div>

	<button on:click={gerar}> Gerar</button>

	{#if senhas.length}
		<div class="resultado">
			{#each senhas as s}
				<div class="senha">
					<span>{s}</span>
					<button on:click={() => copiar(s)}>📋</button>
				</div>
			{/each}
		</div>
	{/if}
</div>

<style>
	.box {

		background: #99c6f5;
		padding: 20px;
		border-radius: 16px;
		max-width: 400px;
		margin: auto;
		font-family: Georgia, 'Times New Roman', Times, serif;
		color: #003366;
		box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
	}

	h1 {
		text-align: center;
		color: #005c99;
		margin-bottom: 20px;
		font-size: 24px;
	}

	label {
		display: block;
		margin: 10px 0 5px;
		font-weight: 600;
	}

	input[type='range'],
	input[type='number'] {
		width: 100%;
		padding: 8px;
		border-radius: 8px;
		border: 1px solid #3399cc;
		background: #ffffff;
		box-sizing: border-box;
	}

	.checks label {
		margin: 5px 0;
		display: block;
	}

	button {
		background: #3399cc;
		color: #fff;
		padding: 12px;
		width: 100%;
		border: none;
		border-radius: 10px;
		font-size: 16px;
		margin-top: 15px;
		cursor: pointer;
		transition: 0.3s;
	}
	button:hover {
		background: #267399;
	}

	.resultado {
		margin-top: 20px;
		background: #cce6ff;
		padding: 15px;
		border-radius: 12px;
	}

	.senha {
		background: #b3d9ff;
		padding: 10px;
		border-radius: 8px;
		margin-bottom: 10px;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	.senha span {
		font-weight: bold;
		color: #003366;
		word-break: break-word;
	}

	.senha button {
    background: #66b3ff;
    padding: 3px 8px;
    border-radius: 3px;
    color: #fff;
    font-size: 11px;
    border: none;
    cursor: pointer;
    width: 150px; 
}
	.senha button:hover {
		background: #3399cc;
	}
</style>
