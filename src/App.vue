<template>
  <div class="container"></div>
  <global-header :user="currentUser"> </global-header>
  <!-- <column-list :list="list"></column-list> -->
  <validate-form @form-submit="onFormSubmit">
    <div class="mb-3">
      <label class="form-label">邮箱地址</label>
      <validate-input :rules="emailRules" v-model="emailVal" placeholder="请输入邮箱" type="text" ref="inputRef"></validate-input>
      {{emailVal}}
    </div>

    <div class="mb-3">
      <label for="exampleInputEmail1" class="form-label">邮箱地址</label>
      <input type="email" class="form-control" id="exampleInputEmail1" v-model="emailRef.val" @blur="validateEmail">
      <dir class="form-text" v-if="emailRef.error">{{emailRef.message}}</dir>
    </div>
    <div class="mb-3">
      <label class="form-label">密码</label>
      <validate-input type="password" placeholder="请输入密码" :rules="passwordRules" v-model="passwordVal"></validate-input>
    </div>
    <template #submit>
      <span class="btn btn-danger">submit</span>
    </template>
  </validate-form>
</template>

<script lang="ts">
import { defineComponent, reactive, ref } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
// import ColumnList, { ColumnProps } from './components/ColumnList.vue'
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'
import ValidateInput, { RulesProp } from './components/ValidateInput.vue'
import ValidateForm from './components/ValidateForm.vue'
// const testData:ColumnProps[] = [
//   {
//     id: 1,
//     title: '技术',
//     avatar: 'https://avatars0.githubusercontent.com/u/8186664?s=460&v=4',
//     description: '技术是一种艺术，技术是一种生活'
//   },
//   {
//     id: 2,
//     title: '生活',
//     // avatar: 'https://avatars0.githubusercontent.com/u/8186664?s=460&v=4',
//     description: '生活是一种艺术，生活是一种生活'
//   },
//   {
//     id: 3,
//     title: '旅行',
//     avatar: 'https://avatars0.githubusercontent.com/u/8186664?s=460&v=4',
//     description: '旅行是一种艺术，旅行是一种生活'
//   }
// ]
const emailReg = /^[a-zA-Z0-9.!#$%&’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/
export default defineComponent({
  name: 'App',
  components: {
    // ColumnList,
    GlobalHeader,
    ValidateInput,
    ValidateForm
  },
  inheritAttrs: false,
  setup () {
    const inputRef = ref<any>()
    const emailVal = ref('123@test.com')
    const emailRules:RulesProp = [
      { type: 'required', message: '邮箱不能为空' },
      { type: 'email', message: '邮箱格式不正确' }
    ]
    const emailRef = reactive({
      val: '',
      error: false,
      message: ''
    })
    const validateEmail = () => {
      if (emailRef.val.trim() === '') {
        emailRef.error = true
        emailRef.message = '邮箱不能为空'
      } else if (!emailReg.test(emailRef.val)) {
        emailRef.error = true
        emailRef.message = '邮箱格式不正确'
      }
    }
    const currentUser:UserProps = {
      isLogin: true,
      name: '者也'
    }
    const onFormSubmit = (result:boolean) => {
      console.log('result', result)
    }
    return {
      // list: testData,
      currentUser,
      GlobalHeader,
      emailRef,
      validateEmail,
      emailRules,
      emailVal,
      onFormSubmit,
      inputRef
    }
  }
})
</script>

<style>

</style>
