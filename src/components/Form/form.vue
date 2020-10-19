<template>
    <form @submit.prevent="submitForm">
        <div class="form-group" :key="key" v-for="(form, key) of formData">
            <label :for="key">{{formData[key].label}}</label>
            <input 
                class="form-control" 
                :id="key" 
                :name="key" 
                :type="key" 
                v-model.trim="formData[key].value" 
                @blur="checkValidity" 
                :placeholder="formData[key].placeholder" />
            <ErrorMessage v-if="formData[key].validity === false">{{formData[key].msgError}}</ErrorMessage>
        </div>
        <div class="form-group">
            <a href="https://admin.wobiz.com.ar/recovery">¿Olvidaste tu contraseña?</a>
        </div>
        <div class="form-group">
            <button class="btn btn-action-2 btn-lg btn-block mt-3 btn-validate btn-primary">Ingresar a mi cuenta</button>
        </div>
    </form>
</template>

<script>
import ErrorMessage from '../UI/errorMessage'
export default {
    components: {
        ErrorMessage
    },
    data() {
        return {
            formData: {
                email: {
                    value: '',
                    validity: null,
                    msgError: '',
                    rules: ['required', 'email'],
                    label: 'Email',
                    placeholder: 'ej: usuario@mail.com'
                },
                password: {
                    value: '',
                    validity: null,
                    msgError: '',
                    rules: ['required', 'min:5'],
                    label: 'Contraseña',
                    placeholder: 'Escribe tu contraseña'
                }
            }
        }
    },
    methods: {
        checkValidity(e) {
            let input = e.target.id
            let value = e.target.value
            let isValid = true
            let errorMessage = ''
            let rules = this.formData[input].rules
            for (let rule of rules) {
                if(rule == 'required'){
                    isValid = value.trim() !== '' && isValid
                    if(!isValid) {
                        errorMessage = `Necesitamos tu ${input}`
                        break;
                    }
                }
                if(rule == 'email') {
                    const regExpMail = /\S+@\S+\.\S+/
                    isValid = regExpMail.test(value.toLowerCase()) && isValid
                    if(!isValid) {
                        errorMessage = `El email ingresado no es correcto`
                        break;
                    }
                }
                if(rule.includes('min')) {
                    let lengthRequired = rule.slice(rule.indexOf(':') + 1);
                    isValid = value.trim().length > lengthRequired && isValid
                    if(!isValid) {
                        errorMessage = `La contraseña no tiene un formato válido. Minimo de ${+lengthRequired + 1} caracteres`
                        break;
                    }
                }
            }
            this.formData[input].msgError = errorMessage;
            this.formData[input].validity = isValid
        },
        submitForm() {
            this.$emit('onFormSubmitted', this.formData)
        }
    }
}
</script>

<style scoped>
    form > div {
        display: flex;
        flex-direction: column;
    }
    label {
        font-size: 13px;
        font-weight: 500;
    }
    input {
        height: 50px;
    }
    a {
        color: #969696;
        font-size: 14px;
        text-decoration: underline;
    }
    a:hover {
        color: #363636;
    }
    button {
        font-size: 13px;
        font-weight: 700;
        height: 45px;
    }

</style>