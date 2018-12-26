<template>
  <div class="row">
      <div class="col-lg-12 text-center">
          <router-link to='/get-started'><button class="btn btn-primary">{{ title }}</button></router-link>
      </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      title: 'Get Started'
    }
  }
}
</script>
