<template>
    <h1 class="title">Cadastro de talento</h1>
    <form @submit.prevent="handleSubmit" class="form-new">

        <label for="name">Nome completo</label>
        <input id="name" v-model="name" />
        {{ this.errors.name }}

        <label for="email">Email</label>
        <input id="email" v-model="email" />
        {{ this.errors.email }}

        <label for="date">Data de nascimento</label>
        <input type="date" id="name" v-model="date_birth" />

        <label for="phone">WhatsApp</label>
        <input id="phone" v-model="phone" />

        <label for="area">Área de interesse</label>
        <select v-model="area">
            <option value="frontend">Frontend</option>
            <option value="backend">Backend</option>
            <option value="fullstack">Fullstack</option>
        </select>
        {{ this.errors.area }}

        <label for="nivel">Nível</label>
        <select v-model="nivel">
            <option value="junior">Junior</option>
            <option value="pleno">Pleno</option>
            <option value="senior">Senior</option>
        </select>

        <p>Selecione suas habilidades</p>

        {{ skills.length }}

        <div v-if="area === 'frontend' || area === 'fullstack'">
            <label><input type="checkbox" v-model="skills" value="HTML" />HTML</label>
            <label><input type="checkbox" v-model="skills" value="CSS" />CSS</label>
            <label><input type="checkbox" v-model="skills" value="JAVASCRIPT" />JAVASCRIPT</label>
            <label><input type="checkbox" v-model="skills" value="VUE" />VUE</label>
        </div>

        <div v-if="area === 'backend' || area === 'fullstack'">
            <label><input type="checkbox" v-model="skills" value="NODE" />NODE</label>
            <label><input type="checkbox" v-model="skills" value="PHP" />PHP</label>
            <label><input type="checkbox" v-model="skills" value="LARAVEL" />LARAVEL</label>
            <label><input type="checkbox" v-model="skills" value="JAVA" />JAVA</label>
        </div>

        <label>Carta de apresentação</label>
        <textarea v-model="apresentation"></textarea>

        <button type="submit">Cadastrar</button>
    </form>
</template>

<script>

import * as yup from 'yup'
import { captureErrorYup } from '../../../utils/captureErroYup'
import axios from 'axios'


export default {
    data() {
        return {
            name: '',
            email: '',
            date_birth: '',
            phone: '',
            area: '',
            nivel: '',
            skills: [],
            apresentation: '',
            errors: {}
        }
    },
    methods: {
        handleSubmit() {
            try {
                const schema = yup.object().shape({
                    name: yup.string().required("O nome é obrigatório"),
                    email: yup.string().required("Email inválido").required("Email é obrigatório"),
                    area: yup.string().required("A área é obrigatória")

                })

                schema.validateSync({
                    name: this.name,
                    email: this.email,
                    area: this.area
                },
                    { abortErly: false })

                axios({
                    url: 'http://localhost:5173/api/talent',
                    method: 'POST',
                    data: {
                        name: this.name,
                        email: this.email,
                        date_birth: this.date_birth,
                        phone: this.phone,
                        area: this.area,
                        nivel: this.nivel,
                        skills: this.skills,
                        bio: this.apresentation
                    }
                })
                    .then(() => {
                        alert('Talento cadastrado com sucesso!')
                    })
                    .catch(() => {
                        alert('Erro ao cadastrar talento!')
                    })

            } catch (error) {
                if (error instanceof yup.ValidationError) {

                    this.errors = captureErrorYup(error)
                }
            }
        }
    },
    watch: {
        area(newValue, oldValue) {
            if (newValue !== oldValue) {
                this.skills = []
            }
        }
    }
}
</script>

<style scoped>
.form-new {
    display: flex;
    flex-direction: column;
    gap: 10px;
    max-width: 40%;
}
.title {
    font-family:Verdana, Geneva, Tahoma, sans-serif;
    font-size: 30px;
    font-weight: bold;
    color:black;
    text-align: center;
}
label,
p {
  margin: 0;
  padding: 0;
  line-height: 1.5rem;
  text-align: justify;
  color: #727272;
  font-weight: 500;
}
button {
  width: 18%;
  height: 38px;
  border-radius: 4px;
  border: none;
  outline: none;
  background-color: #e2a64c;
  color: #ffffff;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
}
button:hover {
  background-color: #e8c860;
}
textarea {
  height: 100px;
  resize: none;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  padding-top: 5px;
}


</style>
