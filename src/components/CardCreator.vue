<template>
    <div>
        <div class="card">
            <img :src="info.poster" :alt="info.title">
            <div class="card-body">
                <div class="card-title">
                    <h4>{{ info.title }}</h4>
                </div>
                <span>{{ info.author }}</span>
                <span>{{ info.year }}</span>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    props: {
        info: Object,
    }
}
</script>