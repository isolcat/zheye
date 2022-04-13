<template>
 <nav class="navbar navbar-dark bg-primary justify-content-between mb-4">
     <a class="navbar-brand" href="#">者也专栏</a>
     <ul v-if="!user.isLogin" class="list-inline mb-0">
         <li class="list-inline-item"><a href="#" class="btn btn-outline-light my-2">登录</a></li>
         <li class="list-inline-item"><a href="#" class="btn btn-outline-light my-2">注册</a></li>
     </ul>
     <ul v-else class="list-inline mb-0">
         <li class="list-inline-item"><a href="#" class="btn btn-outline-light my-2">你好 {{user.name}}</a></li>
     </ul>
</nav>
</template>

<script lang="ts">
import { UserProps } from '@/user'
import { defineComponent } from '@vue/runtime-core'
import { PropType } from 'vue'

export default defineComponent({
  name: 'GlobalHeader',
  props: {
    user: {
      type: Object as PropType<UserProps>,
      required: true
    }
  }
})
</script>

<style>

</style>
