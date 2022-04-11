<template>
    <div class="product-display">
        <div class="product-container">
            <!--이미지 추가-->
            <div class="product-image">
                <img v-bind:src="image">
            </div>
            <!--상품 설명-->
            <div class="product-info">
                <h1>{{title}}</h1>
                <p v-if="variants[this.selection].color == 'white'">색상 : {{variants[this.selection].color}}</p>
                <p v-else>색상 : {{variants[this.selection].color}}</p>
                <p v-if="isStock">수량 : {{isStock}}</p>
                <p v-else style="color : red">품절</p>

                <p>금액 : {{pay}}</p>

                <!--상품 세부설명-->
                <ul>
                    <!--배열로 들고와서 한번에 출력-->
                    <li v-for="(detail, i) in details" v-bind:key="i"> {{detail}} </li>
                </ul>

                <!--색상 바꾸기-->
                <!--값을 두개 들고오면 뒤에 오는 값은 배열의 인덱스값-->

                <div class="color-circle" 
                v-for="(variant, index) in variants" v-bind:key="index"
                v-bind:style="{ backgroundColor:variant.color }"
                v-on:mouseover="updateVariant(index)"></div>

                <!--버튼-->
                <button class="button"
                 v-bind:class="{disabledButton : !isStock}">
                 <span v-if="isStock" v-on:click="cartSelect++">장바구니에 추가</span>
                 <span v-else>품절입니다</span>
                 </button>
            </div>
            <button class="cart" v-on:click="cartSelect++">장바구니({{cartSelect}})</button>

        </div>
    </div>
</template>

<script>
export default {
    name : 'ProductDisplay',
    data : function(){
        return {
            brand : 'Green',
            product : '마스크',
            pay : 15000,
            details : ['폴리프로필렌 부직포',
                       '플라스틱 (코편)',
                       '나일론 끈'],
            variants : [
                {color : 'white', image: require('@/assets/mask_white.jpg'), stock : 10},
                {color : 'black', image: require('@/assets/mask_black.jpg'), stock : 0}
            ],
            //선택한 상품
            selection : 0,
            cartSelect : 0,
        };
    },
    methods : {
        updateVariant : function(index){
            this.selection = index;
        }
    },
    computed : {
        title : function(){
            return this.brand+" "+this.product;
        },
        image : function(){
            //배열의 이미지값을 들고오기 위함
            //selection을 이용하여 선택한 상품의 인덱스를 받아옴
            return this.variants[this.selection].image;
        },
        isStock : function(){
            //배열의 재고의 값을 들고오기 위함
            return this.variants[this.selection].stock;
        }
    },

}
</script>