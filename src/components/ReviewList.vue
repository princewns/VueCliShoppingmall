<template>
    <div class="review-container">
        <h3>Reviews : </h3>
        <ul>
            <li v-for="(review, i) in reviews" v-bind:key="i">
                {{review.name}} 님이 {{review.rating}} 점을 주었습니다.<br>
                "{{review.review}}"<br>
                추천 : {{review.recommend}}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name : 'ReviewList',
    props : ['reviews'],
}
</script>