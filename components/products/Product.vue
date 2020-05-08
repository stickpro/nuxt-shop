<template>
    <div class="card">
        <div class="card-image">
            <figure class="image is-4by3">    
                <img src="https://bulma.io/images/placeholders/1280x960.png" alt="">
            </figure>
        </div>
        <div class="card-content">
            <div class="media">
                <div class="media-content">
                    <a :href="product.slug" class="title is-5">{{ product.name }}</a>
                </div>
            </div>
            <div class="content" v-if="product.description">
                <p>{{ product.description }}</p>
                <span class="tag is-rounded is-medium">Product price</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        product: {
            requred: true,
            type: Object,
        },
    }
}
</script>