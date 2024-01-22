<template>
    <div class="col-2 card  overflow-hidden mx-1 rounded-1">
        <div class="img-wrapper">
            <img :src="source"
                :alt="title" />
        </div>
        <div class="card-body ">
            <div>
                <h4 class="text-my-red">
                    {{ title }}
                </h4>
                <h5 class="fw-light">
                    {{ subtitle }}
                </h5>
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

.img-wrapper {
    width: 250px;
}

div>img {
    width: 100%;
}
</style>