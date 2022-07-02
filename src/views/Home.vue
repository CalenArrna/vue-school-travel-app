<template>

<div class="home">
    <h1>All Destinations</h1>
    <div class="destinations">
    <router-link 
    v-for="dest in destinations"
    :key="dest.id"
    :to="{name: 'destination.show', params:{id: dest.id, slug: dest.slug}}"
    >
        <h2>{{dest.name}}</h2>
        <img :src="`/images/${dest.image}`" :alt="dest.name">
    </router-link>
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