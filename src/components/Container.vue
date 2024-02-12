<template>
  <div v-for="(a, i) in insta" :key="i">
    <Post :insta="insta" :i="i"/>
  </div>
</template>

<script>
import Post from './Post';

export default {
    components : {
        Post,
    },
    props : {
      insta : Array,
    }
}
</script>

<style>

</style>