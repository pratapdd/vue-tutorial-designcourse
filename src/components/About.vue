<template>
  <div class="about">
    <h1>Hellow {{ their_name }} This is an About Page.</h1>
    <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Nam blanditiis, earum autem similique delectus molestiae vel rem perspiciatis pariatur harum praesentium nisi consectetur eligendi, commodi quas eos corrupti id. Rem.</p>
  </div>
</template>

<script>
export default {
  name: 'About',
  data() {
    return {
      their_name: this.$route.params.name
    }
  }
}
</script>