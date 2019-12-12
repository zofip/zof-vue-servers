<template>
  <div>
    <img alt="Vue logo" src="../assets/logo.png">
    <Domains />
  </div>
</template>

<script>
// @ is an alias to /src
import Domains from '@/components/Domains.vue'

export default {
  name: 'home',
  components: {
    Domains
  }
}
</script>
