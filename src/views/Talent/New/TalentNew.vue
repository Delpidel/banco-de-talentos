<template>
 <div class="form-new">
    <h1>Cadastro de talento</h1>

    <label for="name">Nome completo</label>
    <input id="name" v-model="name" />

    <label for="email">Email</label>
    <input id="email" v-model="email" />

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

    <label for="phone">Nível</label>
    <select v-model="nivel">
        <option value="junior">Junior</option>
        <option value="pleno">Pleno</option>
        <option value="senior">Senior</option>
    </select>

    <p>Selecione suas habilidades</p>
    <div v-if="area === 'frontend'">
        <label><input type="checkbox" />HTML</label>
        <label><input type="checkbox" />CSS</label>
        <label><input type="checkbox" />JAVASCRIPT</label>
        <label><input type="checkbox" />VUE</label>
    </div>

    <div v-if="area === 'backend'">
        <label><input type="checkbox" />NODE</label>
        <label><input type="checkbox" />PHP</label>
        <label><input type="checkbox" />LARAVEL</label>
        <label><input type="checkbox" />JAVA</label>
    </div>

    <div v-if="area === 'fullstack'">
        <label><input type="checkbox" />HTML</label>
        <label><input type="checkbox" />CSS</label>
        <label><input type="checkbox" />JAVASCRIPT</label>
        <label><input type="checkbox" />VUE</label>
        <label><input type="checkbox" />NODE</label>
        <label><input type="checkbox" />PHP</label>
        <label><input type="checkbox" />LARAVEL</label>
        <label><input type="checkbox" />JAVA</label>
    </div>
 </div>
</template>

<script>
    export default {
        data(){
            return {
                name: '',
                email: '',
                date_birth:'',
                phone: '',
                area: '',
                nivel: ''
            }
        }
    }

</script>

<style scoped>
.form-new {
    display: flex;
    flex-direction: column;
}
</style>