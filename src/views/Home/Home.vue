<template>
    <nav>
        <ul class="menu">
        <router-link to="/">
            <li class="item-menu">
                <img width="50" height="50" src="https://img.icons8.com/ios/50/home--v1.png" alt="home--v1"/>
                <h2>Home</h2>
            </li>
        </router-link>
        
        <router-link to="/talentos/novo">
            <li class="item-menu">
                <img width="50" height="50" src="https://img.icons8.com/ios/50/home--v1.png" alt="home--v1"/>
                <h2>Cadastro</h2>
            </li>
        </router-link>
        <router-link to="/sobre">
            <li class="item-menu">
                <img width="50" height="50" src="https://img.icons8.com/ios/50/home--v1.png" alt="home--v1"/>
                <h2>Sobre</h2>
            </li>
        </router-link>
        </ul>
    </nav>

    <h1 class="title">Banco de Talentos</h1>
</template>

<style scoped>
.title {
    font-family:Verdana, Geneva, Tahoma, sans-serif;
    font-size: 30px;
    font-weight: bold;
    color:rgb(114, 214, 214);
    text-align: center;
}
.menu {
    display: flex;
    justify-content: space-between;
    list-style: none;
}
.item-menu {
    display: flex;
    border: 1px solid black;
    border-radius: 6px;
    padding: 5px;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    width: 33%;
}
</style>
