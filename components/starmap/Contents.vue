<template>
  <TransitionRoot as="template" :show="open">
    <Dialog as="div" class="relative z-20" @close="open = false">
      <TransitionChild
        as="template"
        enter="ease-out duration-300"
        enter-from="opacity-0"
        enter-to="opacity-100"
        leave="ease-in duration-200"
        leave-from="opacity-100"
        leave-to="opacity-0"
      >
        <div
          class="fixed inset-0 bg-gray-900 bg-opacity-90 transition-opacity"
        />
      </TransitionChild>

      <div class="fixed inset-0 z-10 overflow-y-auto">
        <div
          class="flex min-h-full items-center justify-center p-2 sm:p-4 text-center"
        >
          <TransitionChild
            as="template"
            enter="ease-out duration-300"
            enter-from="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
            enter-to="opacity-100 translate-y-0 sm:scale-100"
            leave="ease-in duration-200"
            leave-from="opacity-100 translate-y-0 sm:scale-100"
            leave-to="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
          >
            <DialogPanel
              class="relative transform overflow-hidden rounded-3xl bg-space-gray-dark px-4 py-8 text-left shadow-xl transition-all sm:w-full lg:p-12 lg:pr-4"
              :class="
                discoveries[discoveryId]['description'] === ''
                  ? 'sm:max-w-xl'
                  : 'sm:max-w-7xl'
              "
            >
              <div>
                <div class="mt-3 sm:mt-5">
                  <DialogTitle
                    as="h3"
                    class="text-xl sm:text-2xl font-bold text-white text-center leading-tight sm:px-16"
                  >
                    {{ discoveries[discoveryId]["title"] }}
                  </DialogTitle>
                  <div
                    :class="
                      discoveries[discoveryId]['image'] &&
                      'flex items-center flex-col-reverse lg:flex-row'
                    "
                  >
                    <div class="my-6">
                      <p
                        class="text-gray-200 whitespace-pre-wrap"
                        :class="
                          discoveries[discoveryId]['image'] === '' &&
                          'text-center'
                        "
                      >
                        {{ discoveries[discoveryId]["description"] }}
                      </p>
                      <a
                        v-if="discoveries[discoveryId]['href']"
                        :href="discoveries[discoveryId]['href']"
                        target="_blank"
                        rel="noopener"
                        class="flex items-center transition text-space-cyan hover:underline hover:text-space-cyan-lighter mt-5 outline-none"
                      >
                        More info in the article
                        <span class="sr-only">
                          about {{ discoveries[discoveryId]["title"] }}
                        </span>
                        <IconArrowTopRightOnSquare
                          class="w-5 h-5 stroke-2 ml-1"
                        />
                      </a>
                    </div>
                    <div
                      v-if="discoveries[discoveryId]['image']"
                      class="shrink-0 ml-2"
                    >
                      <img
                        class=""
                        :src="
                          useAsset(
                            'starmap/' + discoveries[discoveryId]['image']
                          )
                        "
                        :alt="discoveries[discoveryId]['title']"
                        width="580"
                        height="480"
                      />
                    </div>
                  </div>
                </div>
              </div>

              <button
                type="button"
                class="text-gray-500 transition cursor-pointer p-3 hover:bg-space-gray hover:text-gray-400 rounded-full outline-none absolute right-0 top-0 sm:right-3 sm:top-3"
                @click="open = false"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1"
                  stroke="currentColor"
                  class="w-8 h-8 sm:w-12 sm:h-12"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M6 18L18 6M6 6l12 12"
                  />
                </svg>
              </button>
            </DialogPanel>
          </TransitionChild>
        </div>
      </div>
    </Dialog>
  </TransitionRoot>

  <div
    class="relative z-10 bg-cover"
    :style="`background-image: url(${useAsset(
      'starmap/nebula.png'
    )}); background-position:center top; background-repeat:no-repeat;`"
  >
    <div class="md:absolute w-full">
      <div
        class="max-w-screen-2xl mx-auto px-4 sm:px-6 space-y-24 sm:space-y-0"
      >
        <div class="sm:flex items-center min-h-[600px] lg:min-h-[800px]">
          <div
            class="whitespace-nowrap text-center text-7xl sm:text-10xl lg:text-11xl xl:text-14xl mb-4 sm:mb-0 leading-none"
          >
            <span class="font-black tracking-tight sm:block mr-1 sm:mr-0">
              Q1
            </span>
            <span
              class="font-jp kanji leading-tight tracking-wide sm:[writing-mode:vertical-lr]"
            >
              創世
            </span>
          </div>
          <div class="md:max-w-[400px] xl:max-w-[540px] sm:ml-10 relative z-10">
            <h2 class="title mb-4">
              <span class="text-3xl lg:text-4xl">The Reborn Nebula</span>
            </h2>
            <div class="xl:text-lg">
              <p class="mb-8">
                Our journey begins in the Reborn Nebula where we aim to make the
                first discoveries of the year. Each one will upgrade our network
                with innovative features, pushing us further to our goal of
                becoming a powerful layer 1. Follow along and join us in
                celebrating each discovery throughout the year.
              </p>
              <h3 class="font-bold text-xl">Q1</h3>
              <p>
                In this quarter we can look forward to discoveries that relate
                to the following:
              </p>
              <ul class="list-disc pl-4">
                <li>
                  <span @click="clickAction('xvm')" class="popup-link">
                    Cross-Virtual Machine (XVM): The Portal to the Future
                  </span>
                </li>
                <li>
                  Astar UI Library &
                  <span @click="clickAction('astarjs')" class="popup-link">
                    Astar.js
                  </span>
                </li>
                <li>WASM tooling and showcase dapps</li>
                <li>XCM smart contracts</li>
                <li>dApp staking</li>
              </ul>
            </div>
          </div>
        </div>

        <div
          class="sm:flex items-center justify-end min-h-[600px] lg:min-h-[800px]"
        >
          <div
            class="whitespace-nowrap text-center order-2 text-7xl sm:text-10xl lg:text-11xl xl:text-14xl mb-4 sm:mb-0 leading-none"
          >
            <span class="font-black tracking-tight sm:block mr-1 sm:mr-0">
              Q2
            </span>
            <span
              class="font-jp kanji leading-tight tracking-wide sm:[writing-mode:vertical-lr]"
              >発展</span
            >
          </div>
          <div class="md:max-w-[400px] xl:max-w-[540px] order-1">
            <h2 class="title mb-4">
              <span class="text-3xl lg:text-4xl">The Growth Nebula</span>
            </h2>
            <div class="xl:text-lg">
              <p class="mb-8">
                We continue to grow at a steady pace while bringing true
                innovation to our users and builders alike. In this quarter we
                focus on growing out some some of our key features as well as
                introducing new ones.
              </p>
              <h3 class="font-bold text-xl">Q2</h3>
              <p>
                We can look forward to discoveries that relate to the following:
              </p>
              <ul class="list-disc pl-4">
                <li>Swanky Suite and projects</li>
                <li>Token economics</li>
                <li>Decentralized tooling</li>
              </ul>
            </div>
          </div>
        </div>

        <div class="sm:flex items-center min-h-[600px] lg:min-h-[800px]">
          <div
            class="whitespace-nowrap text-center text-7xl sm:text-10xl lg:text-11xl xl:text-14xl mb-4 sm:mb-0 leading-none"
          >
            <span class="font-black tracking-tight sm:block mr-1 sm:mr-0">
              Q3
            </span>
            <span
              class="font-jp kanji leading-tight tracking-wide sm:[writing-mode:vertical-lr]"
            >
              拡大
            </span>
          </div>
          <div class="md:max-w-[400px] xl:max-w-[540px] sm:ml-10 relative z-10">
            <h2 class="title mb-4">
              <span class="text-3xl lg:text-4xl">The Expansion Nebula</span>
            </h2>
            <div class="xl:text-lg">
              <p class="mb-8">
                At Astar we plan to expand our reach even further. By creating
                high quality tools and projects, we can further attract top
                talent. We will focus on improving not only the user experience,
                but also the developer experience.
              </p>
              <h3 class="font-bold text-xl">Q3</h3>
              <p>
                We can look forward to discoveries that relate to the following:
              </p>
              <ul class="list-disc pl-4">
                <li>Astar SDK</li>
                <li>Decentralization of our infrastructure</li>
                <li>Developer tooling improvements</li>
                <li>Learning Hub for dApp developers</li>
              </ul>
            </div>
          </div>
        </div>

        <div
          class="sm:flex items-center justify-end min-h-[600px] lg:min-h-[800px]"
        >
          <div
            class="whitespace-nowrap text-center order-2 text-7xl sm:text-10xl lg:text-11xl xl:text-14xl mb-4 sm:mb-0 leading-none"
          >
            <span class="font-black tracking-tight sm:block mr-1 sm:mr-0">
              Q4
            </span>
            <span
              class="font-jp kanji leading-tight tracking-wide sm:[writing-mode:vertical-lr]"
            >
              煌閃
            </span>
          </div>
          <div class="md:max-w-[400px] xl:max-w-[540px] order-1">
            <h2 class="title mb-4">
              <span class="text-3xl lg:text-4xl">The Shine Nebula</span>
            </h2>
            <div class="xl:text-lg">
              <p class="mb-8">
                We now approach the last nebula in 2023. By now we have made
                many great discoveries and grown to new heights - as Web3
                technology, and as a team. But we are not done yet. We plan to
                shine like a star to close out the year and prepare for the 2024
                journey ahead.
              </p>
              <h3 class="font-bold text-xl">Q4</h3>
              <p>We’re excited for this quarter. Stay tuned for more info.</p>
              <!-- <ul class="list-disc pl-4">
                <li>Swanky Suite and projects</li>
                <li>Token economics</li>
                <li>Decentralized tooling</li>
              </ul> -->
            </div>
          </div>
        </div>
      </div>
    </div>

    <StarmapLine
      v-on:showDetails="clickAction"
      class="relative hidden md:block w-full h-auto max-w-[1280px] mx-auto"
    />
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
const open = ref(false);
const discoveryId = ref("xvm");

interface Discovery {
  title: string;
  description: string;
  href: string;
  image: string;
}

const discoveries: { [index: string]: Discovery } = {
  xvm: {
    title: "Cross-Virtual Machine (XVM): The Portal to the Future",
    description: `As we are well-aware, WASM is the future. Currently, WASM smart contracts have a large limitation when pushing the technology for mass adoption in the EVM-dominated space. Teams are inclined to choose one or the other when developing their project. This is why we created XVM.\n\nCross-Virtual Machine (XVM) is a custom pallet and a set of interfaces that allow a smart contract in one virtual machine to communicate with another, as if they are in the same environment. In other words, with XVM, you can create an ink! smart contract and access any assets or contracts available on the EVM side. You can enjoy the best of both worlds!`,
    href: "https://medium.com/astar-network/cross-virtual-machine-creating-a-portal-to-the-future-of-smart-contracts-a96c6d2f79b8",
    image: "xvm.svg",
  },
  astarjs: {
    title: "Astar.js",
    description:
      "Astar.js is an essential tool for anyone looking to build a dApp on the Astar network. Its modular design and comprehensive feature set make it easy for developers to create powerful and scalable decentralised applications. In addition to the many packages it contains, it also supports EVM and substrate native structures. Whether you're a seasoned blockchain developer or just starting out, Astar.js is a valuable tool to have in your toolkit.",
    href: "https://medium.com/astar-network/overview-23e6eaa321c2",
    image: "astarjs.svg",
  },
  comingSoon: {
    title: "Coming soon!",
    description: "",
    href: "",
    image: "",
  },
};

const clickAction = (discovery: string) => {
  discoveryId.value = discovery;
  open.value = true;
};
</script>

<style scoped lang="postcss">
.kanji {
  background: linear-gradient(
    180deg,
    #e6007a -5.88%,
    #703ac2 15.42%,
    #0070eb 40.77%,
    #0297fb 72.21%,
    #0ae2ff 95.53%
  );
  -webkit-background-clip: text;
  -webkit-text-stroke: 4px transparent;
  @apply text-space-gray-dark;
}
.popup-link {
  @apply text-space-cyan hover:underline cursor-pointer transition hover:text-space-cyan-lighter;
}
</style>
