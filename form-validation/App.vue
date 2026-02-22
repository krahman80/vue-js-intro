<template>
    <my-input 
        name="Username"
        :rules="{ required: true, min: 5}"
        :value="username.value"
        @update="update"
    />
    <my-input 
        name="Password"
        :rules="{ required: true, min: 10}"
        :value="password.value"
        @update="update"
    />
    <my-button 
        background="darkslateblue"
        color="white"
        :disabled="!valid"
    />    
</template>

<script>
import MyButton from './MyButton.vue'
import MyInput from './MyInput.vue'

export default {
    components: {
        MyButton,
        MyInput
    },
    data() {
        return {
            valid: true,
            username: {
                value:'user',
                valid: false
            },
            password: {
                value:'pass',
                valid: false
            }
        }
    },
    methods: {
        update({name, value}) {
            this[name].value = value
        }
    }
}
</script>

<style scoped>
</style>