<script setup lang="ts">
import { darkTheme } from 'naive-ui'
import { RouterView } from 'vue-router'

import { useI18n } from 'vue-i18n'
// import i18n from '@/i18n'
import { useSiteStore } from '@/store/site-state'

const i18n = useI18n()
const siteStore = useSiteStore()

i18n.locale.value = siteStore.i18nLanguage

siteStore.$subscribe((mutation, state) => {
    i18n.locale.value = state.i18nLanguage
    localStorage.setItem('i18nLanguage', state.i18nLanguage)
})

</script>

<template>
    <n-config-provider :theme="darkTheme">
        <n-notification-provider>
            <n-message-provider>
                <RouterView />
            </n-message-provider>
        </n-notification-provider>
    </n-config-provider>
</template>

<style scoped lang="scss">
</style>
