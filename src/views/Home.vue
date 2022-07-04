<template>

    <div class="home">
        <h1>All Destinations</h1>
        <button @click="triggerRouterError">Trigger Router Error</button>
        <button @click="addDynamicRoute">Add Dynamic Route</button>
        <router-link to="/dynamic">Visit Dynamic route</router-link>
        <div class="destinations">
            <AppLink v-for="dest in destinations" :key="dest.id"
                :to="{ name: 'destination.show', params: { id: dest.id, slug: dest.slug } }">
                <h2>{{ dest.name }}</h2>
                <img :src="`/images/${dest.image}`" :alt="dest.name">
            </AppLink>
        </div>

    </div>

</template>

<script>
import dataSource from '@/data.json';
import { isNavigationFailure, NavigationFailureType } from 'vue-router';

export default {
    data() {
        return {
            destinations: dataSource.destinations
        }
    },
    methods: {
        async triggerRouterError() {
            const navigationFailure = await this.$router.push('/');
            if (isNavigationFailure(navigationFailure, NavigationFailureType.duplicated)) {
                console.log(navigationFailure.to)
                console.log(navigationFailure.from)
            } else {

            }
        },
        addDynamicRoute() {
            this.$router.addRoute({
                name: "dynamic",
                path: '/dynamic',
                component: () => import("@/views/Login.vue")
            })
        }
    },
}
</script>