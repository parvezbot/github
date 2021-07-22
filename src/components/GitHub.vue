<template>
    <div v-if="github" class="grid md:grid-col-6 user-grid shadow-2xl ">
        <div class="md:col-start-1 md:col-span-1">
            <img class="user-img" :src="github.avatar_url" />
        </div>
        <div class="md:col-start-2 md:col-end-7">
            <h3 class="user">Username: {{ github.login }}</h3>
            <div class="grid grid-col-2">
                <div class="md:col-span-1">
                    <h3>Id: {{ github.id }}</h3>

                    <a :href="github.html_url" target="_"
                        ><h3>github url</h3></a
                    >
                    <h3>Followers: {{ github.followers }}</h3>
                    <h3>Following: {{ github.following }}</h3>
                </div>
                <div class="md:col-end-3">
                    <h3>Public Repos: {{ github.public_repos }}</h3>
                    <h3>Public Gists: {{ github.public_gists }}</h3>
                    <h3>Email: {{ github.email }}</h3>
                    <h3>Twitter: @{{ github.twitter_username }}</h3>
                </div>
                <div class="md:col-span-2">
                    <h3>
                        Blog/Portfolio:
                        <a class="blog" :href="github.blog">{{
                            github.blog
                        }}</a>
                    </h3>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["github"],
};
</script>

<style>
.user-img {
    width: 15rem;
    border-radius: 50%;
    transform: translateY(2.4rem);
}
h3 {
    font-size: 1.5rem;
    padding: 0.5rem;
}
a {
    color: #a03c78;
}
.user-grid {
    border-radius: 3rem;
    padding: 2rem;
    text-align: center;
    background-color: #fff;
    font-family: "Roboto", sans-serif;
    color: #54436b;
}
.user-grid:hover {
    transform: scale(1.04);
}
@media screen and (max-width: 768px) {
    .user-img {
        width: 10rem;
        padding: 0;
        transform: translateY(0rem);
    }
    .user-grid {
        text-align: left;
        margin: 1rem;
    }
}
</style>
