<template>
  <div>
    <FForm :model="model" :rules="rules" ref="loginFormRef">
        <FFormItem label="用户名" prop="username">
            <FInput v-model="model.username" placeholder="请输入用户名！"></FInput>
        </FFormItem>
        <FFormItem label="密码" prop="password">
            <FInput v-model="model.password" placeholder="请输入密码！"></FInput>
        <FFormItem>
        <FFormItem>
            <button @click="login">登录</button>
        </FFormItem>
    </FForm>
  </div>
</template>

<script>
import FForm from "@/components/form/FForm.vue";
import FFormItem from "@/components/form/FFormItem.vue";
import FInput from "@/components/form/FInput.vue"


export default {
    name: 'formIndex',
    components: {
        FForm,
        FFormItem,
        FInput
    },
    data() {
        return {
            model: {
                username: "",
                password: ""
            },
            rules: {
                username: [{required: true, message: "请输入用户名！"}],
                password: [{required: true, message: "请输入密码！"}]
            }
        }
    },
    methods: {
        login() {
            this.$refs.loginFormRef.validate(isValid => {
                if(isValid) {
                    alert("校验成功！")
                } else {
                    alert("校验失败！")
                }
            })
        }
    }

}

</script>
<style>
</style>