<template>
    <div class="container">
        <div class="row row-cols-5">
            <div class="col" v-for="disc in filteredAlbums" :key="disc.title">
                <CardCreator :info="disc"></CardCreator>
                
            </div>
        </div>
    </div>
</template>

<script>
import CardCreator from "./CardCreator.vue";
import axios from "axios";

export default {
    props: {
        changeGenre: String,
    },
    components: {
        CardCreator,
    },

    data() {
        return{
            apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
            discList: [],
        }
    },

    computed: {
        filteredAlbums() {
            if (!this.changeGenre || this.changeGenre === "Filtra per genere") {
                return this.discList
            }

            return this.discList.filter((disc) => {
                return disc.genre === this.changeGenre
            })
        }
    },

    methods: {
        fetchDiscList() {
            axios.get(this.apiUrl)
                 .then((resp) => {
                this.discList = resp.data.response;
                this.$emit("genresList", this.genreList())
            })
        },

        genreList() {
            const list = [];

            this.discList.forEach((disc) => {
                if (!list.includes(disc.genre)) {
                    list.push(disc.genre);
                }
            });

            return list
        }
    },

    mounted() {
        this.fetchDiscList()
    }
}
</script>