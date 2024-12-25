<svelte:options runes />

<script>
  import { onMount } from "svelte";
	import sparkleSfxRaw from '$lib/sounds/554312__opticaillusions__sparkly.wav';
  import crystalBall from '$lib/images/crystal-ball.png';

  let fortune = $state('');
	let isThinking = $state(false);
  let sparkleSfx;
	const newYearFortunes = [
		'This year, embrace change; it will lead you to unexpected opportunities.',
		'A new friendship will blossom in the most unlikely of places.',
		'Your creativity will shine brightly; let it guide your decisions.',
		'A journey awaits you—pack your bags and open your heart.',
		'This year, your hard work will finally pay off in ways you never imagined.',
		'A surprise gift will bring you joy and remind you of the love around you.',
		'Trust your instincts; they will lead you to the right path.',
		'A long-held dream will begin to take shape; nurture it with care.',
		'You will find balance in your life, bringing peace to your mind and spirit.',
		'A new skill learned this year will open doors to exciting adventures.',
		'Your kindness will create ripples of positivity in the lives of others.',
		'A financial opportunity will present itself; be ready to seize it.',
		'This year, let go of what no longer serves you; make space for the new.',
		'A moment of clarity will guide you to a significant decision.',
		'You will discover a hidden talent that brings you joy and fulfillment.',
		'A family reunion will strengthen bonds and create lasting memories.',
		'Your health will improve as you prioritize self-care and wellness.',
		'A mentor will enter your life, offering wisdom and guidance.',
		'This year, you will learn the power of gratitude and its impact on your life.',
		'A chance encounter will lead to a meaningful connection.',
		'Your laughter will be contagious; spread joy wherever you go.',
		'A project you start this year will exceed your expectations.',
		'You will find beauty in the little things; cherish each moment.',
		'A long-distance relationship will flourish through communication and trust.',
		'This year, you will step out of your comfort zone and thrive.',
		'A new perspective will help you overcome a challenge you"ve faced.',
		'You will inspire others with your passion and determination.',
		'A book you read will change your outlook on life.',
		'This year, you will cultivate a deeper understanding of yourself.',
		'Love is on the horizon; keep your heart open to new possibilities.'
	];


  async function getNewYearFortune() {
    if (isThinking) return;
    
    isThinking = true;
    fortune = '';

    try {
      // Play the sparkle sound
      if (sparkleSfx) {
        sparkleSfx.currentTime = 0; // Reset audio to start
        await sparkleSfx.play();
      }
    } catch (error) {
      console.log('Audio playback failed:', error);
    }

    setTimeout(() => {
      fortune = newYearFortunes[Math.floor(Math.random() * newYearFortunes.length)];
      isThinking = false;
    }, 2000);
  }

  onMount(() => {
    sparkleSfx = new Audio(sparkleSfxRaw);
    sparkleSfx.volume = 1.0;
  });
</script>

<div class="card">
	<header>
		<h1>
			<span class="sparkle">✨</span>
			2025 Fortune Teller
			<span class="sparkle">✨</span>
		</h1>
    <img src={crystalBall} alt="Crystal Ball"/>
	</header>

	<div class="content">
		<div class="button-container">
			<button onclick={getNewYearFortune} disabled={isThinking}>
				{isThinking ? 'Peering into 2025...' : 'Reveal My 2025 Fortune'}
			</button>
		</div>

		{#if fortune}
			<div class="fortune-display">
				<p>{fortune}</p>
			</div>
		{/if}
	</div>
</div>

<style>
	.card {
		width: 100%;
		max-width: 500px;
		margin: 0 auto;
		padding: 1.5rem;
		border-radius: 12px;
		background: linear-gradient(to bottom right, #1e3a8a, #4c1d95);
		color: white;
	}

	header {
		text-align: center;
		margin-bottom: 1.5rem;
	}

	h1 {
		font-size: 1.5rem;
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 0.5rem;
	}

	.sparkle {
		color: #ffd700;
	}

	.content {
		display: flex;
		flex-direction: column;
		gap: 1.5rem;
	}

	.button-container {
		text-align: center;
	}

	button {
		background-color: #2563eb;
		color: white;
		padding: 0.75rem 1.5rem;
		border: none;
		border-radius: 8px;
		font-size: 1.125rem;
		cursor: pointer;
		transition: background-color 0.3s ease;
	}

	button:hover:not(:disabled) {
		background-color: #3b82f6;
	}

	button:disabled {
		opacity: 0.7;
		cursor: wait;
	}

	.fortune-display {
		margin-top: 1.5rem;
		padding: 1.5rem;
		background-color: rgba(30, 58, 138, 0.3);
		border-radius: 8px;
		border: 1px solid rgba(59, 130, 246, 0.3);
		min-height: 120px;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.fortune-display p {
		font-size: 1.125rem;
		font-weight: 500;
		line-height: 1.6;
		margin: 0;
	}
</style>
