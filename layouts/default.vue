<script setup lang="ts">
import type { before } from 'node:test'
import { MY_INFO } from '~/constants'

const { t } = useI18n()
const top = [
  t('me.title', '', { locale: 'en' }),
  t('me.company_of_employment', '', { locale: 'en' }),
  t(
    'about.based_in',
    { location: t('me.location', '', { locale: 'en' }) },
    { locale: 'en' },
  ),
]
</script>
<template>
  <div class="relative mx-auto h-screen max-w-lg bg-slate-950">
    <div class="_bg absolute h-full w-full" />
    <main
      :class="[
        '_container g:no-scrollbar relative z-10 mx-auto h-screen min-h-screen snap-y snap-mandatory space-y-10 overflow-hidden overflow-y-auto p-10 text-white backdrop-blur-sm',
      ]"
    >
      <div class="relative z-10 space-y-10">
        <h1
          class="relative -z-10 -mx-10 space-y-3 bg-seagull-900 py-4 text-center text-5xl"
        >
          <p>Web Developer</p>
          <p>[ {{ MY_INFO.name }} ]</p>
        </h1>
        <Avator class="mx-auto" />
        <section class="p-6">
          <ul class="space-y-1 text-base">
            <li v-for="i in top" class="flex">
              <IconWrapped name="loader-5-line" class="rotate-180" />
              <span class="whitespace-nowrap">{{ i }}</span>
            </li>
          </ul>
          <ContactNavs class="mt-4 flex justify-between" />
        </section>
      </div>

      <section class="flex items-center">
        <Markdown article="about" />
      </section>

      <section class="overflow-auto">
        <Markdown article="tech" />
        <!-- <TechList /> -->
      </section>

      <section>
        <Markdown article="howcanihelp" />
      </section>

      <!-- spotify block -->
      <!-- side projects -->
      <!-- what next -->
      <!-- <TodolistBlock /> -->

      <!-- <LifeProgressing class="h-screen" /> -->
    </main>
    <div
      class="absolute bottom-1 left-1 z-40 flex h-10 w-10 items-center justify-center rounded-full bg-white/50 text-3xl"
    >
      <LangSwitch />
    </div>
  </div>
</template>
<style>
._bg {
  background-image: url('~/assets/bg.png');
  background-position-y: center;
  background-position-x: 46.4%;
}
._container section {
  @apply rounded-lg bg-seagull-900/50 outline outline-2 outline-seagull-200 backdrop-blur-xl;
}
._container > div,
._container > section {
  @apply max-h-full snap-center;
}
._container > section {
  @apply overflow-auto no-scrollbar;
}

/* https://cssarrowplease.com/ */
.arrow_box {
  @apply absolute right-full -translate-x-3 p-1 text-xs;
  background: #4b5563;
  border: 2px solid #f3f4f6;
}
.arrow_box:after,
.arrow_box:before {
  left: 100%;
  top: 50%;
  border: solid transparent;
  content: '';
  height: 0;
  width: 0;
  position: absolute;
  pointer-events: none;
}

.arrow_box:after {
  border-color: rgba(75, 85, 99, 0);
  border-left-color: #4b5563;
  border-width: 6px;
  margin-top: -6px;
}
.arrow_box:before {
  border-color: rgba(243, 244, 246, 0);
  border-left-color: #f3f4f6;
  border-width: 9px;
  margin-top: -9px;
}
</style>
