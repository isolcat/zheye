<template>
  <div class="container"></div>
  <global-header :user="currentUser"> </global-header>
  <column-list :list="list"></column-list>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import ColumnList, { ColumnProps } from './components/ColumnList.vue'
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'

const testData:ColumnProps[] = [
  {
    id: 1,
    title: '技术',
    avatar: 'https://avatars0.githubusercontent.com/u/8186664?s=460&v=4',
    description: '技术是一种艺术，技术是一种生活'
  },
  {
    id: 2,
    title: '生活',
    // avatar: 'https://avatars0.githubusercontent.com/u/8186664?s=460&v=4',
    description: '生活是一种艺术，生活是一种生活'
  },
  {
    id: 3,
    title: '旅行',
    avatar: 'https://avatars0.githubusercontent.com/u/8186664?s=460&v=4',
    description: '旅行是一种艺术，旅行是一种生活'
  }
]
export default defineComponent({
  name: 'App',
  components: {
    ColumnList,
    GlobalHeader
  },
  setup () {
    const currentUser:UserProps = {
      isLogin: true,
      name: '者也'
    }
    return {
      list: testData,
      currentUser,
      GlobalHeader
    }
  }
})
</script>

<style>

</style>
