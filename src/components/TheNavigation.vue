<template>
  <div id="nav">
    <AppLink id="logo" to="/">Vue School Travel App</AppLink>

    <AppLink v-for="dest in destinations" :key="dest.id"
      :to="{ name: 'destination.show', params: { id: dest.id, slug: dest.slug } }">
      {{ dest.name }}
    </AppLink>
    <AppLink :to="{ name: 'protected' }">Dashboard</AppLink>
    <AppLink to="https://vueschool.io">Vue School</AppLink>
  </div>
</template>

<script>
import dataSource from '@/data.json';
export default {
  data() {
    return {
      destinations: dataSource.destinations
    };
  },
}
</script>