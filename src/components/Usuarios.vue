<template>
    <div>
        <h2>Agregar Usuarios</h2>
        <form @submit.prevent="agregarUsuario">
            <input v-model="nuevoUsuario" placeholder="Nombre de usuario">
            <button>Añadir Usuario</button>
        </form>

        <h2>Lista de Usuarios</h2>
        <button @click="toggleLista">{{ mostrarLista ? 'Ocultar' : 'Mostrar' }} Lista</button>

        <ul v-if="mostrarLista">
            <li v-for="(usuario, index) in usuarios" :key="index">{{ usuario }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    data() {
        return {
            nuevoUsuario: '',
            usuarios: ['Usuario 1', 'Usuario 2', 'Usuario 3'],
            mostrarLista: false
        };
    },
    methods: {
        agregarUsuario() {
            if (this.nuevoUsuario.trim() !== '') {
                this.usuarios.push(this.nuevoUsuario);
                this.nuevoUsuario = ''; // Limpiamos el campo de entrada
            }
        },
        toggleLista() {
            this.mostrarLista = !this.mostrarLista;
        }
    }
};
</script>
