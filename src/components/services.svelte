<script lang="ts">
  import Icon from "@iconify/svelte";
  import { SERVICES } from "../constants/services.constants";
  import { cn } from "../lib/utils";
  import gsap from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";
  import { onMount } from "svelte";

  gsap.registerPlugin(ScrollTrigger);

  let headingDescriptionEl: HTMLDivElement;
  let servicesButtonsEl: HTMLDivElement;
  let learnButtonEl: HTMLButtonElement;
  let imageDivEl: HTMLDivElement;

  let selectedService = $state("smart lighting");

  onMount(() => {
    const tl = gsap.timeline({
      scrollTrigger: {
        trigger: headingDescriptionEl,
        start: "top 80%",
      },
      defaults: { duration: 1, ease: "power2.out" },
    });

    gsap.fromTo(
      headingDescriptionEl,
      { autoAlpha: 0, x: -100 },
      {
        autoAlpha: 1,
        x: 0,
        duration: 1,
        ease: "power2.out",
        scrollTrigger: {
          trigger: headingDescriptionEl,
          start: "top 85%",
        },
      },
    );
    gsap.fromTo(
      servicesButtonsEl,
      { autoAlpha: 0, scale: 0.5 },
      {
        autoAlpha: 1,
        scale: 1,
        duration: 1,
        scrollTrigger: {
          trigger: servicesButtonsEl,
          start: "top 85%",
        },
      },
    );
    gsap.fromTo(
      learnButtonEl,
      { autoAlpha: 0, scale: 0.5 },
      {
        autoAlpha: 1,
        scale: 1,
        duration: 1,
        scrollTrigger: {
          trigger: learnButtonEl,
          start: "top 85%",
        },
      },
    );
    gsap.fromTo(
      imageDivEl,
      { autoAlpha: 0 },
      {
        autoAlpha: 1,
        duration: 1,
        scrollTrigger: {
          trigger: imageDivEl,
          start: "top 85%",
        },
      },
    );
  });
</script>

<section class="bg-foreground text-background lg:p-20">
  <div
    class="mx-auto my-10 flex max-w-[1920px] flex-col gap-10 px-5 py-10 lg:flex-row lg:p-0"
  >
    <!-- Left side with buttons -->
    <div
      class="flex flex-col items-start justify-between gap-5 lg:mt-16 lg:w-1/3 lg:gap-0"
    >
      <!-- Heading and description -->
      <div bind:this={headingDescriptionEl} class="space-y-5">
        <h3 class="text-background inline-block text-4xl uppercase lg:text-6xl">
          the solutions we offer
        </h3>
        <p class="text-sm text-slate-300/60 lg:w-[25vw]">
          From installation to setup and support, we ensure your home is
          equipped with the latest technology, working smoothly and effortlessly
          - just the way you want it.
        </p>
      </div>
      <!-- Buttons for each service -->
      <div bind:this={servicesButtonsEl} class="flex flex-col gap-4">
        {#each SERVICES as service, i}
          <button
            class={`cursor-pointer text-start`}
            onclick={() => (selectedService = service.name)}
          >
            <p
              class={cn(
                "text-xl uppercase lg:text-2xl",
                selectedService === service.name && "text-secondary",
              )}
            >
              <span class="mr-10">{i < 10 ? `0${i + 1}` : i + 1}</span>
              {service.name}
            </p>
          </button>
        {/each}
      </div>
      <!-- Learn more button -->
      <button
        bind:this={learnButtonEl}
        class="bg-background text-foreground hidden w-max scale-110 cursor-pointer items-center gap-2 rounded-4xl px-4 py-2 uppercase transition-transform hover:scale-110 lg:flex lg:scale-100"
      >
        learn more
        <Icon
          icon="mdi:arrow-top-right"
          width="44"
          height="44"
          class="bg-foreground text-background -my-1 -mr-3 ml-2 rounded-full p-2"
        />
      </button>
    </div>

    <!-- Image with descriptions -->
    <div
      bind:this={imageDivEl}
      class="relative aspect-6/7 w-full rounded-3xl bg-[url('/services/services-photo.webp')] bg-cover bg-center lg:aspect-7/5"
    >
      <span
        class="absolute top-10 right-10 hidden text-end text-xs opacity-90 lg:block"
        >Our services are tailored <br /> to fit your lifestyle</span
      >
      <span
        class="absolute bottom-10 left-10 hidden text-xs opacity-90 lg:block"
        >We are ready to simplify <br /> your life and enhance <br /> your living
        experience</span
      >
      {#each SERVICES as service}
        <div
          class={cn(
            "absolute max-w-88 rounded-4xl border-t border-r border-white text-start backdrop-blur-md transition-all duration-300",
            service.classAbsolute,
            selectedService === service.name
              ? "p-6"
              : "hidden px-8 py-2 text-center lg:block",
          )}
        >
          <h3
            class={cn(
              "mb-2",
              selectedService === service.name
                ? "text-2xl uppercase"
                : "hidden lg:block lg:text-sm lg:capitalize",
            )}
          >
            {service.name}
          </h3>
          <p
            class={cn(
              "text-xs opacity-80",
              selectedService === service.name ? "block" : "hidden",
            )}
          >
            {service.description}
          </p>
          <a
            href={service.link}
            class={cn(
              "mt-4 inline-block text-sm underline",
              selectedService === service.name ? "block" : "hidden",
            )}
          >
            Learn More...
          </a>
          <span
            class={cn(
              "top-11 h-20 rounded-bl-3xl border-b border-l border-white bg-transparent",
              service.classLine,
              selectedService === service.name ? "hidden" : "absolute",
            )}
          ></span>
        </div>
      {/each}
    </div>

    <button
      class="bg-background text-foreground flex w-max cursor-pointer items-center gap-2 place-self-center rounded-4xl px-4 py-2 uppercase transition-transform hover:scale-110 lg:hidden"
    >
      learn more
      <Icon
        icon="mdi:arrow-top-right"
        width="44"
        height="44"
        class="bg-foreground text-background -my-1 -mr-3 ml-2 rounded-full p-2"
      />
    </button>
  </div>
</section>
