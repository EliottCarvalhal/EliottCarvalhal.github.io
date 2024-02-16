<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import * as Card from '$lib/components/ui/card';
	import * as Carousel from '$lib/components/ui/carousel/index.js';

	let hellokitty = 'https://i.imgur.com/rbuaSTA.jpg';
	let keroppi = 'https://i.imgur.com/7Iy6EMv.jpg';
	let baekhyun = 'https://i.imgur.com/UL04RWz.png';

	//why the fuck do people upload fake jpg pictures with the fucking squares when it's not a fucking jpg
	let hearts = 'https://i.imgur.com/HYvLArr.png';

	let img1 = 'https://i.imgur.com/sOZckZV.jpg';
	let img2 = 'https://i.imgur.com/rzCf9IJ.jpg';
	let img3 = 'https://i.imgur.com/rhGgTi9.jpg';
	let img4 = 'https://i.imgur.com/Yv1PztH.jpg';
	let img5 = 'https://i.imgur.com/xNaIKTK.jpg';
	let img6 = 'https://i.imgur.com/4Vv6fhw.jpg';
	let imgs = [img1, img2, img3, img4, img5, img6];

	let showStart = true;
	let showPictures = false;

	const togglePictures = () => {
		showPictures = true;
		showStart = false;
	};
	const toggleStart = () => {
		showStart = true;
		showPictures = false;
	};
</script>

<div class="pt-16 bg-[#FFF6F7] h-[100vh]">
	<!-- title -->
	<div class="flex justify-center py-10">
		<h1 class="text-3xl text-center">Bemelie & Gnälliott 4ever</h1>
	</div>
	<!-- navigation buttons-->
	<div class="flex space-x-6 justify-center">
		<img src={keroppi} alt="keroppi" class="w-10 h-10" />
		<Button on:click={toggleStart} class="bg-red-200 hover:bg-red-100 active:bg-red-300"
			>start</Button
		>
		<Button on:click={togglePictures} class="bg-red-200 hover:bg-red-100 active:bg-red-300"
			>bilder</Button
		>
		<img src={hellokitty} alt="hello kitty holding a camera" class="w-10 h-10" />
	</div>
	<!-- start page -->
	{#if showStart}
		<div class="flex-col text-center pt-14 p-3">
			<h1 class=" text-2xl">Glad alla hjärtans dag !</h1>
			<p class="pt-2 leading-8">
				Jag älskar dig så mycket! Jag hoppas att du och jag kan spendera många flera valentines days
				tillsammans !!
			</p>
		</div>
		<div class="flex flex-col justify-center pt-2">
			<img src={hearts} alt="many hearts" class=" self-center" />

			<img src={baekhyun} alt="baekhyun from EXO" class="w-16 h-16 self-center" />
			<p class="text-xs self-center pt-36">varför kollar du här nere? 🤨</p>
		</div>
	{/if}
	<!-- picture carousel page -->
	{#if showPictures}
		<div class="p-20">
			<!-- why does this component add mt-10 -->
			<Carousel.Root class="w-full self-center -mt-10">
				<Carousel.Content>
					{#each Array(imgs.length) as _, i (i)}
						<Carousel.Item>
							<div class="p-1 sm:flex sm:justify-center">
								<Card.Root class=" sm:h-[30vw] sm:w-[30vh]  ">
									<Card.Content
										class="flex aspect-square items-center rounded-l justify-center p-6 bg-red-200 "
									>
										<div class="object-cover">
											<img src={imgs[i]} alt="emelie and i" />
										</div>
									</Card.Content>
								</Card.Root>
							</div>
						</Carousel.Item>
					{/each}
				</Carousel.Content>
			</Carousel.Root>
		</div>
	{/if}
</div>
