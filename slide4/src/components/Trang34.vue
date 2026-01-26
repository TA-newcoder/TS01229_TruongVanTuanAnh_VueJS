<template>
    <div>
        <h1>Hiển thị nội dung ở đây</h1>
        <h2>{{ message }}</h2>
        <h2 v-html="number"> </h2>
        <!-- <h2>{{ number + 5 }}</h2> -->
        <h2>{{ sayHi() }}</h2>
        <p>Phương thức sayHi trả về: {{ sayHi() }}</p>
        <p>Số này là số {{ number % 2 == 0 ? 'chẵn' : 'lẻ' }}</p>

        <button @click="change()">Change</button>
    </div>
</template>
<script>
export default {
    data() {
        return {
            message: 'Xin chao VueJS',
            number: 2
        }
    },
    methods: {
        sayHi() {
            return 'Đây là một phương thức'
        },
        sayHello() {
            return this.message = 'ABC'
        },
        changeContent() {
            this.message = 'Đây là nội dung mới'
        },
        change() {
            this.message = 'Đây là nội dung mới'
        },
        sayHii: function () {
            return 'vuejs.org'
        }
    }
}
</script>
<style></style>