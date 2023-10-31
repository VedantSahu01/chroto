<script setup>
import titleView from "~/views/title-view.vue";
var resultValues = useState("userPoints");
const wordNormal = ref(["R", "E", "S", "U", "L", "T"]);
const wordFinal = ref(["R", "E", "S", "U", "L", "T"]);
const finalPointsDividedBy10 = computed(() => {
    if (Array.isArray(resultValues.value)) {
        return resultValues.value.map((point) => Math.round(point / 10));
    } else {
        return [10, 10, 10, 10, 10];
    }
});

</script>

<template>
    <title-view :recievedWordNormal="wordNormal" :recievedWordFinal="wordFinal"></title-view>
    <div class="center-div">
        <div v-for="(resultValueLoop, index) in finalPointsDividedBy10">
            <span class="green-block" v-for="value in resultValueLoop"> </span>
        </div>
        <div class="button-container">
            <nuxt-link to="/" class="custom-link-button">Go Home</nuxt-link>
        </div>
    </div>
</template>

<style>
.button-container {
    margin-top: 20px; /* Adjust the margin-top as needed */
}
.center-div{
    text-align: center;
}
.green-block {
    width: 4%; /* Adjust the width as needed */
    padding-bottom: 4%; /* Adjust the height as needed */
    background-color: royalblue;
    display: inline-block; /* Add some margin between blocks */
    border-radius: 10%;
    margin: 0.5%;
}

.custom-link-button {
    margin: 0 auto; /* Center the button horizontally */
    padding: 1%;
    border-radius: 7%;
    border: 4px solid black;
    font-family: Orbitron;
    font-weight: 800;
    font-size: large;
    text-align: center;
    /* Remove other unnecessary styles for centering */
    text-decoration: none;
    cursor: pointer;
    color: black;
    background-color: white;
    transition: background-color 0.3s ease;
}
</style>