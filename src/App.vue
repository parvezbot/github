<template class="app">
    <h1>GitHub Search</h1>

    <input
        class="search-bar focus:ring-2 focus:ring-blue-600"
        type="text"
        placeholder="Enter GitHub Username"
        v-model="username"
        @keyup.enter="
            getGit();
            getRepo();
        "
        required
    />
    <button
        @click="
            getGit();
            getRepo();
        "
    >
        Search
    </button>
    <div v-if="github.id">
        <GitHub :github="github" />
    </div>

    <div v-if="gitrepos.length">
        <h1>Repos</h1>
        <div
            class="grid grid-rows-1
         "
        >
            <Repos v-for="repo in gitrepos" :key="repo.id" :repo="repo" />
        </div>
    </div>
</template>

<script>
import "./assets/tailwind.css";
import { ref } from "vue";
import GitHub from "./components/GitHub.vue";
import Repos from "./components/Repos.vue";

export default {
    name: "App",
    components: {
        GitHub,
        Repos,
    },
    setup() {
        const username = ref("");
        const github = ref("");
        const gitrepos = ref([]);

        const getGit = () => {
            fetch("https://api.github.com/users/" + username.value)
                .then((res) => res.json())
                .then((data) => (github.value = data))
                .catch((err) => console.log(err.message));
        };
        const getRepo = () => {
            fetch("https://api.github.com/users/" + username.value + "/repos")
                .then((res) => res.json())
                .then((data) => (gitrepos.value = data))
                .catch((err) => console.log(err.message));
            username.value = "";
        };
        return {
            username,
            github,
            gitrepos,
            getGit,
            getRepo,
        };
    },
};
</script>

<style>
body {
    margin: 0;
    box-sizing: border-box;
    font-family: "Montserrat", sans-serif;
    /* background-color: #eeeeee; */
    background-color: #deebdd;
    background-image: linear-gradient(315deg, #deebdd 0%, #bbdbbe 74%);
    align-content: center;
    padding: 3rem 10rem;
}
h1 {
    font-family: "Marck Script", cursive;
    text-align: center;
    font-size: 6rem;
    color: #548ca8;
    padding: 2rem 0 4rem 0;
}
.search-bar {
    background: none;
    border: none;
    outline: none;
    background-color: #f3f3f3;
    box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
    display: block;
    width: 100%;

    padding: 15px;
    border-radius: 8px;
    color: #313131;
    font-size: 20px;
}

button {
    margin: 4rem 25% 4rem 25%;

    width: 40%;
    height: 5rem;
    border: 0;
    text-align: center;
    font-size: 2rem;
    background-color: #19bc9c;
    border-radius: 4rem;
    box-shadow: rgba(0, 0, 0, 0.07) 0px 1px 1px, rgba(0, 0, 0, 0.07) 0px 2px 2px,
        rgba(0, 0, 0, 0.07) 0px 4px 4px, rgba(0, 0, 0, 0.07) 0px 8px 8px,
        rgba(0, 0, 0, 0.07) 0px 16px 16px;
    color: #fff;
}
button:hover {
    background-color: #313131;
}
@media screen and (max-width: 680px) {
    .body {
        padding: 1rem;
    }
}
@media screen and (max-width: 1040px) {
    body {
        padding: 1rem;
    }
}
@media screen and (max-width: 486px) {
    body {
        padding: 0.5rem;
    }
}
</style>
