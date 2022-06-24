<template>
    <div>
        <form @submit.prevent="createContact">
            <input type="text" placeholder="Prénom" v-model="contact.firstName"><br>
            <input type="text" placeholder="Nom" v-model="contact.lastName"><br>
            <input type="text" placeholder="Email" v-model="contact.mail"><br>
            <input type="text" placeholder="Téléphone" v-model="contact.phone"><br>
            <button type="submit">Créer</button>
        </form>
    </div>
</template>

<script>
    import db from '../shared/db';
    export default {
        data() {
            return {
                contact: {
                firstName: "",
                lastName: "",
                email: "",
                phone: ""
                }
            };
        },
        methods: {
           createContact() {
            db.create(this.contact)
            .then((data) => {
                console.log(data);
            })
            .catch((error) => {
                console.error(error);
            });
           } 
        },
    };
</script>

<style scoped>
</style>