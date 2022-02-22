<template>
  <div>
    <p v-for="user in state.users" :key="user.id">
      {{user.first_name}}
    </p> 
  </div>
</template>

<script>
import { reactive } from 'vue'

  export default {
    async setup() {
      const state = reactive({
      error: null,
      users: null
    })
 
   // const load = async() => {
      try {
        const usersResponse = await fetch("https://reqres.in/api/users?delay=1")
        //state.users = await usersResponse.json() // this will create another array "data" test it
        
        await usersResponse.json().then(userData => {
          state.users = userData.data
        })
      }
      catch (err){
        state.error = err.message
        console.log(state.error)
      }
  //  }
  // await load();
  // Could also use a lifecycle hook to initiate it. fx onMounted, etc.
 
    return { /* load, */ state }
    }
  }

</script>

<style lang="scss" scoped>

</style>