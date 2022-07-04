<template>
    <a class="external-link" target="_blank" rel="noopener" v-if="isExternal" :href="to">
        <slot />
    </a>
    <router-link class="internal-link" v-else v-bind="$props">
        <slot />
    </router-link>
</template>
<script>
import { RouterLink } from "vue-router";
export default {
    props: {
        ...RouterLink.props
    },
    computed: {
        isExternal() {
            return typeof this.to === "string" && this.to.startsWith('http')
        },

    }

}
</script>