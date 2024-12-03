<!-- eslint-disable vue/multi-word-component-names -->
<script setup lang="ts">
import { useDevtoolsClient } from "@nuxt/devtools-kit/iframe-client";

const client = useDevtoolsClient();
</script>

<template>
  <div class="relative p-10 n-bg-base flex flex-col h-screen">
    <h1 class="text-3xl font-bold">Responsive Devtools</h1>
    <div class="opacity-50 mb-4">
      A devtools to know more about the responsiveness of your website:
      breakpoints, etc.
    </div>
    <div v-if="client" class="flex flex-col gap-2">
      <NTip n="green" icon="carbon-checkmark">
        Nuxt DevTools is connected
      </NTip>
      <div>
        The current app is using
        <code class="text-green"
          >vue@{{ client.host.nuxt.vueApp.version }}</code
        >
      </div>
      <div>
        <BreakpointStatus />
      </div>
    </div>
    <div v-else>
      <NTip n="yellow">
        Failed to connect to the client. Did you open this page inside Nuxt
        DevTools?
      </NTip>
    </div>

    <div class="flex-auto" />
    <ModuleAuthorNote class="mt-5" />
  </div>
</template>
