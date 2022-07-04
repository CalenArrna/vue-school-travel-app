<template>

    <div class="home">
        <h1>All Destinations</h1>
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
export default {
    data() {
        return {
            destinations: dataSource.destinations
        }
    }
}
</script>