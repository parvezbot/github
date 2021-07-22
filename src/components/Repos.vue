<template>
    <!-- <div v-if="gitrepos.length"> -->
    <!-- <div v-for="repo in gitrepos" :key="repo.id"> -->
    <div class="grid md:grid-cols-2 repo-grid ">
        <div class="md:col-span-2">
            <h2 class="repo-h">
                <img class="repo" src="../assets/github.png" alt="" />
                Repo Name:
                {{ repo.name }}
            </h2>
        </div>
        <div>
            <h2>Id: {{ repo.id }}</h2>
        </div>
        <div>
            <h2><a :href="repo.html_url" target="_blank">Repo Url</a></h2>
        </div>
        <div>
            <h2>Description: {{ repo.description }}</h2>
        </div>
        <div>
            <h2>Language: {{ repo.language }}</h2>
        </div>
        <div>
            <h2>Created At: {{ repo.created_at }}</h2>
        </div>
        <div>
            <h2>Updated At: {{ repo.updated_at }}</h2>
        </div>
    </div>

    <!-- </div> -->
    <!-- </div> -->
</template>

<script>
export default {
    name: "Repos",
    props: ["repo"],
};
</script>

<style>
h2 {
    font-size: 1.5rem;
    padding: 0.2rem;
    font-family: "Ubuntu Bold", sans-serif;
}
.repo-h {
    transform: translateX(-2rem);
}
.repo {
    width: 4rem;
    display: inline-block;
    /* transform: translateX(-6rem); */
}
a {
    color: #a03c78;
}
.repo-grid {
    border-radius: 3rem;
    padding: 2rem;
    text-align: center;
    background-color: #fff;
    font-family: "Roboto", sans-serif;
    color: #54436b;
    box-shadow: 0 3px 8px rgb(0 0 0 / 24%);

    margin: 2rem;
}
.repo-grid:hover {
    transform: scale(1.04);
}
@media screen and (max-width: 768px) {
    .repo-h {
        transform: translateX(0);
    }
    .repo {
        transform: translateX(0);
    }
    .repo-grid {
        margin: 1rem;
    }
}
@media screen and (max-width: 486px) {
    .repo-grid {
    }
}
</style>
