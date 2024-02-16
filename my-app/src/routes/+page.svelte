<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import * as Card from '$lib/components/ui/card';
	import * as Carousel from '$lib/components/ui/carousel/index.js';
	import * as Tabs from '$lib/components/ui/tabs';

	let img1 = 'https://i.imgur.com/rhGgTi9.jpg';
	let img2 = 'https://i.imgur.com/rzCf9IJ.jpg';
	let img3 = 'https://i.imgur.com/sOZckZV.jpg';
	let img4 = 'https://i.imgur.com/Yv1PztH.jpg';
	let img5 = 'https://i.imgur.com/4Vv6fhw.jpg';
	let img6 = 'https://i.imgur.com/xNaIKTK.jpg';
	let imgs = [img1, img2, img3, img4, img5, img6];

	let showStart = false;
	let showPictures = true;

	const togglePictures = () => {
		showPictures = true;
		showStart = false;
	};
	const toggleStart = () => {
		showStart = true;
		showPictures = false;
	};

	const removeButtons = () => {
		const els = document.querySelectorAll('[aria-roledescription="carousel"] > button');
		els.forEach((el) => {
			el.remove();
		});
	};
	// removeButtons()
</script>

<div class="pt-16 bg-[#FFF6F7] h-[100vh]">
	<div class="flex space-x-6 justify-center">
		<p on:click={toggleStart} class="hover:text-blue-300 cursor-pointer">start</p>
		<p on:click={togglePictures} class="hover:text-blue-300 cursor-pointer">bilder</p>
	</div>
	{#if showStart}
		<div class="flex-col text-center pt-14 p-3">
			<h1 class=" text-2xl">Glad alla hjärtans dag !</h1>
			<p class="pt-2">
				Jag älskar dig så mycket! Jag hoppas att du och jag kan spendera många flera alla hjärtans
				dag tillsammans!
			</p>
		</div>
	{/if}
	<div class="p-20">
		{#if showPictures}
			<Carousel.Root class="w-full self-center ">
				<Carousel.Content>
					{#each Array(5) as _, i (i)}
						<Carousel.Item>
							<div class="p-1">
								<Card.Root class=" min-h-full min-w-full ">
									<Card.Content
										class="flex aspect-square items-center rounded-l justify-center p-6 bg-red-200 "
									>
										<div class="object-cover">
											<img src={imgs[i]} alt="cool" />
										</div>
									</Card.Content>
								</Card.Root>
							</div>
						</Carousel.Item>
					{/each}
				</Carousel.Content>
			</Carousel.Root>
		{/if}
	</div>
</div>
