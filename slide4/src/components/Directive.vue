<template>
    <h1>2-Tuấn Anh</h1>
    <div>
        <input type="test" name="" v-blind:value="content">
    </div>
</template>
<script>
export default {
    data() {
        return {
            content: 'Xin chao VueJS',
            className: 'text-red'
        }
    },
    methods: {
        sayHi() {
            return 'Đây là một phương thức'
        },
        sayHello() {
            return this.message = 'ABC'
        },
        change() {
            this.message = 'Đây là nội dung mới'
        },

    }
}
</script>
<style></style>