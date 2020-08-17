<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
export default {
    provide() {
        return {
            form: this // 传递当前表单组件实例
        }
    },
    props: {
        model: {
            type: Object,
            required: true
        },
        rules: Object
    },
    methods: {
        validate(cb) {
            // 全局校验方法 执行内部所有FormItem校验方法，统一处理结果
            const tasks = this.$children.filter(item => item.prop).map(item => item.validate())
            // 将FormItem数组转换为Promise数组 统一检查校验结果
            Promise.all(tasks).then(() => cb(true)).catch(() => cb(false))
        }
    }
}

</script>
<style>
</style>