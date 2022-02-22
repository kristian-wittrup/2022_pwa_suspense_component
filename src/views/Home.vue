<template>
  <div class="home">
     <img alt="Vue logo" src="../assets/logo.png">
    <Suspense>
      <template #default>
        <users />
      </template>
      <template #fallback>
        <p>Loading data...</p>
      </template>
    </Suspense>
   
   
   </div>

</template>

<script>
// @ is an alias to /src
//import { reactive } from 'vue'
import users from '@/components/users.vue'

export default {
  name: 'Home',
  components: {
    users
  }
}
</script>
