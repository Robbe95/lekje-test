<script setup lang="ts">
import { useDark } from '@vueuse/core'
import CookiesConsent from './components/cookies/CookiesConsent.vue'
import { hasChoosenCookies, hasCookiesOpened } from './composables/cookies/useCookiesConsent'
import { scaleBounceTransition } from './transitions'

const isDark = useDark()

const isAppearanceTransition = computed(() => {
  // @ts-expect-error: Transition API
  return document.startViewTransition
})

function toggle(event: MouseEvent): void {
  if (!isAppearanceTransition.value) {
    setClass(!isDark.value)
    return
  }
  const x = event.clientX
  const y = event.clientY
  const endRadius = Math.hypot(
    Math.max(x, innerWidth - x),
    Math.max(y, innerHeight - y),
  )
  // @ts-expect-error: Transition API
  const transition = document.startViewTransition(() => {
    setClass(!isDark.value)
  })
  transition.ready.then(() => {
    const clipPath = [
        `circle(0px at ${x}px ${y}px)`,
        `circle(${endRadius}px at ${x}px ${y}px)`,
    ]
    document.documentElement.animate(
      {
        clipPath: isDark ? clipPath : [...clipPath].reverse(),
      },
      {
        duration: 500,
        easing: 'ease',
        pseudoElement: isDark ? '::view-transition-new(root)' : '::view-transition-old(root)',
      },
    )
  })
}

function setClass(dark: boolean): void {
  const css = document.createElement('style')
  css.type = 'text/css'
  css.appendChild(
    document.createTextNode(
        `:not(.VPSwitchAppearance):not(.VPSwitchAppearance *) {
        -webkit-transition: none !important;
        -moz-transition: none !important;
        -o-transition: none !important;
        -ms-transition: none !important;
        transition: none !important;
      }`,
    ),
  )
  document.head.appendChild(css)
  const classList = document.documentElement.classList
  classList[dark ? 'add' : 'remove']('dark')
  const _ = window.getComputedStyle(css).opacity
  document.head.removeChild(css)
  isDark.value = dark
}
</script>

<template>
  <div class="bg-background">
    <AppButton @component:click="toggle">
      close cookies
    </AppButton>
    <RouterView />
    <Transition v-bind="scaleBounceTransition">
      <CookiesConsent v-if="!hasChoosenCookies || hasCookiesOpened" />
    </Transition>
  <!-- <FormSelect v-model="selectedMultiple" :display-function="(value: Option) => value" has-multiple key-value="value"> -->
  </div>
</template>

<style></style>
