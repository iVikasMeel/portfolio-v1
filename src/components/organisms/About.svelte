<script>
	import RichPresence from '../molecules/RichPresence.svelte';
	import Tooltip from '../atoms/Tooltip.svelte';

	let getAge = () => {
		let birthDate = new Date('2002/02/17');
		const ageMs = Date.now() - birthDate.getTime();
		const preciseAge = (ageMs / 31536000000).toFixed(10);
		return preciseAge;
	};

	let age = getAge();
	setInterval(() => {
		age = getAge();
	}, 1000);
</script>

<section id="about" class="wrapper">
	<div>
		<RichPresence />
	</div>
	<div class="text">
		<h2>bio</h2>
		<p>
			Hey there, I’m Vikas! :] I’m a <Tooltip tip={age}
				><span>{Math.floor(Number(age))}</span></Tooltip
			>
			year old frontend developer and freelancer based in India. I’ve taken coding seriously since 
			<span>2022</span>, and have been freelancing since <span>2024</span>.
			Recently, however, I’ve grown a knack for giving back to community. I like contributing to 
			<Tooltip tip="🤓">
				<a href="https://github.com/xafn" target="_blank" rel="noreferrer">
					<span>open source</span>
				</a>
			</Tooltip>
			as a web developer, which is probably the reason why you've ended up here. Currently struggling
			with React and Javascript.
		</p>
	</div>
</section>

<style lang="scss">
	@import '../../styles/mixins.scss';

	section {
		margin-bottom: 6rem;
		display: grid;
		gap: 4.5rem;
		grid-template-columns: 1fr 1fr;
		align-items: center;
	}

	.text {
		position: relative;
		line-height: 1.75rem;
	}

	span {
		font-weight: 400;
		font-family: var(--font-two);
		font-size: 0.9rem;
		background-color: var(--elevation-one);
		border-radius: 7px;
		color: var(--accent);
		padding: 0.2rem 0.5rem 0.2rem;
		width: fit-content;
	}

	a {
		text-decoration: none;
	}

	.text::before {
		@include outlineText(
			$content: 'vks',
			$translateX: 97%,
			$translateY: -5%,
			$fontSize: 270px,
			$opacity: 0.22
		);
	}

	h2 {
		display: none;
		margin-top: 1rem;
	}

	@media (max-width: 868px) {
		section {
			display: flex;
			flex-direction: column;
			align-items: normal;
		}

		h2 {
			display: block;
			margin-bottom: 1rem;
		}
	}
</style>
