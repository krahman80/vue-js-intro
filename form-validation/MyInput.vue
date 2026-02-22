<template>
     <div class="label">
        <label :for="name">{{ name }}</label>
        <div class="error">{{ error }}</div>
     </div>
     <input 
       :id="name" 
       :value="value"
       @input="input"
       />
</template>

<script>
export default {
    props: {
        name: {
            type: String,
            required: true
        },
        value: {
            type: String,
            required: true
        },
        rules: {
            //min:number
            //required: true
            type: Object,
            default: {}
        }
    },
    methods: {
        input($event) {
            this.$emit('update', {
                name: this.name.toLowerCase(),
                value: $event.target.value,
            })
        }
    },
    computed: {
        error() {
            if (this.rules.required && this.value.length === 0) {
                return `Value is required.`
            }
            if (this.rules.min && this.value.length < this.rules.min) {
                return `The min length is ${this.rules.min}.`
            }
        }
    }
}
</script>

<style scoped>
.input-wrapper {
    display: flex;
    flex-direction: column;
}
.error {
    color: red;
}
.label {
    display: flex;
    justify-content: space-between;
}
input {
    background: none;
    color: black;
    border: 1px solid silver;
    border-radius: 5px;
    padding: 10px;
    margin: 5px 0;
    font-size: 16px;
}
</style>