<template>
  <div id="nav">
    <router-link id="logo" to="/">Vue School Travel App</router-link>

    <router-link 
      v-for="dest in destinations"
      :key="dest.id"
      :to="{name: 'destination.show', params:{id: dest.id, slug: dest.slug}}"
      >
        {{dest.name}}
    </router-link>
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