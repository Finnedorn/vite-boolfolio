<template>
    <div class="col-lg-2 col-md-1 card mx-1 rounded-1 p-2">
        <div class="overflow-hidden rounded-2 ">
            <img :src="source"
                :alt="title" />
        </div>
        <div class="card-body ">
            <div>
                <h4 class="text-my-red">
                    {{ title }}
                </h4>
                <h6 class="fw-light">
                    {{ subtitle }}
                </h6>
            </div>
            <div class="pt-2">
                <small v-for="badge in badges" class="badge text-bg-primary mx-1">
                    {{ badge.name }}
                </small>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    name: "CardComponent",
    props: {
        source: String,
        title: String,
        subtitle: String,
        badges: Array
    },
    data() {
        return {
        };
    },
    methods: {
    },
    mounted() {
    }
};
</script>
  
<style lang="scss" scoped>

img {
    width: 100%;
}
</style>