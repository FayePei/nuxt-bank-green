<template>
    <div class="page">
        <div class="bg-gradient-to-b from-sushi-50 to-sushi-100 md:pt-20">
            <div class="page-fade-in contain flex flex-col justify-center items-center">
                <a id="top"></a>
                <div class="max-w-4xl pt-28 lg:pt-12">
                    <h2 class="text-center text-2xl font-semibold text-gray-800 sm:text-5xl">
                        Is your money being used to fund climate chaos?
                    </h2>


                    <div
                        class="flex flex-col md:flex-row items-stretch md:items-center space-y-2 md:space-y-0 md:space-x-4 mt-8 md:mt-10 md:mb-10">
                        <ClientOnly>
                            <LocationSearch class="md:w-1/2 flex-initial" v-model="country" />
                            <BankSearch class="md:w-1/2 flex-initial" ref="bankSearch" :disabled="!country"
                                :country="country" v-model="bank" />
                            <template #fallback>
                                <div class="relative md:w-1/2 flex-initial">
                                    <input disabled
                                        class="relative w-full appearance-none border border-gray-200 text-gray-500 placeholder-gray-300 bg-gray-100 rounded-2xl shadow-sm pl-12 pr-10 py-4 text-left cursor-wait focus:outline-none focus:ring-1 sm:text-sm truncate" />
                                    <LoadingJumper class="h-5 w-5 absolute inset-0 m-4 text-sushi-500" />
                                </div>
                                <div class="relative md:w-1/2 flex-initial">
                                    <input disabled
                                        class="relative w-full appearance-none border border-gray-200 text-gray-500 placeholder-gray-300 bg-gray-100 rounded-2xl shadow-sm pl-12 pr-10 py-4 text-left cursor-wait focus:outline-none focus:ring-1 sm:text-sm truncate" />
                                    <LoadingJumper class="h-5 w-5 absolute inset-0 m-4 text-sushi-500" />
                                </div>
                            </template>
                        </ClientOnly>
                        <NuxtLink :to="`/banks/${bank?.tag}`" class="flex-initial md:w-48 button-green"
                            :class="{ disabled: !bank }" @click="onCheckBankClick">Check My Bank</NuxtLink>
                    </div>


                    <div class="flex flex-col items-center md:flex-row w-full pt-10 md:pt-8 md:pb-16">
                        <h3 class="text-center text-2xl md:text-xl font-semibold whitespace-nowrap mb-6 md:mb-0 md:mr-2 lg:mr-12"
                            style="font-family: serif">
                            As featured in
                        </h3>
                        <div
                            class="flex flex-col space-y-6 md:space-y-0 md:flex-row justify-between items-center w-full filter-grayscale opacity-20">
                            <SliceZone :slices="home?.data.slices1 ?? []" :components="sliceComps" />
                            <!-- <img class="h-6 w-auto" src="/img/featured/forbes.png"
                                alt="Bank Green featured in Forbes" />
                            <img class="h-12 pb-2 w-auto" src="/img/featured/the-new-yorker.png"
                                alt="Bank Green featured in The New Yorker" />
                            <img class="h-10 w-auto" src="/img/featured/independent.png"
                                alt="Bank Green featured in Independent" />
                            <img class="h-12 w-auto" src="/img/featured/the-big-issue.png"
                                alt="Bank Green featured in The Big Issue" /> -->
                        </div>
                    </div>
                    <div class="hidden md:flex flex-col justify-center items-center">
                        <p class="text-center text-lg font-medium text-gray-700 mb-2">
                            In association with
                        </p>
                        <div class="flex flex-row justify-center items-center space-x-6">
                            <a href="https://www.banktrack.org/" rel="noopener" target="_blank">
                                <div class="bg-white rounded-xl p-5">
                                    <img class="w-36" src="/img/logos/banktrack.svg" />
                                </div>
                            </a>
                        </div>
                        <NuxtLink to="/partners" class="underline mt-2 text-sm">See our partners</NuxtLink>
                    </div>
                    <div class="mt-16">
                        <div class="mt-12 text-lg text-gray-700 text-center leading-4">
                            Why
                            <img class="inline-block h-5 px-0.5" src="/img/trim-hor-light.svg" alt="Bank.Green" />
                            ?
                        </div>
                        <ArrowDownBounce class="mx-auto mt-4 w-10" />
                    </div>
                </div>
            </div>
            <Swoosh />
        </div>
        <!-- <pre>
            {{ JSON.stringify(home, null, 2) }}
        </pre> -->
        <div class="flex flex-col md:flex-row items-center justify-center py-16 contain">
            <div class="md:w-1/2 max-w-sm">
                <PrismicRichText class="text-lg md:text-2xl tracking-wide mb-4" :field="home.data.description1" />
                <PrismicRichText class="md:text-xl tracking-wide whitespace-pre-line text-gray-600 mb-12 md:mb-0"
                    :field="home.data.description2" />
            </div>

            <LazyLottiePlayer :placeholderHeight="480" :placeholderWidth="426" class="md:w-2/5 max-w-full md:ml-24"
                path="/anim/atm_without_bg.json" alt="" />

        </div>
        <div class="bg-blue-100 text-gray-800">
            <div class="overflow-hidden">
                <Swoosh direction="down" />
                <div class="contain">
                    <div class="flex flex-col md:flex-row items-center justify-center pt-8 pb-4 md:pb-16">
                        <div class="md:w-1/2 max-w-sm">
                            <PrismicRichText class="text-lg md:text-2xl tracking-wide mb-4"
                                :field="home.data.description3" />
                            <PrismicRichText
                                class="md:text-xl tracking-wide whitespace-pre-line text-gray-600 mb-12 md:mb-0"
                                :field="home.data.description4" />
                        </div>
                        <img class="md:order-first md:w-2/5 -mx-24 md:mx-0 md:mr-24" src="/img/illustrations/bank.svg"
                            alt="" width="450" height="450" />
                    </div>
                </div>
                <div id="join" class="contain max-w-5xl">
                    <CallToAction />
                </div>
            </div>
            <div class="flex flex-row items-center justify-center">

                <LazyLottiePlayer path="/anim/money_smoke.json"
                    class="w-full md:max-w-2xl h-42 object-cover object-bottom" />

            </div>
        </div>
    </div>
</template>

<script setup>
import LocationSearch from '@/components/forms/location/LocationSearch.vue'
import BankSearch from '@/components/forms/banks/BankSearch.vue'
import ArrowDownBounce from '@/components/icons/ArrowDownBounce.vue'
import { useGtm } from '@gtm-support/vue-gtm'
import { components } from '~~/slices'
import { defineSliceZoneComponents } from '@prismicio/vue';
import { usePrismicSEO } from '~~/composables/useHeadHelpers';
const sliceComps = ref(defineSliceZoneComponents(components))

const bank = ref(null)

const { client } = usePrismic()
const { data: home } = await useAsyncData('home', () => client.getSingle('homepage'))

usePrismicSEO(home.value.data)

const onCheckBankClick = () => {
    const allowCookies = useCookie('bg.allowcookies', { default: () => false })
    if (!allowCookies.value) return
    const gtm = useGtm()
    gtm.enable(true)
    gtm.trackEvent({ event: 'onBankCheckClick' })
}

const { country } = useCountry()

watch(country, loc => {
    bank.value = null
})
</script>
