<script setup>
import { RouterLink, RouterView } from 'vue-router'
import gql from 'graphql-tag'
import { useQuery } from '@vue/apollo-composable'
import { watchEffect } from "vue";

const { result } = useQuery(
  gql`
      query getPosts{
        posts{
          data{
            title
            description
          }
        }
      }
  `)

watchEffect(()=>{
  console.log(result.value)
})  

</script>

<template>
<header>
  <div class="wrapper">

    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </nav>
  </div>
</header>

<RouterView />
</template>

<style scoped></style>
